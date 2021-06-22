import requests

from datetime import datetime

api_key = 'fd03b9ee5e2f8dd2a70701f8763a1083'
location = input("Enter the city name: ")

complete_api_link = "https://api.openweathermap.org/data/2.5/weather?q="+location+"&appid="+api_key
api_link = requests.get(complete_api_link)
api_data = api_link.json()


temp_city = ((api_data['main']['temp'])- 273.15)
weather_desc = api_data['weather'][0]['description']
hmdt = api_data['main']['humidity']
wind_spd = api_data['wind']['speed']
date_time = datetime.now().strftime("%d %b %y | %I %M %S %p")

print("___________________________________________________________________")
print("Weather Stats for - {}  ||  {}".format(location.upper(),date_time))
print("___________________________________________________________________")

print("Current temperature is: {:.2f} deg C".format(temp_city))
print("Current weather desc  :",weather_desc)
print("Current Humidity      :",hmdt,'%')
print("Current wind speed    :",wind_spd,'kmph')
