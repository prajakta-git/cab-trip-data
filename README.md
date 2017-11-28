# Cab Trip API
This API will let user select cab trips per medallion on given date and total number of trips for multiple medallion Ids. 

# Application Set-up on local machine
1.	Extract Zip file “simple-cab-Data.zip” which has two spring boot applications simple-cab-server and simple-cab-client.
2.	The database used for the server application is MSSQL. The application.properties file has all the connection properties. These connection properties should be updated as per the users DB connection properties.
3.	Run the server application as a spring boot application.
4.	The Client application “simple-cab-client” is another spring boot application which will consume the api.
5.	For testing purpose sample medallion data is provided which can be updated. Modify below highlighted code in SimpleCabClientApplication.java file.

public CommandLineRunner run(RestTemplate restTemplate) throws Exception {
		return args -> {
			List data = restTemplate.getForObject("http://localhost:8080/api/trippermed/40E882BDD06233B5C99288FFED13F6A1,1B96632294C366D4BDF08099BCAA6E39", List.class);
			
			
			Integer data2 = restTemplate.getForObject("http://localhost:8080/api/totaltrips/40E882BDD06233B5C99288FFED13F6A1/2013-12-01", Integer.class);

			log.info("Trips per Medallion: " + data.toString());
			log.info("Total trip for Medallion on given date: " + data2.toString());
		};
	}
6.	Run the application as spring boot application and the output will be displayed on the console.
7.	It encodes the image to base64 and makes a REST post call to save the image and return image ID, which can be used to retrieve the image again.

