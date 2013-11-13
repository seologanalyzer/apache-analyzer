# Apache Analyzer

Log some informations from GoogleBot & BingBot for SeoLogAnalyzer.

## Installation

Edit virtualhost (*/etc/apache2/sites-available/*)

Add after *DocumentRoot* :

    LogFormat "%h:::%>s:::%b:::%D:::\"%{Referer}i\":::\"%{User-agent}i\":::\"%V\"\"%r\"" slacombined
    SetEnvIf User-Agent "Googlebot/2.1" sla
    SetEnvIf User-Agent "bingbot/2.0" sla
    SetEnvIf Referer "google.*q=" sla
    SetEnvIf Referer "bing.*q=" sla
    CustomLog "|/var/www/www.xxx.com/sla/logger" slacombined env=sla

## Directive LogFormat Apache logs

- %h = Ip
- %>s = Server code response
- %b = Size
- %D = Loading time (µs)
- %{Referer}i = Referer
- %{User-agent}i = User agent
- %V%r = Complete uri

## More about apache logs

[Apache logs](http://httpd.apache.org/docs/trunk/en/logs.html)

[Apache modlogconfig](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html)


