---
title: "Development of SkyPeeker"
date: 2023-05-08T18:05:14+05:30
draft: false
---
## What is SkyPeeker?
So me and my friend [Warlord64](https://github.com/Warlord64) were getting bored so we decided to make a weather app because it would be something that we could show to normal people(by normal people i mean people who are not developers).

[SkyPeeker](https://github.com/suryapsp/sky-peeker) is a weather app that uses [openweathermap API](https://openweathermap.org/api) and [Flask](https://flask.palletsprojects.com/en/2.3.x/) in the backend and plain HTML CSS and JS in the frontend. Check out the [Demo](http://skypeeker.pythonanywhere.com/).
(**The Demo Website might not work after some time because pythonanywhere require you to manually restart the instance after every 3 months.**)

The front-end was made by my good friend Warlord64 make sure to check him out and the backend was written by me. We both faced a lot of issues during the development because of our massive skill issue.

## Code
Ok so i am not gonna explain what the front-end code is doing but i am gonna focus more on the backend code because i have written that and i know what everything does.

### Setting up the environment
first of all we are gonna create an environment before starting the coding part.

``` bash
mkdir sky-peeker
cd sky-peeker
python3 -m venv venv
./venv/bin/activate
pip install flask
touch app.py
```
### Get your API Key
go to [openweathermap](https://openweathermap.org/api) and get your own api key.

```bash
echo "<your-api-key>" > api_key
```
### The main code
first import all the main packages that we will require in the development.

```python
from flask import Flask,render_template,request,abort
import json
import urllib.request
```

function to convert kelvin to degree celcius
```python
app = Flask(__name__)
def tocelcius(temperature_in_kelvin):
    return str(round(temperature_in_kelvin - 273.15, 3))
```

The main weather function
```python
@app.route('/',methods=['POST', 'GET'])
def weather():
    #api key
    api_key = open('api_key', 'r').read()

    #city
    if request.method == 'POST':
        city = request.form['city']
    else:
        city = 'kanpur'

    #getting json data from the api
    url = urllib.request.urlopen('http://api.openweathermap.org/data/2.5/weather?q=' + city + '&appid=' + api_key).read()

    # converting json data to dictionary
    data = json.loads(url)
    weather_info = {
        "temp": str(data['main']['temp']) + 'k',

        "temp_cel": tocelcius(data['main']['temp']) + 'C',

        "pressure": str(data['main']['pressure']),

        "humidity": str(data['main']['humidity']),

        "cityname":str(city),

        "country_code": str(data['sys']['country']),

        "coordinate": str(data['coord']['lon']) + ' ' + str(data['coord']['lat']),
    }
    return render_template('index.html',weather_info=weather_info)
```

### What to do next
now create the templates and static folder
```bash
mkdir templates
mkdir static
```
templates is the folder where all your index.html and other main files go and in static all your images, css amd javascript files go

## Resources i used 
- [Flask Doccumentation](https://flask.palletsprojects.com/en/2.2.x/)
- [StackOverflow](https://stackoverflow.com/)

