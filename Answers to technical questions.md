A demo, for heroku restaurant api call and parsing json, application using React.

# Get Started

1. **How long did you spend on the coding test? What would you add to your solution if you had more time? If you didn't spend much time on the coding test then use this as an opportunity to explain what you would add.**

  I spent less than 3 hours building this test.
  I would add heroku oAuth token to the app to avoid CORS problem but that requires setting up heroku server which was not part of the requirement and heroku setup need time.
  Since I was short on time and getting the api call dodge CORS I just added a curl call on my server https://www.paksof.com/demo/jsoncallparse/herokuApi.php endpoint that returns the heroku call without CORS issues.


2. **What was the most useful feature that was added to the latest version of your chosen language? Please include a snippet of code that shows how you've used it.**

Moved away from my favourite XHR to fetch api finally ... this is more promise based and easily readable
However more control on the XHR ...
submit() {
  const that = this; // as this changes inside the following anonymous function
  fetch("https://www.paksof.com/demo/jsoncallparse/herokuApi.php?city=" + this.state.city)
    .then(function(response) { /* eslint-disable-line */
      return response.json();
    })
    .then(function(json) {
      that.setState({apiResponse: json});
    });
}

3. **How would you track down a performance issue in production? Have you ever had to do this?**

  This app used the endpoint at AWS to call heroku. performance issues can lay in either of the servers.
  I would run a load test on the api call to find out how many concurrent calls can it handle from time to time.
  Log the results and identify the bottleneck. This bottleneck may not be static and this performance log need to be maintained from time to time.

4. **How would you improve the API that you just used?**

  currently this api only returns restaurant list based on one parameter which is city.
  If we have used that data before and cached it for later use then we will miss the updated list which may occur after caching the data. The same api can add a timestamp call on city basis or entire api basis to determine if we have the upto date data from last cache or we should make a brand new call and get newer data.

5. **Please describe yourself using JSON.**

  JSON is the present and future. Currently the client side and server sides are different languages sharing data with each other. JSON api is available in javascript as well as in PHP. That makes it the best interoperability among the client and server. Restrictions in JSON format allows for clean and maintainable code in the future. I am very comfortable with JSON parsing in javascript as well as in PHP. In javascript it is simply an object whereas in PHP it is a hashed array.
