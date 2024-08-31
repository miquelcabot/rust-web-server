# Simple Web Server with Thread Pool in Rust

This project is a basic web server written in Rust that leverages a thread pool to handle incoming requests. It listens on `127.0.0.1:7878` and serves simple HTML pages. The server is capable of handling multiple requests concurrently by utilizing a thread pool implemented in the `lib.rs` file.

## Features

- **Multithreading**: Uses a thread pool to manage and reuse threads, which improves performance by avoiding the overhead of creating and destroying threads for each request.
- **Simple Routing**: Supports basic routes such as `/` for the homepage and `/sleep` which simulates a long-running task by introducing a delay.
- **Graceful Shutdown**: The thread pool is designed to shut down gracefully, ensuring all threads complete their work before the application exits.

## File Structure

- `main.rs`: The entry point of the application. Sets up the server and manages incoming connections.
- `lib.rs`: Contains the implementation of the thread pool and worker threads.

## How It Works

1. **ThreadPool Creation**: The `ThreadPool::new(4)` creates a thread pool with 4 worker threads.
2. **Handling Requests**: The server listens for incoming TCP connections. For each connection, it uses the thread pool to process the request asynchronously.
3. **Request Handling**:
   - `GET /` serves the `hello.html` file.
   - `GET /sleep` serves the `hello.html` file after a 5-second delay.
   - Any other request returns a `404 NOT FOUND` response with the content of `404.html`.

## Running the Server

1. Ensure you have [Rust installed](https://www.rust-lang.org/learn/get-started).
2. Clone this repository or download the source code.
3. Place the `hello.html` and `404.html` files in the root of the project directory.
4. Run the server using Cargo:
   ```sh
   cargo run
5. Open your browser and navigate to `http://127.0.0.1:7878`.

