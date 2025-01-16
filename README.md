# Demo App for OBIS API using Svelte

## Overview
This is a small demo app that allows users to search for marine species in a specified sea area and depth by utilizing the OBIS API. It provides a simple interface to explore biodiversity data in different marine environments.

## Features
- Enter a sea region (e.g., "North Sea") and a depth (in meters) to retrieve data.
- Fetches and displays a list of marine species based on the entered parameters.

## Example
Entering `North Sea` and `50` as inputs could yield the following results:

- Pennatula
- Methylophilaceae
- Sigambra parva
- Oligochaeta
- Biota incertae sedis
- Macronectes giganteus
- Thunnus albacares
- Morus bassanus
- Copepoda
- Mirounga leonina

(Note: Results may vary based on the API's current data.)

## Setup and Run
To run this app locally:

1. Ensure you have [Node.js](https://nodejs.org/) installed.
2. Clone this repository:
   ```
   git clone <repository-url>
   cd <repository-folder>
   ```
3. Install the dependencies:
   ```
   npm install
   ```
4. Start the development server:
   ```
   npm run dev
   ```
5. Open your browser and navigate to `http://localhost:5173` to view the app.

## Credits and Disclaimer
This code was entirely created using ChatGPT with user-provided guidance. While functional, it is intended as a demo and may require further optimization or customization for production use.

Even this Readme.md was created by ChatGPT.