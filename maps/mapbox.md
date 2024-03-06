# MapBox Static API playground
Open the URL https://docs.mapbox.com/playground/static/ and use the provided tool to pan the map around. This is a website to explore and modify the provided URL to load a specific area. It has many parts that need to be filled in before the request will work (indicated below using brackets around a value, like this: `{value}` where you must replace it with an appropriate input (PS do not keep the `{bracket}` around it!). 

```
https://api.mapbox.com/styles/v1/{username}/{style_id}/static/{overlay}/{lon},{lat},{zoom},{bearing},{pitch}|{auto}|{bbox}/{width}x{height}{padding}{@2x}?access_token={YOUR_ACCESS_TOKEN]
```
This URL tells Mapbox's Static API service exactly what map you want. To understand how to use Mapbox's Static API, review below to test

### See the full API guide here: https://docs.mapbox.com/api/maps/static-images/


## Understanding the URL Structure

A typical URL consists of several parts, each serving a specific function:

1. **Protocol**: This is the beginning part of the URL, indicating the type of protocol the browser must use. For web URLs, this is usually `http` or `https` (the secure version). For example, in `https://api.mapbox.com`, `https` is the protocol.

2. **Domain**: This part identifies the server that hosts the content. In the example above, `api.mapbox.com` is the domain, which points to Mapbox's API server.

3. **Path**: After the domain, the path specifies the location on the server where the specific resources (like an API endpoint) can be found. For instance, `/styles/v1/mapbox/streets-v11/static/` could be a path to a specific style of map in the Static API.

4. **Parameters**: These are additional options that you can add to the URL to customize the request. They are added after a `?` and separated by `&`. Each parameter has a key and a value, which MapBox Static API uses one required parameter to specify the `access_token`. If there were other URL parameters to add, it would required a & for the next set of key and value pair. For example, `?first=value1&second=number2&third=3` has three parameter values, the first has a value of value1, and the second parameter second has a value of number2. Can you tell what the 3rd parameter value is?

## Constructing a Mapbox Static API URL

To use Mapbox's Static API, you'll need to construct a URL that specifies the map's style, location, size, and more. Here's a step-by-step guide:

1. **Start with the Base URL**: The base URL for Mapbox's Static API looks something like this: `https://api.mapbox.com/styles/v1/{username}/{style_id}/static/`. You'll need to replace `{username}` with your Mapbox username and `{style_id}` with the ID of the map style defined in the account specified that you want to use. If using the pre-defined styles from https://docs.mapbox.com/api/maps/styles/#mapbox-styles, then the username is going to be `mapbox` because that is where the style is defined.  

2. **Specify the Location**: After the base URL, you need to specify the longitude, latitude, and zoom level for your map. This part of the URL looks like `{longitude},{latitude},{zoom}`. For example, `-122.4241,37.78,14` could represent a longitude of -122.4241, a latitude of 37.78, and a zoom level of 14.

3. **Choose the Image Size**: The next part of the URL specifies the size of the image in pixels, like `600x400`.

4. **Add API Access Token**: To authenticate your request, you'll need to add your Mapbox access token as a parameter. This is done by appending `?access_token=YOUR_MAPBOX_ACCESS_TOKEN` to the end of the URL.

## Example URL

Putting it all together, a complete URL to request a static map image might look like this:

```
https://api.mapbox.com/styles/v1/mapbox/streets-v11/static/-122.4241,37.78,14/600x400?access_token=YOUR_MAPBOX_ACCESS_TOKEN
```

This URL requests a 600x400 pixel image of the `streets-v11` map style centered at longitude -122.4241, latitude 37.78, with a zoom level of 14.

For more detailed information and advanced options, check the [Mapbox Static Images API documentation](https://docs.mapbox.com/api/maps/static-images/).

# Exploring the Mapbox Static API

Try modifying the URL yourself without the provided web tool. Here are some questions to guide your exploration:

## Getting Started

1. **How do you obtain a Mapbox API key?**
   - Sign up or log in to your Mapbox account.
   - Navigate to your [Account Dashboard](https://account.mapbox.com/).
   - Click on "Tokens" in the sidebar.
   - Here, you can view your default public token or create a new one by clicking "Create a token".
   - Copy the token to use in your API requests.
   - You also will need your username, which can be found on the same account dashboard titled "Account". 

## Explore the MapBox Static API

2. **What is the structure of a Mapbox Static API URL?**
   - Break down the components of a typical Mapbox Static API request URL, identifying the protocol, domain, path, and parameters (explained above).

3. **How does changing the zoom level in the URL affect the map's detail?**
   - Experiment with different zoom levels in your API requests. Observe how increasing or decreasing the zoom level changes the amount of detail on the map.

4. **How can you centre a map on a specific landmark or location using latitude and longitude coordinates?**
   - Choose a landmark or location, find its coordinates, and use them in your API request. Note how the map centers on the specified point. Try using the Frost campus location at 44.341474, -78.741117.

5. **What happens when you switch the map style in the API request?**
   - Try different style IDs (like `streets-v11`, `outdoors-v11`, `light-v10`, `dark-v10`, etc.) in your request and observe how the map's appearance changes. See the various styles at https://docs.mapbox.com/api/maps/styles/#mapbox-styles. 

6. **What is at this location**
   - Zoom close to location latitude 43.429111, longitude -80.330861 using an aerial image map style for a fun surprise. 
<details>
   <summary>Click for answer (add your token):</summary>
https://api.mapbox.com/styles/v1/mapbox/satellite-v9/static/-80.330861,43.429111,17,0/300x200?access_token=YOUR_MAPBOX_ACCESS_TOKEN
</details>

7. **Can you display a map that shows the traffic layer?**
   - Explore the documentation to find out how to overlay real-time traffic information on your map.

By answering these questions and following through with the exercises, you'll gain a deeper understanding of how URLs work using Mapbox Static API as an example. 
Remember to respect Mapbox's [terms of service](https://www.mapbox.com/legal/tos/) and usage limits when using the API.
