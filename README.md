[Bash_SCRIPT.txt](https://github.com/Taman26kaur/custom-linux-command/files/13886611/Bash_SCRIPT.txt)# custom-linux-command
Scenario: There is a customer who came to you with a problem to have a custom linux command for his operations. Your task is to understand the problem and create a linux command via bash script as per the instructions. 
Command name - internsctl
Command version - v0.1.0

# Run the following commands in linux terminal
Step 1: Create a New File-- You can use a text editor like nano and save the file with the name internsct1. 
nano internsct1

Step 2: Make the Script Executable-- Make the script executable by running the following command:
chmod +x internsct1

Step 3: Move the Script to a Directory in the PATH-- Move SCRIPT to a directory that is included in your system's PATH. A common directory for user scripts is /usr/local/bin/:
sudo mv /current_path/internsct1 /usr/local/bin/

Test the Script-- You should be able to run the internsct1 command from any terminal window. 

# Bash Script
[Uploading Bas#!/bin/bash

# Define version
VERSION="v0.1.0"

# Function to display manual page
show_manual() {
    echo "internsctl(1) - Custom Linux command"
    echo
    echo "NAME"
    echo "    internsctl - Perform various system operations"
    echo
    echo "SYNOPSIS"
    echo "    internsctl [OPTION]... [COMMAND] [ARGS]..."
    echo
    echo "DESCRIPTION"
    echo "    internsctl is a custom Linux command to perform various system operations."
    echo
    echo "OPTIONS"
    echo "    --help      Display this help message"
    echo "    --version   Display version information"
    echo
    echo "COMMANDS"
    echo "    cpu         Get CPU information"
    echo "    memory      Get memory information"
    echo "    user        Manage user accounts"
    echo "    file        Get information about a file"
}

# Function to display help message
show_help() {
    echo "Usage: internsctl [OPTION]... [COMMAND] [ARGS]..."
    echo "Perform various system operations."
    echo
    echo "Options:"
    echo "  --help      Display this help message"
    echo "  --version   Display version information"
}

# Function to display version
show_version() {
    echo "internsctl $VERSION"
}

# Function to get CPU information
get_cpu_info() {
    lscpu
}

# Function to get memory information
get_memory_info() {
    free
}

# Function to create a new user
create_user() {
    if [ $# -eq 0 ]; then
        echo "Usage: internsctl user create <username>"
    else
        sudo useradd -m $1
        echo "User '$1' created successfully."
    fi
}

# Function to list users
list_users() {
    if [ "$1" == "--sudo-only" ]; then
        getent passwd | cut -d: -f1,4 | awk -F: '$2 == 0 {print $1}'
    else
        getent passwd | cut -d: -f1
    fi
}

# Function to get file information
get_file_info() {
    local file=$1

    if [ ! -e "$file" ]; then
        echo "File not found: $file"
        exit 1
    fi

    local size=$(stat -c%s "$file")
    local permissions=$(stat -c%a "$file")
    local owner=$(stat -c%U "$file")
    local last_modified=$(stat -c%y "$file")

    echo "File: $file"
    echo "Access: $permissions"
    echo "Size(B): $size"
    echo "Owner: $owner"
    echo "Modify: $last_modified"
}

# Parse command line arguments
case "$1" in
    "cpu")
        shift
        get_cpu_info
        ;;
    "memory")
        shift
        get_memory_info
        ;;
    "user")
        shift
        case "$1" in
            "create")
                shift
                create_user "$@"
                ;;
            "list")
                shift
                list_users "$@"
                ;;
            *)
                show_help
                ;;
        esac
        ;;
    "file")
        shift
        case "$1" in
            "getinfo")
                shift
                get_file_info "$@"
                ;;
            *)
                show_help
                ;;
        esac
        ;;
    "--help")
        show_manual
        ;;
    "--version")
        show_version
        ;;
    *)
        show_help
        ;;
esac
h_SCRIPT.txt…]()



# Flow Diagram

![7flow](https://github.com/Taman26kaur/custom-linux-command/assets/100130372/bf3d0be1-3175-4917-a8c7-a2f71b8f586d)

# SCREENSHORT OF OUTPUTS ARE ATTACHED

![1 ](https://github.com/Taman26kaur/custom-linux-command/assets/100130372/95c484d7-2f97-4d70-ab6f-af4f485521a4)
![2](https://github.com/Taman26kaur/custom-linux-command/assets/100130372/54200019-534e-4604-bd8b-8fc0d99e7de9)
![3](https://github.com/Taman26kaur/custom-linux-command/assets/100130372/8d5e54b4-82c9-4e2d-a50b-8326eae6fb22)
![4](https://github.com/Taman26kaur/custom-linux-command/assets/100130372/5009e1ff-438b-484d-8fda-d88ebd85ad87)
![5](https://github.com/Taman26kaur/custom-linux-command/assets/100130372/6d0893ba-262a-4bfe-a355-944a0a808786)
![6](https://github.com/Taman26kaur/custom-linux-command/assets/100130372/812e222a-3818-4280-a3ca-bf66c746e79f)

