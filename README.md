# yPay Plan Task

yPay monitoring page. Monitor the best pages with the best performance!

© Powered by Prk

# Use Tutorial

## 1) Download the latest release package (.zip).
## 2) Upload the release package to the server and unzip.
## 3) Configure server software (e.g: Nginx, Apache).

### Nginx
```
location / {
  try_files $uri $uri/ /index.html;
}
```

### Apache
```
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.html [L]
</IfModule>
```
Instead of `mod_rewrite`, you could also use `[FallbackResource](https://httpd.apache.org/docs/2.2/mod/mod_dir.html#fallbackresource "Open in new window")`.

### Node.js
```
const http = require('http')
const fs = require('fs')
const httpPort = 80

http.createServer((req, res) => {
  fs.readFile('index.html', 'utf-8', (err, content) => {
    if (err) {
      console.log('We cannot open "index.html" file.')
    }

    res.writeHead(200, {
      'Content-Type': 'text/html; charset=utf-8'
    })

    res.end(content)
  })
}).listen(httpPort, () => {
  console.log('Server listening on: http://localhost:%s', httpPort)
})
```
## 4) U R DOWN !!
