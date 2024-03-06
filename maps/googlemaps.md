# Google Maps Static API playground

The Google Maps Static API allows you to generate static map images that can be embedded in websites, applications, or any digital platform. This service is useful for scenarios where an interactive map is unnecessary, and a simple map image suffices. To use the Google Maps Static API, you need to construct a URL with specific parameters that define the map's appearance and content.

Here's a basic introduction to using the Google Maps Static API:

## Obtaining an API Key
Before you can start using the Google Maps Static API, you need to obtain an API key from Google. This key is essential for authenticating your requests to the Google Maps platform. You can get your API key by signing up or logging into your Google Cloud account, creating a project, and enabling the Maps Static API for that project. This will require a credit card and you to set up billing, as Google Cloud Platform provides you with a free trial period but may require billing information for continued use beyond the trial. The tasks here will not come close to the free tier (seen here https://mapsplatform.google.com/pricing/)

Official steps by Google to do this: https://developers.google.com/maps/documentation/maps-static/get-api-key

To generate a Google Maps Static API project, create an API key limited to the Static Maps API, and restrict it to localhost and your current computer's public IP address, you can follow these steps based on the information gathered:

### Step 1: Create a Google Cloud Project
1. Log in to the [Google Cloud Console](https://console.cloud.google.com/).
2. Click the Menu Bar (Hamburger Icon) > IAM & Admin, and create a new Project.
3. Enter a descriptive name for your project and leave the Location field as default.
4. Click "Create" to set up your new project.

### Step 2: Enable Google Workspace APIs
1. In the Google Cloud Console, navigate to APIs & Services > Library.
2. Search for "Maps Static API" and click on the API in the search results.
3. Click "Enable" to activate the Maps Static API for your project.

### Step 3: Create API Access Credentials
1. Go to APIs & Services > Credentials in the Google Cloud Console.
2. Click "Create credentials" and choose "API key" from the options.
3. Your new API key will be displayed. Make sure to copy this API key for use in your application. You can also find it later in the "API keys" section under Credentials.

### Step 4: Restrict Your API Key
To ensure your API key is secure and can only be used in your specified environments, you'll want to apply restrictions:
1. Go to the Credentials page where your API keys are listed.
2. Click on the edit icon next to your API key to modify its settings.
3. Under "Application restrictions," select "HTTP referrers (websites)" for web use or "IP addresses (web servers, cron jobs, etc.)" for server-side applications.
4. Add your localhost address (e.g., `http://localhost/*`) and your current public IP address (google `what's my ip` to find it!) to the list of allowed IP addresses. This ensures the key can only be used from these sources.
5. Save your changes.

### Step 5: Use Your API Key
Once you've set up and restricted your API key, you can use it in your application. For web applications, include the API key in your requests to the Maps Static API, like so:

```
https://maps.googleapis.com/maps/api/staticmap?center=Paris&zoom=12&size=400x400&key=YOUR_API_KEY
```
Be sure to replace `YOUR_API_KEY` with the actual API key you just created. Now you can proceed with exploring the Google Maps API

### Note:
- To get more detailed information or if you encounter any issues, refer to the [official documentation](https://developers.google.com/maps/documentation/maps-static/start) for the Google Maps Static API.

By following these steps, you'll be able to securely use the Google Maps Static API restricted to specific environments, ensuring the safety and integrity of your API key.

## Constructing a Google Static Maps API Request

https://developers.google.com/maps/documentation/maps-static/start#URL_Parameters

A Google Maps Static API request URL consists of several components, including the base URL, required parameters (center location, zoom level, and size of the map), and your API key. 

Here's a breakdown of the key components:

- **Base URL**: The starting point of your request URL, which for the Google Maps Static API is `https://maps.googleapis.com/maps/api/staticmap`.

### Location Parameters

https://developers.google.com/maps/documentation/maps-static/start#location

- **Center Location**: This parameter defines the central point of your map, which can be specified using latitude and longitude coordinates or a string address.

- **Zoom Level**: This parameter sets the zoom level of the map, where lower numbers show larger areas and higher numbers zoom in for more detail.

### Map Parameters ###

https://developers.google.com/maps/documentation/maps-static/start#map-parameters

- **Size**: This defines the dimensions of the resulting map image in pixels, formatted as `width x height`.

### API Key Parameter ###

https://developers.google.com/maps/documentation/maps-static/start#key-and-signature-parameters

- **API Key**: Your unique API key must be appended to the request URL to authenticate your request. It is important to have this key locked as indicated above to avoid someone else using your account without permission. 

An example of a simple API request URL might look like this:

```
https://maps.googleapis.com/maps/api/staticmap?center=Lindsay%2C+ON&zoom=12&size=600x600&key=YOUR_API_KEY
```
In this example, the map is centered on Lindsay, ON (where the comma is URL encoded as `%2C` and the space encoded as a `+` (plus) character), with a zoom level of 12, and the size of the map image is set to 600x600 pixels. You would replace `YOUR_API_KEY` with your actual API key obtained from Google Cloud Platform.

### Further Customization using Feature Parameters
The Google Maps Static API also allows for further customization of your map images, such as adding markers, lines, or polygons to highlight specific areas or routes. These additional features are specified using extra parameters in your API request URL.

https://developers.google.com/maps/documentation/maps-static/start#feature-parameters

For more detailed information and advanced customization options, you can refer to the [official Google Maps Static API documentation](https://developers.google.com/maps/documentation/maps-static/start).

This introduction should help you get started with the Google Maps Static API. Remember to consult the official documentation for a more comprehensive guide and to ensure you're familiar with Google's terms of service and usage limits.
