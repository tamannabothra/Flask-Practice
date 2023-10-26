# Flask-Practice
# Flask-Practice
# 1
 ```
from flask import Flask
app = Flask(__name__)
@app.route('/')
def hello_world():
    return 'Hello World
if __name__ == '__main__':
    app.run()
```

# 2
 ```
from flask import Flask
app=Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello World!! How are you?'

if __name__=='__main__':
    app.run(debug=True)
 ```

# 3 
 ```
from flask import Flask
app=Flask(__name__)

@app.route('/admin')
def hello_admin():
    return 'Hello Admin!!'

@app.route('/guest/<guest>')
def hello_guest(guest):
    return 'Hello %s you logged in as guest user' % guest

@app.route('/usr/<name>')
def hello_user(name):
    if name=='admin':
        return redirect(url_for('hello_admin'))
    else:
        return redirect(url_for('hello_guest',guest=name))

@app.route('/')
def hello():
    return 'Hello World!'

if __name__=='__main__':
    app.run(debug=True)
 ```


# 4
 ```
from flask import Flask
app = Flask(__name__)
@app.route('/success/<name>')
def success(name):
   return 'welcome %s' % name

@app.route('/login',methods = ['POST', 'GET'])
def login():
   if request.method == 'POST':
      user = request.form['nm']
      return redirect(url_for('success',name = user))
   else:
      user = request.args.get('nm')
      return redirect(url_for('success',name = user))

if __name__ == '__main__':
   app.run(debug = True)
 ```
# index.html


 ```
<!DOCTYPE html>
<html lang="en">
   <body>
      <form action="http://localhost:5000/login" method="post">
         <p>Enter Name:</p>
         <p><input type="text" name="nm" /></p>
         <p><input type="submit" value="submit" /></p>
      </form>
   </body>
</html>
 ```


# 5

demo1.py<br/>
 ```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
   return '<html><body><h1>Hello World</h1></body></html>'

if __name__ == '__main__':
   app.run(debug = True)
 ```
demo2.py
 ```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
   return render_template(‘hello.html’)

if __name__ == '__main__':
   app.run(debug = True)
 ```
# html
 ```
<!doctype html>
<html>
   <body>
   
      <h1>Hello {{ name }}!</h1>
      
   </body>
</html>
```
