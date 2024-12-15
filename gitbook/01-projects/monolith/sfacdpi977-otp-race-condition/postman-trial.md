## Challenge API Call
Request
```
curl --location 'https://www.wayfair.com/auth/v2/email/grant' \
--header 'Accept: application/json' \
--header 'Accept-Language: en-GB,en;q=0.5' \
--header 'Connection: keep-alive' \
--header 'Content-Type: application/json' \
--header 'Cookie: CSNUtId=45a62166-95ce-486b-b8f1-091ad77fd5d3; _wf_fs_sample_user=false; i18nPrefs=lang%3Den-US; postalCode=67346; pxcts=88b4b21c-08a7-11ef-8c97-41e584322059; TopNavCSSCachedByBrowser=true; featureDetect={"isTouch":false,"hasMQ":true,"deviceWidth":1352,"deviceHeight":763,"devicePixelRatio":2}; presentation_layer=global.monolith; CSN=g_countryCode%3DUS%26g_zip%3D67346%26CLVW%3D861; ExCSNUtId=45a62166-95ce-486b-b8f1-091ad77fd5d3; WFCS=CS2; AppInterstitial=visit_date_1%3D2024-10-15%26visit_date_2%3D2024-10-16%26visit_date_3%3D2024-10-17; canary=0; CSNBrief=DRF=dsm1&refid=EML_48500&shouldShowTrafficLight=false; serverUAInfo=%7B%22browser%22%3A%22Google%20Chrome%22%2C%22browserVersion%22%3A130%2C%22OS%22%3A%22Mac%20OS%20X%22%2C%22OSVersion%22%3A%22%22%2C%22isMobile%22%3Afalse%2C%22isTablet%22%3Afalse%2C%22isTouch%22%3Afalse%7D; WFDC=IAD; CSN_CSRF=d4ac702d07ab46ce1147e34b587d7b4ece39dada2ece8babcffe38cd5e6a2149; hideGoogleYolo=1; vid=0af402a4-673a-fb72-7c3b-96eb5c438702; SFSID=e8a26ad7b2f4d6cd55e9505aa97a66da; coreGatewayOptOut=modal; CSNPersist=page_of_visit%3D429%26latestRefid%3DEML_48500; CSNID=1A774F47-C986-4DC4-8C97-A2687165D42C; CSNID=1A774F47-C986-4DC4-8C97-A2687165D42C; canary=0; i18nPrefs=lang%3Den-US; serverUAInfo=%7B%22browser%22%3A%22Google%20Chrome%22%2C%22browserVersion%22%3A130%2C%22OS%22%3A%22Mac%20OS%20X%22%2C%22OSVersion%22%3A%22%22%2C%22isMobile%22%3Afalse%2C%22isTablet%22%3Afalse%2C%22isTouch%22%3Afalse%7D; vid=0af402a4-673a-fb72-7c3b-96eb5c438702' \
--header 'Origin: https://www.wayfair.com' \
--header 'Referer: https://www.wayfair.com/v/account/authentication/login?url=https%3A%2F%2Fwww.wayfair.com%2F%3Flogout%3D1731918706&context=header_wayfair_my_account_menu' \
--header 'Sec-Fetch-Dest: empty' \
--header 'Sec-Fetch-Mode: cors' \
--header 'Sec-Fetch-Site: same-origin' \
--header 'Sec-GPC: 1' \
--header 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0.0.0 Safari/537.36' \
--header 'X-AUTH-CALLER-CONTEXT: auth_main_page_context' \
--header 'X-Parent-TXID: CvQCpGc6+3t8O5brXEPrAg==' \
--header 'X-Requested-With: XMLHttpRequest' \
--header 'sec-ch-ua: "Chromium";v="130", "Brave";v="130", "Not?A_Brand";v="99"' \
--header 'sec-ch-ua-mobile: ?0' \
--header 'sec-ch-ua-platform: "macOS"' \
--data-raw '{"email":"lekhavadivu@gmail.com","password":"563786"}'
```

Response initially
```
{
	"code": 401,
	"key": "invalid_otp",
	"message": "Code entered doesn't match the one we sent. Check your code and try again."
}
```

Response after 6 attempts
```
{
	"code": 401,
	"key": "expired_otp",
	"message": "Code has expired. Try having a new one sent."
}
```

Response after 10 attempts
```
{
	"code": 420,
	"key": "rate_limit_allowed_attempts_exceeded",
	"message": "Please try again later. You've exceeded the allowed number of attempts."
}
```
