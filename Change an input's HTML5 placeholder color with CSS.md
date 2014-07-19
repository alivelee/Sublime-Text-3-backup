Chrome supports the placeholder attribute on `input[type=text]` elements (others probably do too).
But the following CSS doesn't do diddly squat to the placeholder's value:
```
<style>     
input[placeholder], [placeholder], *[placeholder]     {         color:red !important;     } 
</style> 
<input type="text" placeholder="Value" />
```
## Solution 1
WebKit only:
`
input::-webkit-input-placeholder {}
`
Mozilla (Firefox 4) now supports :
`-moz-placeholder: `
Note that Mozilla is using a pseudo class, not a pseudo element, therefore it has to be just one double colon, not two. `input:-moz-placeholder {}` 
You have to use two rules, because user agents are required to ignore a rule with an unknown selector. Since WebKit doesn?t know the proprietary Mozilla selector and vice versa, you have to write:
````
input::-webkit-input-placeholder {    
	color:    #999; } 
input:-moz-placeholder {     
	color:    #999; }
```
To catch input and textarea just drop the element selector:
```language
```
::-webkit-input-placeholder {     
	color:    #999; } 
:-moz-placeholder {     
    color:    #999; }
```
==*the -ms-input-placeholder is for Internet Explorer and works only for IE10*==
== if you want both colorize placeholder on Chrome and Firefox, don't use the following merged rules (missing :) :==
```
input::-webkit-input-placeholder, 
input:-moz-placeholder {     
	color:red; }
```
But instead : 
```
input::-webkit-input-placeholder, 
input::-moz-placeholder {    
	color:red; }
```


Stack Overflow - html5 (423) - Jul 2012 (Kindle Locations 12853-12854). 



