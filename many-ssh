#!/bin/bash

# Configuration
ATTACKS=10         # Number of failed attempts to try
TARGET_USER="testuser" # A valid user on the target machine
TARGET_IP="192.168.1.10" # Replace with the target machine's IP
BAD_PASSWORD="ThisIsNotTheRealPassword"

echo "Starting $ATTACKS failed SSH attempts against $TARGET_IP..."
COUNT=1

while [ $COUNT -le $ATTACKS ]; do
    echo "Attempt $COUNT..."
    
    # Use sshpass to provide the bad password non-interactively
    # The 'ssh -o StrictHostKeyChecking=no' is to bypass the host key prompt
    sshpass -p "$BAD_PASSWORD" ssh -o StrictHostKeyChecking=no "$TARGET_USER@$TARGET_IP" 'exit' 2>/dev/null
    
    # Increment the counter
    COUNT=$((COUNT + 1))
    
    # Optional: Small delay to ensure logs are processed individually
    sleep 0.5 
done

echo "Finished $ATTACKS attempts."
