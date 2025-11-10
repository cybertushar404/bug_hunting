# Retrieving Passive URLs:
```
https://web.archive.org/cdx/search/cdx?url=*.example.com/*&collapse=urlkey&output=text&fl=original
```
# Fetching Files with Specific Extensions:
```
https://web.archive.org/cdx/search/cdx?url=*.example.com/*&collapse=urlkey&output=text&fl=original&filter=original:.*\.(xls|xml|xlsx|json|pdf|sql|doc|docx|pptx|txt|zip|tar\.gz|tgz|bak|7z|rar|log|cache|secret|db|backup|yml|gz|git|config|csv|yaml|md|md5|exe|dll|bin|ini|bat|sh|tar|deb|rpm|iso|img|apk|msi|env|dmg|tmp|crt|pem|key|pub|asc)$
```
 Accessing Deleted Files via 404 Errors:
 Go to webarchive and paste the 404 URL you found from the Wayback Archive into the search bar then hit enter. You’ll see the entire timeline for that URL. Select an older snapshot from the timeline and click on it. This will provide you with a download link for the deleted files. Isn’t that amazing? You can access all the deleted sensitive files from any website this way.


# Automation:
```

 #!/bin/bash
# Prompt for the domain name.
read -p "Enter the domain (e.g., example.com): " domain

echo "Fetching all URLs from the Wayback Machine..."
# Fetch all URLs for the given domain.
curl -G "https://web.archive.org/cdx/search/cdx" \
  --data-urlencode "url=*.$domain/*" \
  --data-urlencode "collapse=urlkey" \
  --data-urlencode "output=text" \
  --data-urlencode "fl=original" \
  -o all_urls.txt

echo "Fetching URLs with specific file extensions..."
# Fetch only URLs ending with certain file extensions.
# (Adjust the extension list if necessary.)
curl "https://web.archive.org/cdx/search/cdx?url=*.$domain/*&collapse=urlkey&output=text&fl=original&filter=original:.*\.(xls|xml|xlsx|json|pdf|sql|doc|docx|pptx|txt|git|zip|tar\.gz|tgz|bak|7z|rar|log|cache|secret|db|backup|yml|gz|config|csv|yaml|md|md5|exe|dll|bin|ini|bat|sh|tar|deb|rpm|iso|img|env|apk|msi|dmg|tmp|crt|pem|key|pub|asc)$" \
  -o filtered_urls.txt

echo "Done! Results saved to:"
echo "  - all_urls.txt (all URLs)"
echo "  - filtered_urls.txt (URLs with specific file extensions)"
```
