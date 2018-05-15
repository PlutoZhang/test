# Sending a `GET` request in Java

Here is sample code to send a `GET` request to Atlas in Java™.

```
public class JobListener implements Runnable {


    /*
    *   Perform an HTTPs GET at the given jobs URL and credentials
    *   targetURL e.g "https://host:port/Atlas/api/jobs?owner=IBMUSER&prefix=*"         
    *   credentials in the form of base64 encoded string of user:password
    */     
    private String executeGET(String targetURL, String credentials) {
        HttpURLConnection connection = null;         
        try {             
            //Create connection             
            URL url = new URL(targetURL);             
            connection = (HttpURLConnection) url.openConnection();
            connection.setRequestMethod("GET");             
            connection.setRequestProperty("Authorization", credentials);

            //Get Response               
            InputStream inputStream = connection.getInputStream();
            BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(inputStream));                             
            StringBuilder response = new StringBuilder();             
            String line;                          

            //Process the response line by line             
            while ((line = bufferedReader.readLine()) != null) {
                System.out.println(line);             
            }              

            //Cleanup             
            bufferedReader.close();              

            //Return the response message             
            return response.toString();         
        } catch (Exception e) {             
            //handle any error(s)         
        } finally {             
            //Cleanup             
            if (connection != null) {                 
                connection.disconnect();             
            }         
        }     
    }
}
```

**Parent topic:** [Programming Atlas REST APIs](../topics/programrestapi.md)
