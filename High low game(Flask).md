from flask import Flask

app = Flask(__name__)

@app.route('/')
def first_page():
    return '<h1 style="text-align:center">Guess a number from 1 to 10</h1>'

@app.route('/<int:n>')
def check(n):
    if (n>5):
        return '<h1> Too high . Try less </h1>'

    elif(n<5):
        return '<h1> Too low . Try more </h1>'
    elif(n==5):
        return '<h1> Wohooo . You found me.</h1>'


if __name__=="__main__":
   app.run(debug=True)
