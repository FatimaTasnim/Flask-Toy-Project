# Flask
**__ name __** : Special variable of python. Just the name of module.
__ name __ = __ main__ for the following code
```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"
```

## Routes
routes are what we type into our browser to go to different pages.

## Run The Application (command prompt )
- At first need to set environment variable
 ```
 set FLASK_APP=flaskblog.py
 ```
 - to run the application
 ```
 flask run
 ```
 - to stop the application ctrl+c

In this way the application need to run again and again if any change happens. And to avoid this need to run in DEBUG mood. for this need to set a different environment variable
 ```
 set FLASK_DEBUG=1
 ```
Another way to run application directly with python and get rid of those environment variable.

add the following code end of the main file

```
if __name__ == '__main__':
    app.run(debug=True)
```
and in command line just run the main file as trivial python file.
```
python flaskblog.py
```
## Adding extra pages
in the main.py(flaskblog.py) page add extra route
```
@app.route("/about")
```

## Adding multiline html(naive approach)
```Python
def home():
    return '''
    <!doctype html>
    <html>
        <head> <title> Home </title> </head>
        <body> Hey! </body>
    </html>
    '''
```

## Adding multiline html(Smart approach)
1. make a templates folder.
2. create html pages.
3. in main.py import render_templates
4. render the page like the following code
```python
def home():
    return render_template('home.html')
```

## Passing Data
- pass the data variable with render
```python
def home():
    return render_template('home.html', posts = posts)
```
- access the data like following
```python
 {% for post in posts%}
        <h1>Hey {{ post.author }}!</h1>
 {% endfor %}
```

## Template Inheritance
To ignore changing each and every pages for a specific part should use a layout file so if any change needed only changing the layout page will do.

1. make a new page layout.html
2. and the common code lines to the page
3. add block where changes required for different pages 
```html 
<body>
    {% block content %}{% endblock %}
</body>
```
4. Change the previous files like the following one
```html
{% extends "layout.html" %}
{% block content %}
    <h1>Hey!</h1>
{% endblock content%}
```
5. can also add bootstrap in layout page.

## Adding CSS
- CSS files need to be kept in a static folder named "static"
- add new css file to that folder.
- to add this css file to layout need to use a flask function - url_for. This function will found the exact location of the routes so no need to worry about it in background. 
- import the url_for function in main.py(flaskblog.py) file.
- 
### Learning Buffer
- Route Decorator
- 