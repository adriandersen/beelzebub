# Beelzebub ![CI](https://github.com/mariocandela/beelzebub/actions/workflows/ci.yml/badge.svg)

A secure multi protocol low interaction honeypot, extremely easy to configure by yaml 🚀

## Quick Start

Using [`docker-compose`](https://docs.docker.com/compose/)

```bash
$ docker-compose build
$ docker-compose up -d
 ```

Using [`go compiler`](https://go.dev/doc/install)

```bash
$ go mod download
$ go build 
$ ./beelzebub
 ```

## Example configuration service 

The configurations are inside the /configurations/services directory, just add a new file for each service/port.

### Example HTTP Honeypot on 80 port

###### http-80.yaml

```yaml
apiVersion: "v1"
protocol: "http"
address: ":80"
commands:
  - regex: "microtick"
    handler: "<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Transitional//EN\" \"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd\">\r\n<html xmlns=\"http://www.w3.org/1999/xhtml\">\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\" />\r\n<link rel=\"icon\" href=\"/favicon.png\"/>\r\n<title>RouterOS router configuration page</title>\r\n<style type=\"text/css\">\r\nbody {\r\nfont-family: Verdana, Geneva, sans-serif;\r\nfont-size: 11px;\r\n}\r\nimg {border: none}\r\nimg:hover {opacity: 0.8;}\r\nh1 {\r\nfont-size: 1.7em;\r\ndisplay: inline;\r\nmargin-bottom: 10px;\r\n}\r\nfieldset {\r\nmargin-top: 20px;\r\nbackground: #fff;\r\npadding: 20px;\r\nborder: 1px solid #c1c1c1; \r\n}\r\n#container {\r\nwidth: 70%;\r\nmargin: 10% auto;\r\n}\r\n#box {\r\nbackground-color: #fff; \r\n-moz-border-radius: 7px; \r\n-webkit-border-radius: 7px; \r\nborder: 1px solid #c1c1c1; \r\npadding: 30px;\r\nfilter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#ffffff', endColorstr='#f3f3f3'); /* for IE */\r\nbackground: -webkit-gradient(linear, left top, left bottom, from(#fff), to(#f3f3f3)); /* for webkit browsers */\r\nbackground: -moz-linear-gradient(top,  #fff,  #f3f3f3); /* for firefox 3.6+ */\r\n}\r\n.floater {float: left; margin-right: 10px;}\r\n.floater label {display: block; text-align: center;}\r\n\r\n#login {\r\n    margin: 2em 0 4em 0;\r\n}\r\n#login h2 {\r\n    font-weight: normal;\r\n    font-size: 14px;\r\n    margin: 0 0 0.5em 1em;\r\n}\r\n#login td {\r\n    padding: 0 4px 0 0;\r\n}\r\n#login td.label {\r\n    text-align: right;\r\n}\r\n#login td.toolbar {\r\n    padding: 0 0 0 1em;\r\n    vertical-align: top;\r\n}\r\n#login ul.toolbar {\r\n    margin: 0;\r\n}\r\n#login input {\r\n    margin: 2px;\r\n    padding: 2px;\r\n    border: 1px solid #888;\r\n    box-shadow: 1px 1px 3px rgba(0,0,0,0.3);\r\n    -webkit-box-shadow: 1px 1px 3px rgba(0,0,0,0.3);\r\n    -moz-box-shadow: 1px 1px 3px rgba(0,0,0,0.3);\r\n}\r\n#error {\r\n    display:none;\r\n    color:red;\r\n    padding: 1em 0 0 0;\r\n}\r\nul.toolbar {\r\n    font-size: 11px;\r\n    text-align: left;\r\n    list-style-type: none;\r\n    padding: 0;\r\n    margin: 2px 0 4px 2px;\r\n}\r\nul.toolbar li {\r\n    float: left;\r\n    vertical-align: middle;\r\n}\r\nul.toolbar a {\r\n    float: none;\r\n    display: block;\r\n    margin: 2px 4px 2px 0;\r\n    padding: 5px;\r\n\r\n    background: #ddd;\r\n    border: 1px solid #888;\r\n    border-radius: 3px;\r\n    -moz-border-radius: 3px;\r\n    box-shadow:\r\n        1px 1px 2px rgba(255,255,255,0.8) inset,\r\n\t0 10px 10px -5px rgba(255,255,255,0.5) inset, /* top gradient */\r\n\t1px 1px 2px rgba(0,0,0,0.2); /* shadow */\r\n    -webkit-box-shadow:\r\n        1px 1px 2px rgba(255,255,255,0.8) inset,\r\n\t0 10px 10px -5px rgba(255,255,255,0.5) inset,\r\n\t1px 1px 2px rgba(0,0,0,0.2);\r\n    -moz-box-shadow:\r\n        1px 1px 2px rgba(255,255,255,0.8) inset,\r\n\t0 10px 10px -5px rgba(255,255,255,0.5) inset,\r\n\t1px 1px 2px rgba(0,0,0,0.2);\r\n    color: #000;\r\n\r\n    text-decoration: none;\r\n    text-align: center;\r\n    white-space: nowrap;\r\n    cursor: inherit;\r\n    min-width: 4em;\r\n\r\n    -webkit-transition: background 0.2s linear, box-shadow 0.2s ease-out;\r\n    -moz-transition: background 0.2s linear, box-shadow 0.2s ease-out;\r\n}\r\nul.toolbar a:hover {\r\n    background: #eee;\r\n}\r\nul.toolbar a:active {\r\n    background: #aaa;\r\n    box-shadow: 1px 1px 2px #999 inset;\r\n    -webkit-box-shadow: 1px 1px 2px #999 inset;\r\n    -moz-box-shadow: 1px 1px 2px #999 inset;\r\n}\r\n</style>\r\n<script>\r\nfunction get(id) {\r\n    return document.getElementById(id);\r\n}\r\nfunction trim(str) {\r\n    return str.replace(/^\\s+|\\s+$/g, '');\r\n}\r\nfunction login(user, pwd, autologin) {\r\n    var expires = new Date();\r\n    expires.setTime(expires.getTime() + (30 * 24 * 60 * 60 * 1000));\r\n    document.cookie = 'username=' + user +\r\n        '; expires=' + expires.toGMTString() + '; path=/';\r\n\r\n    window.name = (autologin ? 'autologin=' : 'login=') + user + '|' + pwd;\r\n    window.location.replace('/webfig/' + window.location.hash);\r\n}\r\nfunction dologin() {\r\n    login(get('name').value, get('password').value);\r\n}\r\nfunction loaded() {\r\n    var p = window.name.split('=');\r\n    if (p[0] == 'error' && p[1]) {\r\n        var err = get('error');\r\n        err.appendChild(document.createTextNode(p[1]));\r\n        err.style.display = 'block';\r\n    } else if (p[0] != 'noautologin' || p[1] != 1) {\r\n        var user = '';\r\n        if (user) {\r\n            login(user, '', true);\r\n            return;\r\n        }\r\n    }\r\n    window.name = '';\r\n\r\n    document.onkeydown = function(e) {\r\n        e = e || event;\r\n        if (e.keyCode == 13) {\r\n            dologin();\r\n            return false;\r\n        }\r\n        return true;\r\n    };\r\n\r\n    var username = null;\r\n    var cookies = document.cookie.split(';');\r\n    for (var i in cookies) {\r\n\tvar c = trim(cookies[i]).split('=');\r\n\tif (c[0] == 'username') {\r\n\t    username = c[1];\r\n\t    break;\r\n\t}\r\n    }\r\n    \r\n    if (username != null) {\r\n\tget('name').value = username;\r\n\tget('password').focus();\r\n    } else {\r\n        get('name').value = 'admin';\r\n\tget('name').focus();\r\n    }\r\n}\r\n</script>\r\n</head>\r\n\r\n<body onload=\"loaded()\">\r\n\r\n<div id=\"container\">\r\n\r\n    <div id=\"box\">\r\n    <a href=\"http://mikrotik.com\"><img src=\"mikrotik_logo.png\" style=\"float: right;\" /></a>\r\n\r\n    <br style=\"clear: both;\"/>\r\n    \r\n\t\t<h1>RouterOS v6.42.12</h1>\r\n        \r\n        <p>You have connected to a router. Administrative access only. If this device is not in your possession, please contact your local network administrator. </p>\r\n        \r\n      <table id=\"login\">\r\n\t<tr><td colspan=\"3\"><h2>WebFig Login:</h2>\r\n        <tr><td class=\"label\">Login: <td><input id=\"name\" type=\"text\" tabindex=\"1\">\r\n\t <td class=\"toolbar\" rowspan=\"2\">\r\n         <ul class=\"toolbar\">\r\n\t   <li><a onclick=\"dologin()\" ondragstart=\"return false;\"><span>Login</span></a></li>\r\n         </ul>\r\n         <tr><td class=\"label\">Password: <td><input id=\"password\" type=\"password\" tabindex=\"2\">\r\n\t<tr><td colspan=\"3\">\r\n\t    <div id=\"error\"></div>\r\n      </table>\r\n            \r\n            <fieldset>\r\n            <div class=\"floater\"> \r\n            \t<a href=\"http://www.mikrotik.com/download/winbox.exe\"><img src=\"winbox.png\"/></a><br/>\r\n                <label>Winbox</label>\r\n            </div>\r\n            \r\n            <div class=\"floater\"> \r\n            \t<a href=\"telnet://10.140.16.24\"><img src=\"console.png\"/></a><br/>\r\n                <label>Telnet</label>\r\n            </div>\r\n\r\n            \r\n            \r\n            <div class=\"floater\"> \r\n            \t<a href=\"/graphs\"><img src=\"green.png\"/></a><br/>\r\n                <label>Graphs</label>\r\n            </div>\r\n           \r\n            \r\n            <div class=\"floater\"> \r\n            \t<a href=\"/help/license.html\"><img src=\"license.png\"/></a><br/>\r\n                <label>License</label>\r\n            </div>\r\n            \r\n\t\t\t<div class=\"floater\"> \r\n            \t<a href=\"http://wiki.mikrotik.com\"><img src=\"help.png\"/></a><br/>\r\n                <label>Help</label>\r\n            </div>\r\n\r\n</fieldset>\r\n           \r\n            <br style=\"clear: both\"/> \r\n                            <div style=\"float: right\">&copy; mikrotik</div>\r\n\r\n    </div>\r\n</div>\r\n\r\n</div>\r\n\r\n</body>\r\n</html>\r\n"
    headers:
      - "Content-Type: text/html"
      - "Expires: 0"
      - "Version: 6.42.12"
    statusCode: 200
  - regex: "hello"
    handler: "world!"
    headers:
      - "Content-Type: text/html"
    statusCode: 500
 ```

### Example HTTP Honeypot on 8080 port

###### http-8080.yaml

```yaml
apiVersion: "v1"
protocol: "http"
address: ":8080"
commands:
  - regex: "wp-admin"
    handler: "Unauthorized"
    headers:
      - "Content-Type: text/html"
    statusCode: 401
 ```

### Example SSH Honeypot

###### ssh-22.yaml

```yaml
apiVersion: "v1"
protocol: "ssh"
address: ":22"
commands:
  - regex: "^ls$"
    handler: "Documents Images  Desktop Downloads .m2 .kube .ssh  .docker"
  - regex: "^pwd$"
    handler: "/home/"
  - regex: "^uname -m$"
    handler: "x86_64"
  - regex: "^docker ps$"
    handler: "CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES"
  - regex: "^docker .*$"
    handler: "Error response from daemon: dial unix docker.raw.sock: connect: connection refused"
  - regex: "^uname$"
    handler: "Linux"
  - regex: "^ps$"
    handler: "  PID TTY           TIME CMD\n21642 ttys000    0:00.07 /bin/dockerd"
  - regex: "^(.+)$"
    handler: "command not found"
serverVersion: "OpenSSH"
serverName: "ubuntu"
passwordRegex: "^(root|qwerty)$"
deadlineTimeoutSeconds: 60
 ```

## Features

- SSH Honeypot
- HTTP Honeypot
- Easy to create a new strategy
- Easy to extend event tracking logic
- Strong code quality
- Docker

## TODO

- telnet
- tcp

## Documentation

- [API Docs](https://) #TODO

## Contributing

The beelzebub team enthusiastically welcomes contributions and project participation! There's a bunch of things you can do if you want to contribute! The [Contributor Guide](CONTRIBUTING.md) has all the information you need for everything from reporting bugs to contributing entire new features. Please don't hesitate to jump in if you'd like to, or even ask us questions if something isn't clear.

All participants and maintainers in this project are expected to follow [Code of Conduct](CODE_OF_CONDUCT.md), and just generally be excellent to each other.

Happy hacking!

## License

This project is licensed under [GNU GPL 3 License](LICENSE).