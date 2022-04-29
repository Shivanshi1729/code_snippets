# Code Snippets

- download canvas elements as images `js`

```js
function downloadCanvasAsImage(name){
    let canvasImage = document.getElementById('pdfCanvas').toDataURL('image/png');
    let xhr = new XMLHttpRequest();
    xhr.responseType = 'blob';
    xhr.onload = function () {
        let a = document.createElement('a');
        a.href = window.URL.createObjectURL(xhr.response);
        a.download =  name + '.png';
        a.style.display = 'none';
        document.body.appendChild(a);
        a.click();
        a.remove();
    };
    xhr.open('GET', canvasImage);
    xhr.send();
}
function sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}
async function downloadIt(){
    x = parseInt(document.getElementById('page_count').textContent)
    for(let i=0;i<x;i++){
        downloadCanvasAsImage('se' + i.toString());
        document.getElementById('next').click();
        await sleep(500);
    }
}
downloadIt()
```

- download slideshare slides `js`

```js
reg = /https:\/\/image\.slidesharecdn\.com\/[^ ]* 1024w/g
a = document.body.innerHTML.match(reg)
b = []
for(i=0;i<a.length();i++){
    b.push(a[i].split(' ')[0])
}
```