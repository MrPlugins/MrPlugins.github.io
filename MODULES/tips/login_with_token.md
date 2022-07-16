It's possible to login into back-end and front-end via uniqid of existing user witohu a login with user and password:\
just reach <code>//YOUR_INCIPIT_INSTALLATION/admin/login?uniqid=THE_UNIQID_OF_USER</code>\
<br/>
this feature is very useful to autolog the administrator through a link sent by email
<br/>
<br/>
You can apen other querystring to the uri and apply other logics for example:\
<code>//YOUR_INCIPIT_INSTALLATION/admin/login?uniqid=THE_UNIQID_OF_THE_USER&url_redirect=products</code>\
this will autolog the user into back-end and redirect to `products` module