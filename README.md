World Weather Analysis
Overview:
In this analysis, we will apply visualizations, analysis and statistical skills and API data retrieval. Gathering data from an API is much more practical and efficient than to retrieve from a website like web scraping, especially when MBs or GBs of data are involved. Web APIs allows the client to request data from the website or database server within the confines of the website's rules. Data can be retrieved from an API in popular formats such as JSON(JavaScript Object Notation). JSON has a hierarchical structutre and stores meta data in key value pairs or multiple dictionaries as opposed to .csv files. Here we will retrieve data from The APIs, store that data in a dataframe, plot that data using matplotlib and google maps and perform statistical analysis.
Tools USed:
Jupyter Notebook Pandas Library CitiPy Python Requests APIs JSON Traversals
These tools will be used to collect weather data from 500 cities around the world. Then data will be analyzed using pandas and plot the data using matplotlib library and google maps API. Then a ststistical analysis will be performed using ScyPy library.End results will show a series of plots that visually and statistically show the relationship between latitudes and a variety of weather parameters.Jupyter Notebook and data from CityPy Module to get the cities from more than 500 random latitudes and longitudes. then I will perform requests on the open weather map API and retrieve the JSON weather data from these cities. The weather data will be added to a pandas dataframe, where I will use matplotlib to create a series of scatter plots to show the relationship between latitudes and a variety of weather parameters for over 500 cities around the world. As part of the analysis, statistical calculations will be performed on the data using linear regression on the weather parameters in the northern and southern hemispheres. This data will help the team to predict the best time of the year for people to plan their vacation.Then I will export the data, clean it and use the weather data to choose the best cities for vacaton based on certain weather criteria. We will then map these cities using Jupyter GMaps and the Google places API.
Background:
'PlanMyTrip' is a top travel technology company that specializes in internet related services in the hotel and lodging industry. Jack is the head of analysis for the user interface team. He has asked me to help him collect and present data for customer's via the search page which they will then filter based on their preferred travel criteria in order to find their ideal hotel anywhere in the world.
Project Outline:
Jack needs help answering a question: How might we provide real-time suggestions for our client's ideal hotels? Your first task was to define what you meant by "ideal." So, over the course of the conversation, you narrowed that to hotels that were (1) within a given range of latitude and longitude and that (2) provided the right kind of weather for the client. Here's an outline of your project plan: - Task: Collect and analyze weather data across cities worldwide. - Purpose: PlanMyTrip will use the data to recommend ideal hotels based on clients' weather preferences. - Method: Create a Pandas DataFrame with 500 or more of the world's unique cities and their weather data in real time. This process will entail collecting, analyzing, and visualizing the data.
Your analysis of the data will be split into three main parts, or stages.
1) Collect the Data
•	Use the NumPy module to generate more than 1,500 random latitudes and longitudes.
•	Use the citipy module to list the nearest city to the latitudes and longitudes.
•	Use the OpenWeatherMap API to request the current weather data from each unique city in your list.
•	Parse the JSON data from the API request.
•	Collect the following data from the JSON file and add it to a DataFrame:
o	City, country, and date
o	Latitude and longitude
o	Maximum temperature
o	Humidity
o	Cloudiness
o	Wind speed
2) Exploratory Analysis with Visualization
•	Create scatter plots of the weather data for the following comparisons:
o	Latitude versus temperature
o	Latitude versus humidity
o	Latitude versus cloudiness
o	Latitude versus wind speed
•	Determine the correlations for the following weather data:
o	Latitude and temperature
o	Latitude and humidity
o	Latitude and cloudiness
o	Latitude and wind speed
•	Create a series of heatmaps using the Google Maps and Places API that showcases the following:
o	Latitude and temperature
o	Latitude and humidity
o	Latitude and cloudiness
o	Latitude and wind speed
3) Visualize Travel Data
Create a heatmap with pop-up markers that can display information on specific cities based on a customer's travel preferences. Complete these steps:
•	
i.	Filter the Pandas DataFrame based on user inputs for a minimum and maximum temperature.
•	
ii.	Create a heatmap for the new DataFrame.
•	
iii.	Find a hotel from the cities' coordinates using Google's Maps and Places API, and Search Nearby feature.
•	
iv.	Store the name of the first hotel in the DataFrame.
•	
v.	Add pop-up markers to the heatmap that display information about the city, current maximum temperature, and a hotel in the city.
We'll generate random latitudes and longitudes to ensure coordinates are fairly distributed around the world. An algorithm will pick random numbers between the low and high values for latitudes and longitudes. Also, the latitudes and longitudes must be floating-point decimal numbers, as each angular unit of degrees, minutes, and seconds can be represented by a decimal number. To generate random numbers, we can use the Python random module.
During a brainstorming session with Jack, you decide to use the OpenWeatherMap Application Programming Interface (API) to get the weather data for your database. Of course, now comes the tricky part: actually getting the data. You know you can do this using an API–but how do you use an API? Time to dig back in. The weather data is visually displayed on maps for the customer. But, in order for that to happen, you'll need to retrieve the weather from each city in your database. Since this is your first time using an API to get data from a server, your manager would like you to review APIs and how your company retrieves the data.
APIs:
When a client uses our company's website to search for hotels, our search engine will gather information from a variety of websites based on the client's preferences through APIs. An API call is very similar to navigating to a website. An API points to a URL and collects some data from the webpage or server.
When clients request information from our server through our website, they are making an API call. Once our database has the client's search criteria, our servers search the web for hotels on behalf of the client. Now the roles are reversed: our company is the client requesting information, and all the websites where we derive information are the servers.   Using an API has its limitations because not all information from a server is accessible. Most APIs have tiered services, from free to paid. Free services allow access to limited information, and paid subscriptions provide more access based on the payment plan. Our company has a paid subscription for APIs, but we can only get certain information from websites on hotels such as location, accessibility, rooms, prices, services, and amenities, as well as regional weather data. We will now register for an OpenWeatherMap API key, a token granting access, and use it to retrieve weather data. We'll use the API setup to go out and get information when our clients ask us for it. So, now it's time to download the Python Requests Library and register for an API key. The link to register for an OpenweatherMap API key is given below: https://openweathermap.org/api Once the API has reached the website or server, its endpoint, and now we can retrieve data from the website. When we retrieve data from a website, we have to make a "request," which returns data in a text format, not in a tab- or comma-separated file. One format we can use to parse data is JavaScript Object Notation (JSON). The JSON format is also referred to as an "object" or "JSON object." The data inside a JSON object opens and closes with curly braces, much like a Python dictionary. Inside the JSON object is a collection of dictionaries and arrays. To request JSON data over the internet, we use the Requests Library in Python. The Anaconda installation comes with version 2.22 of the Requests Library.
Deliverable 1:
How we will get the weather data for each city for the website. We will need to do the following:
•	Import our dependencies and initialize counters and an empty list that will hold the weather data.
•	Loop through the cities list.
•	Group the cities in sets of 50 to log the process as we find the weather data for each city.
•	Two counters will be needed here: one to log the city count from 1 to 50, and another for the sets.
•	Build the city_url or endpoint for each city.
•	Log the URL and the record and set numbers.
•	Make an API request for each city.
•	Parse the JSON weather data for the following:
•	City, country, and date
•	Latitude and longitude
•	Maximum temperature
•	Humidity
•	Cloudiness
•	Wind speed
•	Add the data to a list in a dictionary format and then convert the list to a DataFrame.
•	Save the data into a .csv file.
Deliverable 2:
Google makes available some of the vast sets of tools that power Google Maps, so that any developer, can use the same technologies and datasets in their own applications. These APIs help developers perform the following tasks:
•	Convert latitudinal and longitudinal coordinates into locations on a map.
•	Create a heatmap based on the density or weight of a feature, such as an earthquake.
•	Identify the hotels or restaurants closest to a given location.
•	Determine the distance between two points. To create custom maps with Google, we will install the gmaps dependency, which is a Jupyter plugin for embedding Google Maps in your notebooks. Using gmaps, we'll create heatmaps and location markers for hotels within a certain radius of the cities where our customers travel. To create this heatmap, we'll need to register for a Google Maps and Places API key on the Google Developer site
