#!/bin/bash

# JS Calendar Setup and Commands

# Check if Angular CLI is installed
if ! command -v ng &> /dev/null
then
    echo "Angular CLI could not be found. Please install Angular CLI first."
    exit 1
fi

echo "Starting JS Calendar Project Setup"

# Function to serve the app
serve_app() {
    echo "Running ng serve to start the development server..."
    ng serve
    echo "Navigate to http://localhost:4200/ to view the app."
}

# Function to generate a new component
generate_component() {
    read -p "Enter component name: " component_name
    echo "Generating component $component_name..."
    ng generate component "$component_name"
}

# Function to build the project
build_project() {
    echo "Building the project..."
    ng build
    echo "Build artifacts stored in the dist/ directory."
}

# Function to run unit tests
run_tests() {
    echo "Running unit tests via Karma..."
    ng test
}

# Function to run end-to-end tests
run_e2e_tests() {
    echo "Running end-to-end tests..."
    ng e2e
}

# Menu to select action
while true; do
    echo "Select an action:"
    echo "1) Serve app (ng serve)"
    echo "2) Generate component (ng generate component)"
    echo "3) Build project (ng build)"
    echo "4) Run unit tests (ng test)"
    echo "5) Run end-to-end tests (ng e2e)"
    echo "6) Exit"
    read -p "Enter choice [1-6]: " choice

    case $choice in
        1)
            serve_app
            ;;
        2)
            generate_component
            ;;
        3)
            build_project
            ;;
        4)
            run_tests
            ;;
        5)
            run_e2e_tests
            ;;
        6)
            echo "Exiting..."
            exit 0
            ;;
        *)
            echo "Invalid choice, please try again."
            ;;
    esac
done
