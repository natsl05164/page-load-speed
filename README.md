# page-load-speed

Leverage browser caching,
For  Apache .htaccess

<IfModule mod_headers.c>
<FilesMatch "\\.(ico|jpg|jpeg|png|gif|swf)$">
Header set Cache-Control "max-age=2678100, public"
</FilesMatch>
<FilesMatch "\\.(css)$">
Header set Cache-Control "max-age=604200, public"
</FilesMatch>
<FilesMatch "\\.(js)$">
Header set Cache-Control "max-age=604300, private"
</FilesMatch>
<FilesMatch "\\.(x?html?|php)$">
Header set Cache-Control "max-age=60, private, must-revalidate"
</FilesMatch>
Header unset ETag
Header unset Last-Modified
</IfModule>

 
For nginx Server

location ~* \.(jpg|jpeg|png|gif|ico|css|js|pdf)$ {
expires 7d;
}
 
Enable gzip compression
 
On Nginx Server

gzip on;
gzip_proxied any;
gzip_types text/plain text/xml text/css font/woff2 application/x-javascript application/x-font-woff woff2 application/font-woff2 woff2;
gzip_vary on;
gzip_disable "MSIE [1-6]\.(?!.*SV1)";

 
For .htaccess files In Apache

<IfModule mod_deflate.c>
# Compress HTML, CSS, JavaScript, Text, XML and fonts
AddOutputFilterByType DEFLATE application/javascript
AddOutputFilterByType DEFLATE application/rss+xml
AddOutputFilterByType DEFLATE application/vnd.ms-fontobject
AddOutputFilterByType DEFLATE application/x-font
AddOutputFilterByType DEFLATE application/x-font-opentype
AddOutputFilterByType DEFLATE application/x-font-otf
AddOutputFilterByType DEFLATE application/x-font-truetype
AddOutputFilterByType DEFLATE application/x-font-ttf
AddOutputFilterByType DEFLATE application/x-javascript
AddOutputFilterByType DEFLATE application/xhtml+xml
AddOutputFilterByType DEFLATE application/xml
AddOutputFilterByType DEFLATE font/opentype
AddOutputFilterByType DEFLATE font/otf
AddOutputFilterByType DEFLATE font/ttf
AddOutputFilterByType DEFLATE image/svg+xml
AddOutputFilterByType DEFLATE image/x-icon
AddOutputFilterByType DEFLATE text/css
AddOutputFilterByType DEFLATE text/html
AddOutputFilterByType DEFLATE text/javascript
AddOutputFilterByType DEFLATE text/plain
AddOutputFilterByType DEFLATE text/xml
# Remove browser bugs (only needed for really old browsers)
BrowserMatch ^Mozilla/4 gzip-only-text/html
BrowserMatch ^Mozilla/4\.0[678] no-gzip
BrowserMatch \bMSIE !no-gzip !gzip-only-text/html
Header append Vary User-Agent
</IfModule>

