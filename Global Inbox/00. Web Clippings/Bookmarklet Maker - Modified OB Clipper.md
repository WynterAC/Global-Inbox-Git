author:: Caio Rodrigues. 
source:: [Bookmarklet Maker](https://caiorss.github.io/bookmarklet-maker/)
clipped:: [[2024-07-29]]
published:: 

#webclippings #to_read


> [!NOTE] Source
[**Asseel-Naji](https://gist.github.com/Asseel-Naji)** commented [on Sep 25, 2021](https://gist.github.com/kepano/90c05f162c37cf730abb8ff027987ca3?permalink_comment_id=3905251#gistcomment-3905251)

A small fork that prompts the user for folder and extra tags : [Asseel-Naji/604de43495538e04f0448da394bc456a](https://gist.github.com/Asseel-Naji/604de43495538e04f0448da394bc456a)

[![@Asseel-Naji](https://avatars.githubusercontent.com/u/60823794?s=80&v=4)](https://gist.github.com/Asseel-Naji)

### 

**[

## Javescript
```
javascript:(function()%7Bjavascript%3A%20Promise.all(%5Bimport('https%3A%2F%2Funpkg.com%2Fturndown%406.0.0%3Fmodule')%2C%20import('https%3A%2F%2Funpkg.com%2F%40tehshrike%2Freadability%400.2.0')%2C%20%5D).then(async%20(%5B%7B%0A%20%20%20%20default%3A%20Turndown%0A%7D%2C%20%7B%0A%20%20%20%20default%3A%20Readability%0A%7D%5D)%20%3D%3E%20%7B%0A%0A%20%20%2F*%20Optional%20vault%20name%20*%2F%0A%20%20const%20vault%20%3D%20%22Global%20Inbox%22%3B%0A%0A%20%20%2F*%20Optional%20folder%20name%20such%20as%20%22Clippings%2F%22%20*%2F%0A%20%20%2F*%20const%20folder%20%3D%20%22Resources%2F0_INBOX%2F%22%3B%20*%2F%0A%20%20const%20folder%20%3D%20prompt(%22Folder%3A%22%2C%20%2200.%20Web%20Clippings%2F%22)%3B%0A%0A%20%20%2F*%20Optional%20tags%20%20*%2F%0A%20%20let%20baseTag%20%3D%20%22%23webclippings%20%22%3B%0A%20%20let%20extraTags%20%3D%20prompt(%22additional%20tags%3A%22%2C%20%22%23to_read%22)%3B%0A%20%20const%20tags%20%3D%20baseTag%20%2B%20extraTags%3B%0A%0A%20%20%0A%0A%0A%20%20function%20getSelectionHtml()%20%7B%0A%20%20%20%20var%20html%20%3D%20%22%22%3B%0A%20%20%20%20if%20(typeof%20window.getSelection%20!%3D%20%22undefined%22)%20%7B%0A%20%20%20%20%20%20%20%20var%20sel%20%3D%20window.getSelection()%3B%0A%20%20%20%20%20%20%20%20if%20(sel.rangeCount)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20container%20%3D%20document.createElement(%22div%22)%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20for%20(var%20i%20%3D%200%2C%20len%20%3D%20sel.rangeCount%3B%20i%20%3C%20len%3B%20%2B%2Bi)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20container.appendChild(sel.getRangeAt(i).cloneContents())%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20html%20%3D%20container.innerHTML%3B%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%20else%20if%20(typeof%20document.selection%20!%3D%20%22undefined%22)%20%7B%0A%20%20%20%20%20%20%20%20if%20(document.selection.type%20%3D%3D%20%22Text%22)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20html%20%3D%20document.selection.createRange().htmlText%3B%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%20%20return%20html%3B%0A%20%20%7D%0A%0A%20%20const%20selection%20%3D%20getSelectionHtml()%3B%0A%0A%20%20let%20%7B%0A%20%20%20%20%20%20title%2C%0A%20%20%20%20%20%20byline%2C%0A%20%20%20%20%20%20content%0A%20%20%7D%20%3D%20new%20Readability(document.cloneNode(true)).parse()%3B%0A%0A%20%20function%20getFileName(fileName)%20%7B%0A%20%20%20%20var%20userAgent%20%3D%20window.navigator.userAgent%2C%0A%20%20%20%20%20%20%20%20platform%20%3D%20window.navigator.platform%2C%0A%20%20%20%20%20%20%20%20windowsPlatforms%20%3D%20%5B'Win32'%2C%20'Win64'%2C%20'Windows'%2C%20'WinCE'%5D%3B%0A%0A%20%20%20%20if%20(windowsPlatforms.indexOf(platform)%20!%3D%3D%20-1)%20%7B%0A%20%20%20%20%20%20fileName%20%3D%20fileName.replace('%3A'%2C%20'').replace(%2F%5B%2F%5C%5C%3F%25*%7C%22%3C%3E%5D%2Fg%2C%20'-')%3B%0A%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20fileName%20%3D%20fileName.replace('%3A'%2C%20'').replace(%2F%5C%2F%2Fg%2C%20'-').replace(%2F%5C%5C%2Fg%2C%20'-')%3B%0A%20%20%20%20%7D%0A%20%20%20%20return%20fileName%3B%0A%20%20%7D%0A%20%20let%20fileName%20%3D%20prompt(%22File%20Name%22%2C%20getFileName(title))%3B%0A%0A%20%20if%20(selection)%20%7B%0A%20%20%20%20%20%20var%20markdownify%20%3D%20selection%3B%0A%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20var%20markdownify%20%3D%20content%3B%0A%20%20%7D%0A%0A%20%20if%20(vault)%20%7B%0A%20%20%20%20%20%20var%20vaultName%20%3D%20'%26vault%3D'%20%2B%20encodeURIComponent(%60%24%7Bvault%7D%60)%3B%0A%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20var%20vaultName%20%3D%20''%3B%0A%20%20%7D%0A%0A%20%20const%20markdownBody%20%3D%20new%20Turndown(%7B%0A%20%20%20%20%20%20headingStyle%3A%20'atx'%2C%0A%20%20%20%20%20%20hr%3A%20'---'%2C%0A%20%20%20%20%20%20bulletListMarker%3A%20'-'%2C%0A%20%20%20%20%20%20codeBlockStyle%3A%20'fenced'%2C%0A%20%20%20%20%20%20emDelimiter%3A%20'*'%2C%0A%20%20%7D).turndown(markdownify)%3B%0A%0A%20%20var%20date%20%3D%20new%20Date()%3B%0A%0A%20%20function%20convertDate(date)%20%7B%0A%20%20%20%20var%20yyyy%20%3D%20date.getFullYear().toString()%3B%0A%20%20%20%20var%20mm%20%3D%20(date.getMonth()%2B1).toString()%3B%0A%20%20%20%20var%20dd%20%20%3D%20date.getDate().toString()%3B%0A%20%20%20%20var%20mmChars%20%3D%20mm.split('')%3B%0A%20%20%20%20var%20ddChars%20%3D%20dd.split('')%3B%0A%20%20%20%20return%20yyyy%20%2B%20'-'%20%2B%20(mmChars%5B1%5D%3Fmm%3A%220%22%2BmmChars%5B0%5D)%20%2B%20'-'%20%2B%20(ddChars%5B1%5D%3Fdd%3A%220%22%2BddChars%5B0%5D)%3B%0A%20%20%7D%0A%0A%20%20const%20today%20%3D%20convertDate(date)%3B%0A%0A%20%20const%20fileContent%20%3D%20%0A%20%20%20%20%20%20%22author%3A%3A%20%22%20%2B%20byline%20%2B%20%22%5Cn%22%0A%20%20%20%20%20%20%2B%20%22source%3A%3A%20%5B%22%20%2B%20title%20%2B%20%22%5D(%22%20%2B%20document.URL%20%2B%20%22)%5Cn%22%0A%20%20%20%20%20%20%2B%20%22clipped%3A%3A%20%5B%5B%22%20%2B%20today%20%2B%20%22%5D%5D%5Cn%22%0A%20%20%20%20%20%20%2B%20%22published%3A%3A%20%5Cn%5Cn%22%20%0A%20%20%20%20%20%20%2B%20tags%20%2B%20%22%5Cn%5Cn%22%0A%20%20%20%20%20%20%2B%20markdownBody%20%3B%0A%20%20%0A%20%20document.location.href%20%3D%20%22obsidian%3A%2F%2Fnew%3F%22%0A%20%20%20%20%2B%20%22file%3D%22%20%2B%20encodeURIComponent(folder%20%2B%20fileName)%0A%20%20%20%20%2B%20%22%26content%3D%22%20%2B%20encodeURIComponent(fileContent)%0A%20%20%20%20%2B%20vaultName%20%3B%0A%7D)%7D)()%3B
```

## HTML Code
```
<a href="javascript:(function()%7Bjavascript%3A%20Promise.all(%5Bimport('https%3A%2F%2Funpkg.com%2Fturndown%406.0.0%3Fmodule')%2C%20import('https%3A%2F%2Funpkg.com%2F%40tehshrike%2Freadability%400.2.0')%2C%20%5D).then(async%20(%5B%7B%0A%20%20%20%20default%3A%20Turndown%0A%7D%2C%20%7B%0A%20%20%20%20default%3A%20Readability%0A%7D%5D)%20%3D%3E%20%7B%0A%0A%20%20%2F*%20Optional%20vault%20name%20*%2F%0A%20%20const%20vault%20%3D%20%22Global%20Inbox%22%3B%0A%0A%20%20%2F*%20Optional%20folder%20name%20such%20as%20%22Clippings%2F%22%20*%2F%0A%20%20%2F*%20const%20folder%20%3D%20%22Resources%2F0_INBOX%2F%22%3B%20*%2F%0A%20%20const%20folder%20%3D%20prompt(%22Folder%3A%22%2C%20%2200.%20Web%20Clippings%2F%22)%3B%0A%0A%20%20%2F*%20Optional%20tags%20%20*%2F%0A%20%20let%20baseTag%20%3D%20%22%23webclippings%20%22%3B%0A%20%20let%20extraTags%20%3D%20prompt(%22additional%20tags%3A%22%2C%20%22%23to_read%22)%3B%0A%20%20const%20tags%20%3D%20baseTag%20%2B%20extraTags%3B%0A%0A%20%20%0A%0A%0A%20%20function%20getSelectionHtml()%20%7B%0A%20%20%20%20var%20html%20%3D%20%22%22%3B%0A%20%20%20%20if%20(typeof%20window.getSelection%20!%3D%20%22undefined%22)%20%7B%0A%20%20%20%20%20%20%20%20var%20sel%20%3D%20window.getSelection()%3B%0A%20%20%20%20%20%20%20%20if%20(sel.rangeCount)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20container%20%3D%20document.createElement(%22div%22)%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20for%20(var%20i%20%3D%200%2C%20len%20%3D%20sel.rangeCount%3B%20i%20%3C%20len%3B%20%2B%2Bi)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20container.appendChild(sel.getRangeAt(i).cloneContents())%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20html%20%3D%20container.innerHTML%3B%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%20else%20if%20(typeof%20document.selection%20!%3D%20%22undefined%22)%20%7B%0A%20%20%20%20%20%20%20%20if%20(document.selection.type%20%3D%3D%20%22Text%22)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20html%20%3D%20document.selection.createRange().htmlText%3B%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%20%20return%20html%3B%0A%20%20%7D%0A%0A%20%20const%20selection%20%3D%20getSelectionHtml()%3B%0A%0A%20%20let%20%7B%0A%20%20%20%20%20%20title%2C%0A%20%20%20%20%20%20byline%2C%0A%20%20%20%20%20%20content%0A%20%20%7D%20%3D%20new%20Readability(document.cloneNode(true)).parse()%3B%0A%0A%20%20function%20getFileName(fileName)%20%7B%0A%20%20%20%20var%20userAgent%20%3D%20window.navigator.userAgent%2C%0A%20%20%20%20%20%20%20%20platform%20%3D%20window.navigator.platform%2C%0A%20%20%20%20%20%20%20%20windowsPlatforms%20%3D%20%5B'Win32'%2C%20'Win64'%2C%20'Windows'%2C%20'WinCE'%5D%3B%0A%0A%20%20%20%20if%20(windowsPlatforms.indexOf(platform)%20!%3D%3D%20-1)%20%7B%0A%20%20%20%20%20%20fileName%20%3D%20fileName.replace('%3A'%2C%20'').replace(%2F%5B%2F%5C%5C%3F%25*%7C%22%3C%3E%5D%2Fg%2C%20'-')%3B%0A%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20fileName%20%3D%20fileName.replace('%3A'%2C%20'').replace(%2F%5C%2F%2Fg%2C%20'-').replace(%2F%5C%5C%2Fg%2C%20'-')%3B%0A%20%20%20%20%7D%0A%20%20%20%20return%20fileName%3B%0A%20%20%7D%0A%20%20let%20fileName%20%3D%20prompt(%22File%20Name%22%2C%20getFileName(title))%3B%0A%0A%20%20if%20(selection)%20%7B%0A%20%20%20%20%20%20var%20markdownify%20%3D%20selection%3B%0A%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20var%20markdownify%20%3D%20content%3B%0A%20%20%7D%0A%0A%20%20if%20(vault)%20%7B%0A%20%20%20%20%20%20var%20vaultName%20%3D%20'%26vault%3D'%20%2B%20encodeURIComponent(%60%24%7Bvault%7D%60)%3B%0A%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20var%20vaultName%20%3D%20''%3B%0A%20%20%7D%0A%0A%20%20const%20markdownBody%20%3D%20new%20Turndown(%7B%0A%20%20%20%20%20%20headingStyle%3A%20'atx'%2C%0A%20%20%20%20%20%20hr%3A%20'---'%2C%0A%20%20%20%20%20%20bulletListMarker%3A%20'-'%2C%0A%20%20%20%20%20%20codeBlockStyle%3A%20'fenced'%2C%0A%20%20%20%20%20%20emDelimiter%3A%20'*'%2C%0A%20%20%7D).turndown(markdownify)%3B%0A%0A%20%20var%20date%20%3D%20new%20Date()%3B%0A%0A%20%20function%20convertDate(date)%20%7B%0A%20%20%20%20var%20yyyy%20%3D%20date.getFullYear().toString()%3B%0A%20%20%20%20var%20mm%20%3D%20(date.getMonth()%2B1).toString()%3B%0A%20%20%20%20var%20dd%20%20%3D%20date.getDate().toString()%3B%0A%20%20%20%20var%20mmChars%20%3D%20mm.split('')%3B%0A%20%20%20%20var%20ddChars%20%3D%20dd.split('')%3B%0A%20%20%20%20return%20yyyy%20%2B%20'-'%20%2B%20(mmChars%5B1%5D%3Fmm%3A%220%22%2BmmChars%5B0%5D)%20%2B%20'-'%20%2B%20(ddChars%5B1%5D%3Fdd%3A%220%22%2BddChars%5B0%5D)%3B%0A%20%20%7D%0A%0A%20%20const%20today%20%3D%20convertDate(date)%3B%0A%0A%20%20const%20fileContent%20%3D%20%0A%20%20%20%20%20%20%22author%3A%3A%20%22%20%2B%20byline%20%2B%20%22%5Cn%22%0A%20%20%20%20%20%20%2B%20%22source%3A%3A%20%5B%22%20%2B%20title%20%2B%20%22%5D(%22%20%2B%20document.URL%20%2B%20%22)%5Cn%22%0A%20%20%20%20%20%20%2B%20%22clipped%3A%3A%20%5B%5B%22%20%2B%20today%20%2B%20%22%5D%5D%5Cn%22%0A%20%20%20%20%20%20%2B%20%22published%3A%3A%20%5Cn%5Cn%22%20%0A%20%20%20%20%20%20%2B%20tags%20%2B%20%22%5Cn%5Cn%22%0A%20%20%20%20%20%20%2B%20markdownBody%20%3B%0A%20%20%0A%20%20document.location.href%20%3D%20%22obsidian%3A%2F%2Fnew%3F%22%0A%20%20%20%20%2B%20%22file%3D%22%20%2B%20encodeURIComponent(folder%20%2B%20fileName)%0A%20%20%20%20%2B%20%22%26content%3D%22%20%2B%20encodeURIComponent(fileContent)%0A%20%20%20%20%2B%20vaultName%20%3B%0A%7D)%7D)()%3B">Clip to Global Inbox</a>
```
## Examples:

Sumbmit current URL to Reddit:

Sumbmit to Reddit

var url = document.URL ;
var title = document.title ;

window.location.href = "https://www.reddit.com/r/"
                        + prompt("Subreddit: ", "")
                        + "/submit?title="
                        + title + "&url="
                        + url ;  
      

Submit current URL to Reddit in a new tab

Submit to reddit in a new tab

var defaultSub = "dummy"
var subreddit = prompt("Enter the subreddit", defaultSub)
var baseUrl =  'https://www.reddit.com/r/' + subreddit + 'submit?title=';
window.open(baseUrl + document.title + '&url=' + document.URL, '\_blank') 
      

Generate org-mode hyperlink

Org-mode hyperlink

var md = "\[\[" + document.URL + "\]\[" + document.title + "\]\]" ;
prompt("Enter Ctrl+C to copy this org-mode hyperlink. :", md);
      

Clear google search URLs to allow easy copy URLs without messing it.

Clear google URL

var $s = function (selector){
    return Array.from(document.querySelectorAll(selector));
};

$s(".rc a").forEach(e => e.onmousedown = null);
      

Inject css style sheet from a given URL into current page.

inject css

var link = document.createElement("link");
link.href = prompt("css url", "");
link.type = "text/css";
link.rel = "stylesheet";
document.getElementsByTagName("head")\[0\].appendChild(link);
      

Open a prompt showing Google driver URL to current document. Useful to create short URL in services like tiny URL and view document in Tablets or Smartphones.

Copy Gdriver URL

prompt("Google driver URL:", "https://drive.google.com/viewerng/viewer?url=" + document.URL);
      

Past some URL and open it in Google driver.

open Gdriver prompt

var baseUrl = "https://drive.google.com/viewerng/viewer?url=";
var url = prompt("Paste Url");
if (url != null){
    window.open(baseUrl + url);
}
 

Open page that doesn't exist anymore in Web Archive

open in WebArchive

var baseUrl = "https://web.archive.org/web/\*/"
var urlmod  = document.URL
window.location.href = baseUrl + urlmod


`