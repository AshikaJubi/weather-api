# Exercise 11: API Integration and Data Processing

### Reg No: 212221040013

## AIM:
To retrieve weather data using an API, extract the temperature in Kelvin, convert it to Celsius, and display it with two decimal places.

## Activities Required:
1. HTTP Request
2. Assign
3. Message Box

## Procedure:
1. Open **UiPath Studio** and create a new process called **WeatherAPIIntegration**.

2. In the **Activities Panel**, search for **HTTP Request** and drag it into the **Designer Panel**.

3. Set the **Endpoint** property of the **HTTP Request** to `"https://api.openweathermap.org/data/2.5/weather?q=CityName&appid=YourAPIKey"` (replace `CityName` with the target city and `YourAPIKey` with your API key).

4. Set the **Method** property of **HTTP Request** to `GET` to retrieve weather data.

5. Use an **Assign** activity to parse the JSON response and extract the temperature data:
   - Set `weatherJSON` to `Newtonsoft.Json.Linq.JObject.Parse(responseString)`, where `responseString` is the output of **HTTP Request**.

6. Use an **Assign** activity to retrieve the temperature in Kelvin and convert it to Celsius:
   - Set `kelvinTemp` to `Convert.ToDouble(weatherJSON("main")("temp").ToString())`.
   - Set `celsiusTemp` to `Math.Round(kelvinTemp - 273.15, 2)` to convert and round the temperature.

7. Use a **Message Box** activity to display the temperature in Celsius with two decimal places:
   - Set the **Text** property to `celsiusTemp.ToString("F2")`.

8. Save and Run the workflow.

## Workflow:
![image](https://github.com/user-attachments/assets/f2b234ff-5a73-4d97-aefb-471a9a1911bd)

## Expected Output:
![image](https://github.com/user-attachments/assets/c833c943-25d1-4f7c-8e17-660a1f756510)


## Result:
The weather data is successfully retrieved, and the temperature is displayed in Celsius with two decimal precision.
