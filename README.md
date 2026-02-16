
# AI Software Engineer Assignment (JS/TS)

This repository contains my solution to the AI Software Engineer Assignment.  
It includes a minimal bug fix, test validation, pinned dependencies, and a Docker setup to ensure reproducible execution.

---

## Running Tests Locally

1. Install dependencies:

   npm install

2. Run the test suite:

   npm test

---

## Running Tests with Docker

Build the Docker image:

   docker build -t ai-assignment .

Run the test suite inside the container:

   docker run --rm ai-assignment

The container installs dependencies using `npm install` and runs the tests by default.
