# Tauri v2 + SvelteKit + TypeScript + Diesel + postgres

## This template initializes the following

### Frontend

- SvelteKit
- Typscript
- Eslint + Prettier
- AirBnb config
- Vite

### Backend

- Diesel ORM
- postgres connection with example env
- starter commands implementing user authentication

## Project structure/design

- backend files are in server dir, frontend files in src dir
- database calls are handled in rust and connected to the frontend with tauri commands
- tauri commands are in server/src/commands dir
- server/src/routes dir structure Rust logic according to associated frontend route
- server/src/db dir contains database query logic
- each tauri command has an associated bin file to test the Rust logic w/o the frontend
  - this allows developing the Rust code first then building the frontend
  - run a desired bin by entering `cargo run --bin {bin name}`

### Misc

- all packages are updated at time of editing this readme, 14 Nov 2024
- html/css/frontend files are as created at apps initialization, tune to taste
- pnpm

### Who this is for

This isn't my first Tauri app, however this time I wanted to leverage Rust more. My goal is to transfer as much logic to Rust as possible. This template is for those who want to do the same, or at least have a starting point to build from.

If you enjoy coding in Rust and are interested in leaning more into it, then this template may suit you. If you don't like Svelte, just replace the FE files with what you prefer.

So far, what's working for me is to develop Rust functions in the server/src/bin dir that I intend to use to fetch/manipulate data that will be returned to the frontend. Once the binary does what I want it to do, I can build out the tauri command and frontend as necessary.

For example, before creating a frontend form, tauri command, and rust logic to create a new user in the database; I would first sandbox the logic in a binary. See server/src/bin/create_user.rs. When the rust logic acts as desired, connecting the frontend is much simpler.

### Getting Started

1. Pull the code
2. install deps `pnpm i`
3. connect to db by copying server/.env.example to server/.env with valid variables
4. initialize database `cd server` then `diesel migration run`
5. test valid database connection `cd server && cargo test`
6. run the software in dev mode `pnpm run tauri dev`
7. form submissions on FE are being logged, open inspection window to view console

![landing page](./static/landing.png)
