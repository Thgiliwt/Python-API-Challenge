# Python-API-Challenge
This is my 6th homework from the coding bootcamp course.
In this homework I need to try multipul API calls with OpenWeather and Gmaps. Then use the obtained data to plot or generate figures to show statistical analysis and findings. It is the coding interface to exchange data to real-world applications which is chanllenging and could be very useful to workplace tasks.

## Key Reflects

### New Findings
A new external library is introduced called 'citipy', there is an useful link about it at 'https://github.com/wingchen/citipy'. So the basic idea of introducing it is because we are generating random cities for analysis. We will use the geographic coordinates to locate the nearest city to it, i.e. a pair of Latitude and Longitude. There are other features about this library but it is relevant to this task.
The built-in lib of 'random' is used to generate 1500 pair of coordinates, very handy to use for statistical studies and also maybe good for estimation or checking findings afterwards.
The first API call for part 1 is with 'OpenWeather'. We focus on the current weather data as we would like to use the weather information of different cities for further anaylsis and it does not require any particular date of weather. It provides very detailed information about the weather for a typical city. We could use the data obtained to generate new dataframe for later use. Within the weather API call, we need to indicate the base url, API keys and what exactly we require as the query. We will use .requests and display it in json() format.
As the date format is unix UTC so we use pd.to_datetime() to convert it to local time. See 'Uncertainties' for further notes.
First time using def functions within python. It is very convenient and saves much time when repeating similar coding for plots. Should try more in the future.
The second API is with 'Gmaps'. We obtain a slice of google map showing within the notebook, where it is not just a screenshot but a semi-interface window where you could adjust the size, type of map and etc. The heatmap to my understanding is that, the Gmaps provides us with the map, and you could use your local data to add widgets to it, more like a sandbox. The marker one, however is for you to gather information from the server and then use the data obtained to generate little features, such as marker, on top of the sandbox, whereas it could be different layers to the blank map.

### New Tricks
When generating the new dataframe from part 1, I used a for loop. This really gave me a headache for the first few attempts. There are different ways to iterate through a list, such as range() method where x is the index number, the for loop where x could be the actual variables, same idea for the list comprehension, the while loop where x is the index number, the enumerate(iterable, start_index). I used the for loop just to show a clearer understanding and coding steps.
Def a function, where as mentioned above, very easy and efficient. I found that I could even set up a string as the variable within a function.
The 'requests.get(baseurl,params) way of exchanging data are also outstanding to use.
The 'for index, row in XXX.iterrows():' way of iterating a list is also good when adding items into a series or a dataframe.
The codes for implenmenting the marker and layouts as below:
    "# Using the template add the hotel marks to the heatmap
    info_box_template = """
    <dl>
    <dt>Name</dt><dd>{Hotel Name}</dd>
    <dt>City</dt><dd>{City}</dd>
    <dt>Country</dt><dd>{Country}</dd>
    </dl>
    """
    # Store the DataFrame Row
    # NOTE: be sure to update with your DataFrame name
    hotel_info = [info_box_template.format(**row) for index, row in hotel_df.iterrows()]
    locations = hotel_df[["Lat", "Lng"]]"


### Uncertainties
1. I have imported 'datetime' to convert the units of unix UTC date and time but could not workout the correct way of using it. It says that could not convert the int value. I may try to convert it within the API call steps.
2. I have not applied time.sleep() but should have done it.
3. There is no any dataset that has more than 100% of humidity from my data, however it there is I could use the drop or remove method from last homework to get a clearer data.
4. In the part 2 of getting the marker image, as there are multipul hotels within the given 5km radius, I could have different hotel name shows each time I made an API call. I have searched the coordinates on google map for each city to check for this. Maybe narrow down the search by specifiying in 'keywords' category.

### Screenshots for Part II

Heatmap of humidity for all cities:
![Heatmap](https://github.com/Thgiliwt/Python-API-Challenge/blob/72e28f8b1e1f8d7b41e124ca7495dbfac70a6c9d/output_data/Heatmap.png)


Marker of hotels within 5km radius of the city geo coordinates:
![Marker](https://github.com/Thgiliwt/Python-API-Challenge/blob/72e28f8b1e1f8d7b41e124ca7495dbfac70a6c9d/output_data/Marker.PNG)

