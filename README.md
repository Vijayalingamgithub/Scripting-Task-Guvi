# Scripting-Task-Guvi-1
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
-------------------------------------------------------------------------------------------------------------
# Scripting Task-2
# Create  file
vi replacetext.txt
# Replace all occurrence of the word "give" with "learning" from 5th line till the end in only those lines that contain the word "welcome"
sed -i '5,$ {/welcome/ s/give/learning/g}' replacetext.txt
# View the script content linux command
cat replacetext.txt
