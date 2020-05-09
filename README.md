# tomstorms / Snippets / PHP Clean URL

Snippet code demonstrating how you could get a clean URL from a user supplied domain name.


```

function cleanURL($url) {

  // Remove http, https and trailing slashes from the url.
	$domainURL = str_ireplace('http://', '', $url);
	$domainURL = str_ireplace('https://', '', $domainURL);
	$domainURL = rtrim($domainURL, '/');

  // Check if the URL contains a slash after cleaning.
  // This would be sub-pages of the domain.
	$pageURL = '';
	$hasSlash = stripos($domainURL, '/');
	if ($hasSlash) {
		$url = substr($domainURL, 0, $hasSlash);
		$pageURL = substr($domainURL, $hasSlash);
		$domainURL = $url;
		if ($pageURL == '/') $pageURL = '';
	}

  // Build new data
	$returnData = array();
	$returnData['domain_url'] = $domainURL;
	if ($pageURL!='') $returnData['page_url'] = $pageURL;
	return $returnData;

}

```
