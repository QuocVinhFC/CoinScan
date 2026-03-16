# iOS Screen Flow

## Overview
This document details the iOS screen flow for the CoinScan app, focusing on the user interface sequences and the internal API processing involved in scanning coins.

## Screen Flow
1. **Launch Screen**: The app opens directly to the camera interface.
2. **Capture Image**: Users can capture an image of a coin.
3. **Image Preview**: Users can preview the captured image before sending it for analysis.
4. **Processing Screen**: After the user confirms the image, the app shows a loading indicator while the image is being processed.
5. **Results Screen**: Once processing is complete, the results (coin identification) are displayed to the user.

## Scan Flow
The scan process involves the following steps:
1. **Sending Image for Analysis**
   - The app sends a POST request to `https://scanner-services.fuentechsoft.com/coins-identifier/scan-analyze-images` with the captured image.
   - The request should contain the appropriate headers and the image data.

2. **Fetching Coin List**
   - After processing the image, the app performs a GET request to fetch the list of coins from `https://coins-banknotes.fuentechsoft.com/coin/api/v1/coins`.

3. **Hashing the Response**
   - The returned JSON string from the API is hashed using SHA-256 for data integrity and security purposes.
   - Use the following method to hash the JSON:
     ```swift
     func sha256(_ data: Data) -> String {
         let hashedData = SHA256.hash(data: data)
         return hashedData.map { String(format: "%02hhx", $0) }.joined()
     }
     ```

## Conclusion
This iOS screen flow and accompanying API hashing workflow are essential for the seamless functioning of the CoinScan application, ensuring that users can effectively identify and verify coins using their iPhones.