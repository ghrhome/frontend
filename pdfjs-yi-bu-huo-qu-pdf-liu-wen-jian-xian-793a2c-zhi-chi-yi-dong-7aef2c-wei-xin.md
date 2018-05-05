# pdf.js 异步获取pdf流文件显示,支持移动端,微信

> 公司最近在有一个需求就是pdf要现在预览，所以就找到了pdf.js的插件，开始用了它的viewr.js，这个是美化了预览页面，但是在移动端safari会出问题，所以只能放弃，自己写喽

```
var param = function(name) { //一个获取url中参数的方法
    var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)"); //构造一个含有目标参数的正则表达式对象
    var r = window.location.search.substr(1).match(reg); //匹配目标参数
    if (r != null) return unescape(r[2]);
    return null; //返回参数值
};
var PDFData = "";
var currPage = 1; //当前页数从1开始
var numPages = 0;
var thePDF = null;
$.ajax({
    type: "post",
    mimeType: 'text/plain; charset=x-user-defined',
    url: param("pdfUrl"),
    //url中要有 pdfUrl 参数和值，值为pdf流地址
    success: function(data) {
        if (data) {
            PDFData = data;
            var rawLength = PDFData.length;
            //转换成pdf.js能直接解析的Uint8Array类型,见pdf.js-4068
            var array = new Uint8Array(new ArrayBuffer(rawLength));
            for (i = 0; i < rawLength; i++) {
                array[i] = PDFData.charCodeAt(i) & 0xff;
            }
            PDFJS.getDocument(array).then(function(pdf) {
                require('module/common/dialog').hideLoading();
                //将pdf对象赋值到全局变量，能够在其他方法中使用
                thePDF = pdf;
                //获取一共有多少页
                numPages = pdf.numPages;
                //从第一页开始
                pdf.getPage(1).then(handlePages);
            });
        } else {
            console.log("pdf请求失败")
        }
    }
});
function handlePages(page) {
    //获取全尺寸pdf
    var viewport = page.getViewport(2);
    var canvas = document.createElement("canvas");
    var canvasCon = document.createElement("div");
    canvas.id = "canvas_" + currPage;
    canvasCon.id = "canvasCon_" + currPage;
    canvasCon.className = "canvasCon";
    var winRatio = ($(window).width() / viewport.width) * 0.9;
    $(canvas).css({
        "transform": "scale(" + winRatio + ")",
        "webkitTransform": "scale(" + winRatio + ")",
        "left": $(window).width() * 0.05
    });
    $(".canvasCon").css({
        'height': viewport.height * winRatio
    });
    var context = canvas.getContext('2d');
    canvas.height = viewport.height;
    canvas.width = viewport.width;
    //在canvas上绘制
    page.render({
        canvasContext: context,
        viewport: viewport
    });
    //在页面中插入画布
    document.body.appendChild(canvasCon);
    document.getElementById("canvasCon_" + currPage).appendChild(canvas);
    //开始下一页到绘制
    currPage++;
    if (thePDF !== null && currPage <= numPages) {
        thePDF.getPage(currPage).then(handlePages);
    }
}
```



