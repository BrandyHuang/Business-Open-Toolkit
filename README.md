# Business-Open-Toolkit
#### This is a creative project! It aims to provide some ideas to business men or women who have ideas to operate a business but don't know where to hit the road. It utilizes skills of APIs and python in asscessing data from websties. Here are the steps and details:
* Not matter what you want, tell us your idea firstly :)!
* Get google map API to draw a heatmap of traffic in the city you want to operate business in
* Get Yelp API to analyze top competitors in the city
* Get GoogleAI API to generate strategies for you! 
  
## API connection process
```
import requests

## Set boundary for all SF
types = ["shopping_mall", "tourist_attraction", "transit_station", "restaurant"]
results = []

for place_type in types:
    response = requests.get("https://maps.googleapis.com/maps/api/place/nearbysearch/json", params={
        "location": "37.7529,-122.4474",
        "radius": 1000000,
        "type": place_type,
        "key": "put your key"
    })
    results.extend(response.json().get("results", []))
```
```
API_KEY = "###put your key"
headers = {"Authorization": f"Bearer {API_KEY}"}

# Function to fetch data with pagination
def get_yelp_data(offset):
    response = requests.get(
        "https://api.yelp.com/v3/businesses/search",
        headers=headers,
        params={
            "location": "San Francisco, CA",
            "categories": "icecream",
            "limit": 50,
            "offset": offset,
            "sort_by": "rating"
        }
    )
    return response.json()
```
