# Scripting-Task-Guvi
# Create script file
vi Check_HTTP_ERROR_CODE.sh
# write scrip using VI editor
#!/bin/bash

# HTTP Status Code Checker for guvi.in

URL="https://www.guvi.in"

HTTP_CODE=$(curl -o /dev/null -s -w "%{http_code}" $URL)

echo "URL: $URL"
echo "HTTP Response Code: $HTTP_CODE"
echo "-----------------------------------"

if [ "$HTTP_CODE" -ge 200 ] && [ "$HTTP_CODE" -lt 300 ]; then
    echo "SUCCESS: Site is UP! ($HTTP_CODE - OK)"

elif [ "$HTTP_CODE" -ge 300 ] && [ "$HTTP_CODE" -lt 400 ]; then
    echo "REDIRECT: Site redirected ($HTTP_CODE - Redirection)"

elif [ "$HTTP_CODE" -ge 400 ] && [ "$HTTP_CODE" -lt 500 ]; then
    echo "FAILURE: Client Error! ($HTTP_CODE - Check URL)"

elif [ "$HTTP_CODE" -ge 500 ]; then
    echo "FAILURE: Server Error! ($HTTP_CODE - Server Down)"

else
    echo "FAILURE: Unknown response ($HTTP_CODE)"
fi
# Give execute permission on script file command
chmod 755 Check_HTTP_ERROR_CODE.sh
# Run script file command
./Check_HTTP_ERROR_CODE.sh
# View the script content linux command
cat Check_HTTP_ERROR_CODE.sh
