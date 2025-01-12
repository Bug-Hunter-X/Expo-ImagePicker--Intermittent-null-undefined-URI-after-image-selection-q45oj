# Expo ImagePicker - Intermittent Null/Undefined URI Bug

This repository demonstrates a bug encountered when using the Expo ImagePicker library. The issue involves the `uri` property of the selected image sometimes being `null` or `undefined` after a successful image selection. This leads to an inability to display the selected image.

## Steps to Reproduce

1. Clone this repository.
2. Run `npm install` or `yarn install`.
3. Run the application using Expo Go.
4. Attempt to select an image using the ImagePicker.  Observe that sometimes the image URI is correctly returned and other times it is null or undefined.

## Potential Causes

* Asynchronous operations: There might be a race condition, where the image URI isn't fully resolved before the component attempts to use it.
* Permissions: Though permissions are handled by Expo, occasional permission issues might lead to unexpected behavior. 
* Platform inconsistencies: There might be variations in how ImagePicker behaves across different iOS and Android devices.

## Workaround (as shown in bugSolution.js)

The provided workaround utilizes a Promise to ensure the image is properly loaded before attempting to display it.  Error handling is included to gracefully manage situations where the URI is still null or undefined despite the delay.