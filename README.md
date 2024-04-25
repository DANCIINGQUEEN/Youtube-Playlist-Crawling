# Youtube-Playlist-Crawling

### Crawling Code V2
```javascript
const q = d => {
    let results = [];
    let videoRows = document.querySelectorAll('ytcp-video-row');
    videoRows.forEach(row => {
        let date = row.querySelector('.tablecell-date').innerText.trim().split('\n')[0];
        if (date === d) {
            let titleElement = row.querySelector('#video-title');
            let title = titleElement ? titleElement.innerText.trim() : "No title";
            let link = titleElement ? titleElement.href.split('/')[4] : "No link";
            link = `https://www.youtube.com/watch?v=${link}`;
            results.push({ title, link });
        }
    });
    console.log("플레이리스트 개수 : ",results.length)
    let resultString = JSON.stringify(results)
    resultString=resultString.slice(1,resultString.length-1)

    let textArea = document.createElement('textarea');
    textArea.style.position = 'fixed'; 
    textArea.style.left = '0';
    textArea.style.top = '0';
    textArea.style.opacity = '0';
    textArea.value = resultString;
    document.body.appendChild(textArea);
    textArea.focus();
    textArea.select();
    try {
        let successful = document.execCommand('copy');
        let msg = successful ? 'Successful copy' : 'Copy failed';
        console.log(msg);
    } catch (err) {
        console.error('Error copying text: ', err);
    }
    document.body.removeChild(textArea);
};

q('2024. 4. 25.');
```

### Crawling Code V1
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
youtube스튜디오 채널 콘텐츠 창에서 개발자 모드를 켜고 콘솔에 입력
