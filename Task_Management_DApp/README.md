# Task Management Rollup Server

This project demonstrates a simple task management system that interacts with a rollup server. It processes task updates and inspection requests, communicating with the server via HTTP requests. The code utilizes the `ethers` library for handling hexadecimal data.

## Features

- **Handle Task Updates**: Add or update tasks based on incoming requests.
- **Inspect Tasks**: Retrieve the current state of tasks.
- **Integration with Rollup Server**: Communicate with a specified rollup server to report task updates and receive status updates.

## Prerequisites

- Node.js
- `ethers` library (`npm install ethers`)

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Install dependencies:
   ```bash
   npm install ethers
   ```

## Configuration

Ensure you have the following environment variable set:

- `ROLLUP_HTTP_SERVER_URL`: The URL of the rollup HTTP server.

You can set this variable in your environment or in a `.env` file.

## Usage

1. **Run the Script**:

   Execute the script using Node.js:
   ```bash
   node <script-file-name>.js
   ```

2. **Functionality**:

   - **`handle_advance(data)`**: Processes task updates based on the provided `data`. Updates are sent to the rollup server if valid, or a rejection notice is sent if the format is invalid.
   - **`handle_inspect(data)`**: Handles inspection requests, returning the current state of tasks or an error message if the route is not implemented.
   - **Polling**: The script continuously polls the rollup server for finish requests, processes them, and updates the status accordingly.

## Code Overview

- **`hex2Object(hex)`**: Converts a hexadecimal string to a JavaScript object.
- **`obj2Hex(obj)`**: Converts a JavaScript object to a hexadecimal string.
- **`tasks`**: An array that stores the current tasks.
- **`handlers`**: An object mapping request types to their corresponding handler functions (`handle_advance` and `handle_inspect`).
- **Polling Loop**: Continuously fetches the finish status from the rollup server and processes incoming requests.
