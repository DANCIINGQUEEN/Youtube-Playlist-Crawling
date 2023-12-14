# Youtube-Playlist-Crawling
```javascript
const q=d=>{
    let results = [];
    let videoRows = document.querySelectorAll('ytcp-video-row');
    videoRows.forEach((row) => {
        let date = row.querySelector('.tablecell-date').innerText.trim().split`\n`[0];
        if (date === d) {
            let titleElement = row.querySelector('#video-title');
            let title = titleElement ? titleElement.innerText.trim() : "No title";
            let link = titleElement ? titleElement.href.split`/`[4] : "No link";
            link=`https://www.youtube.com/watch?v=`+link
            results.push({ title: title, link: link });
        }
    });
    console.log(JSON.stringify(results));
}
q('2023. 12. 11.')
```
