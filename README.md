# Temperature-Humidity

1. [Table of Contents](#Table-of-Contents)
2. [Overview](#Overview)
3. [API Endpoints](#API-endpoints)
      - Submit Daily Data
4. [Request Body Format](#Request-Body-Format)
5. [Setup Instructions](#Setup-Instructions)
6. [Example Usage](#Example-Usage)
7. [Conclusion](#Conclusion)

## Overview

The Temperature-Humidity API allows users to submit and retrieve daily temperature and humidity data recorded by various devices. The data is structured by date and time, with each time entry containing information from multiple devices.

## API Endpoints

### Submit Daily Data
- **Endpoint:** /dailyData
- **Method:** POST
- **Content-Type:** application/xml

## Request Body Format

The request body should be in XML format and contain the following elements:
- **<dailyData>:** Root element that encapsulates the daily data.
      - **<date>:** Specifies the date of the recorded data in YYYY-MM-DD format.
      - **<hourlyData>:** Contains the hourly data entries.
            - **<time>:** Specifies the time of the recorded data in HH:MM format.
            - **<device>:** Contains data from individual devices.
                - **<id>:** The unique identifier for the device.
                - **<temperature>:** The temperature recorded by the device.
                - **<humidity>:** The humidity recorded by the device.
  
## Setup Instructions

- **Clone the Repository:** Clone the project repository to your local machine.
- **Install Dependencies:** Run the appropriate command to install dependencies (e.g., mvn install for - Maven projects).
- **Start the Server:** Start the server using your preferred method (e.g., mvn spring-boot:run for Spring Boot projects).

## Example Usage

To submit daily temperature and humidity data, send a POST request to the /dailyData endpoint with the following XML body:
```
<dailyData>
    <date>2015-06-01</date>
    <hourlyData>
        <time>10:00</time>
        <device>
            <id>34</id>
            <temperature>70</temperature>
            <humidity>11</humidity>
        </device>
        <device>
            <id>35</id>
            <temperature>72</temperature>
            <humidity>12</humidity>
        </device>
    </hourlyData>
    <hourlyData>
        <time>11:00</time>
        <device>
            <id>34</id>
            <temperature>71</temperature>
            <humidity>10</humidity>
        </device>
    </hourlyData>
</dailyData>
```
A successful response will confirm that the data has been submitted:
```
{
    "message": "Daily data submitted successfully.",
    "submissionId": 67890
}
```

## Conclusion

The Temperature-Humidity API provides a structured way to submit and retrieve daily temperature and humidity data from various devices. This documentation outlines the required request format, expected responses, and provides examples to help users get started with the API.
