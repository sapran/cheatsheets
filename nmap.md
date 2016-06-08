## Quick discovery scan

~~~
sudo nmap -n -P0 -p80 -iL hosts.lst --script \
http-apache-server-status,\
http-auth-finder,\
http-backup-finder,\
http-comments-displayer,\
http-default-accounts,\
http-devframework,\
http-enum,\
http-headers,\
http-mobileversion-checker,\
http-php-version,\
http-robots.txt,\
http-svn-info,\
http-useragent-tester,\
http-vhosts,\
http-webdav-scan,\
http-xssed\
 -oA nmap_tcp_80_with_scripts
~~~

## Quick validation/exploitation scan

~~~
sudo nmap -n -P0 -p80 -iL hosts.lst --script \
http-csrf,\
http-dombased-xss,\
http-fileupload-exploiter,\
http-shellshock,\
http-stored-xss,\
http-vuln-cve2006-3392,\
http-vuln-cve2009-3960,\
http-vuln-cve2012-1823,\
http-vuln-cve2013-0156,\
http-vuln-cve2013-6786,\
http-vuln-cve2013-7091,\
http-vuln-cve2014-3704,\
http-vuln-cve2014-8877\
 -oA nmap_tcp_80_with_scripts
~~~

## Full crazy scan with huge overheads

~~~
sudo nmap -n -P0 -p80,443 -iL hosts.lst --script \
http-enum,\
http-vhosts,\
http-server-header,\
http-title,\
http-methods,\
http-method-tamper,\
http-put,\
http-headers,\
http-robots.txt,\
http-errors,\
http-auth-finder,\
http-backup-finder,\
http-comments-displayer,\
http-cors,\
http-cross-domain-policy,\
http-devframework,\
http-dombased-xss,\
http-exif-spider,\
http-git,\
http-svn-info,\
http-webdav-scan,\
http-shellshock,\
http-slowloris-check,\
http-csrf,\
http-sql-injection,\
http-rfi-spider,\
http-phpself-xss,\
http-stored-xss,\
http-unsafe-output-escaping,\
http-open-proxy,\
http-open-redirect,\
http-passwd,\
http-php-version,\
http-useragent-tester,\
http-userdir-enum,\
http-xssed,\
http-vuln-*\
 -oA nmap_tcp_80,443_with_scripts
~~~
