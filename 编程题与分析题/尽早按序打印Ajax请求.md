/**
 * 接受一个URL数组做参数，并行请求，尽可能快的按照顺序打印内容
 */

[https://lxzjj.github.io/2017/10/29/%E4%B8%80%E6%AC%A1js%E5%B9%B6%E8%A1%8C%E4%B8%B2%E8%A1%8C%E7%9A%84%E6%80%9D%E8%80%83/](https://lxzjj.github.io/2017/10/29/%E4%B8%80%E6%AC%A1js%E5%B9%B6%E8%A1%8C%E4%B8%B2%E8%A1%8C%E7%9A%84%E6%80%9D%E8%80%83/)

```js
const urlList = [1,2,3,4,5]


loadData(urlList)

function fetchData(url, succCallback) {
  setTimeout(() => {
    succCallback('ok: ' + url);
  }, (Math.random() * 5 * 1000) >> 0);
}

function loadData(urlList) {
  let resArr = [],
    doneId = 0;
  for (let i = 0; i < urlList.length; i++) {
    fetchData(urlList[i], res => {
      console.log(`${i + 1} has done`)
      resArr[i] = res;
      outPutRes(resArr);
    });
  }
  function outPutRes(resArr) {
    for (let i = doneId; i < resArr.length; i++) {
      if (resArr[i]) {
        console.log(resArr[i]);
        doneId++;
      } else {
        break;
      }
    }
  }
}
```


