### base64格式的pdf预览

在项目中我们会遇到预览pdf的需求，一般的需求都是要求能直接打开，一般后端回传pdf的格式有两种，一种是直接传pdf的url地址，还有一种就是直接传回来base64格式的pdf。怎么知道是base64格式的pdf呢，一般的格式都是下面这样子的

```js
JVBERi0xLjQKJeLjz9MKMiAwIG9iaiA8PC9MZW5ndGggNzUzL0ZpbHRlci9GbGF0ZURlY29kZT4+c3RyZWFtCnicrZY/TxRBGIcXEy220d5mQgUF47zzf7EzUYyFkeMSTSSnggfGSAGKxMrSGDDQSExMSCz8EnZ+DS2s/AAmRhIbfOd218DtvHO3BMgdl/3NPvvsb2bnWM+vdXNlmReWdR/ngs2A9eHT9W4+n68PXpLdwmAuF9ywrdx7rpjTlknDJZOCbfTzhSoDUPg3hNpw5YZT47l3g9gabtRQLKXmGujYF7zQZKyM4bqEgwEuh/NSW/pSG3xEG8NSeyittDEuL3wyrrWpuNIm4lob40r7ZF5qg0hoY5jSxjilTcWVNhHX2hjT2raQtHYIE9ohTmiTcalNxZV2iBPaTie0MUxpY5zSpuJKm4hrbYwT2sYmtI1Nahub1KbiSpuIa21jU9oq8UiGMKWtko8kGVfaRFxrq8YjOR82S2ACf4HJcC5zHnfLtfzKDWCAO+gKbpbdjQBS+IOwqUcX3359Nvfw6nT3KW6imAEexc31GKkQvGDOwH+QOAZSNai3u3CYgABYDmNg7n9aenX7S/deCuWAWz0a1bnc+9v/8/53AiWV4+BGo5Y/9+0IlBKSj0EK9zeCpAG4GLOqMH2pqcN1KJlTEpdCxSoCaiqDcNZQr1JyW8RG799cuvThW+QMC1xBlC8zkUHmsxl8l/guM50xPOayWfxUNFlSWu7NGbEKyfHxOBNWVSHoJipWoRus8ubo59urv+gCY/TTFtiC5ZGlMk8X2JoV8VIWt8poJ9uH/TdrH8XE67t3Fqf3z2/97L1892P3+9Hiys7kzuTRBDUZtrANLUVORmT04ILkbMTwre+6mo02rAJZkFjObVmYNVla+DAbEdbe5vpq5+DFBXGO7N35hoAm95HI6FUIE04XH+GfuvgWrGLAiqyguvizYGlwg+KbrL3NzkGidCsaFzf0Ym+OTu48MXr7mqrKW7MSa70lS0fXOv6TJqKdbB8+6DxZTpSum98cll7pzdEjvjFj/Na3V9c+Ngvw6Cy+Is9sXfupWf8AJ3cIwAplbmRzdHJlYW0KZW5kb2JqCjQgMCBvYmo8PC9QYXJlbnQgMyAwIFIvQ29udGVudHMgMiAwIFIvVHlwZS9QYWdlL1Jlc291cmNlczw8L1Byb2NTZXQgWy9QREYgL1RleHQgL0ltYWdlQiAvSW1hZ2VDIC9JbWFnZUldL0ZvbnQ8PC9GMSAxIDAgUj4+Pj4vTWVkaWFCb3hbMCAwIDU5NSA4NDJdPj4KZW5kb2JqCjUgMCBvYmo8PC9Gb250QkJveCBbLTI1IC0yNTQgMTAwMCA4ODBdL0NhcEhlaWdodCA4ODAvU3R5bGU8PC9QYW5vc2UoAQUCAgQAAAAAAAAAKT4+L1R5cGUvRm9udERlc2NyaXB0b3IvU3RlbVYgOTMvRGVzY2VudCAtMTIwL0ZsYWdzIDYvRm9udE5hbWUvU1RTb25nLUxpZ2h0L0FzY2VudCA4ODAvSXRhbGljQW5nbGUgMD4+CmVuZG9iago2IDAgb2JqPDwvQmFzZUZvbnQvU1RTb25nLUxpZ2h0L0NJRFN5c3RlbUluZm88PC9PcmRlcmluZyhHQjEpL1JlZ2lzdHJ5KEFkb2JlKS9TdXBwbGVtZW50IDQ+Pi9XIFsxWzIwN10xNFszNzVdMTcgMjYgNDYyIDI3WzIzOF1dL1R5cGUvRm9udC9TdWJ0eXBlL0NJREZvbnRUeXBlMC9Gb250RGVzY3JpcHRvciA1IDAgUi9EVyAxMDAwPj4KZW5kb2JqCjEgMCBvYmo8PC9EZXNjZW5kYW50Rm9udHNbNiAwIFJdL0Jhc2VGb250L1NUU29uZy1MaWdodC1VbmlHQi1VQ1MyLUgvVHlwZS9Gb250L0VuY29kaW5nL1VuaUdCLVVDUzItSC9TdWJ0eXBlL1R5cGUwPj4KZW5kb2JqCjMgMCBvYmo8PC9UeXBlL1BhZ2VzL0NvdW50IDEvS2lkc1s0IDAgUl0+PgplbmRvYmoKNyAwIG9iajw8L1R5cGUvQ2F0YWxvZy9QYWdlcyAzIDAgUj4+CmVuZG9iago4IDAgb2JqPDwvUHJvZHVjZXIoaVRleHQgMi4wLjcgXChieSBsb3dhZ2llLmNvbVwpKS9Nb2REYXRlKEQ6MjAyMTA2MzAwOTU1NDkrMDgnMDAnKS9DcmVhdGlvbkRhdGUoRDoyMDIxMDYzMDA5NTU0OSswOCcwMCcpPj4KZW5kb2JqCnhyZWYKMCA5CjAwMDAwMDAwMDAgNjU1MzUgZiAKMDAwMDAwMTM3OCAwMDAwMCBuIAowMDAwMDAwMDE1IDAwMDAwIG4gCjAwMDAwMDE1MDEgMDAwMDAgbiAKMDAwMDAwMDgzNSAwMDAwMCBuIAowMDAwMDAwOTkxIDAwMDAwIG4gCjAwMDAwMDExODEgMDAwMDAgbiAKMDAwMDAwMTU1MSAwMDAwMCBuIAowMDAwMDAxNTk1IDAwMDAwIG4gCnRyYWlsZXIKPDwvUm9vdCA3IDAgUi9JRCBbPDk5MGVjNjU1ZDZhODIzODRlYWFlODBkY2FhNzRiNjNiPjwyNDRjNjQ1Yzc5NWRkZWQ5MmI1NTM2MzViNGE3NmY2Zj5dL0luZm8gOCAwIFIvU2l6ZSA5Pj4Kc3RhcnR4cmVmCjE3MjYKJSVFT0YK
```



先看看要实现的需求：

打开前：

![pdf1](C:\Users\Administrator\Desktop\pdf1.jpg)

打开后：

![pdf2](C:\Users\Administrator\Desktop\pdf2.jpg)

遇到这种格式的pdf怎么打开呢？

1.直接打开，因为现在浏览器上都可以直接打开pdf，这种方式最方便了，但是有个问题就是，在ie上你点击预览的时候，ie浏览器会让你下载，而不是直接打开，所以，如果你们项目可以直接ie不是直接打开的话，那么最好就是用这种方式了。下面放代码怎么打开：

```js
viewPdf (content) {
      if (!content) {
        console.log(content)
        this.$message.error('暂无意见')
        return
      }
      const blob = this.base64ToBlob(content)
      if (window.navigator && window.navigator.msSaveOrOpenBlob) {
        window.navigator.msSaveOrOpenBlob(blob)
      } else {
        const fileURL = URL.createObjectURL(blob)
        window.open(fileURL)
      }
    },
    base64ToBlob (code) {
      code = code.replace(/[\n\r]/g, '')
      const raw = window.atob(code)
      const rawLength = raw.length
      const uInt8Array = new Uint8Array(rawLength)
      for (let i = 0; i < rawLength; ++i) {
        uInt8Array[i] = raw.charCodeAt(i)
      }
      return new Blob([uInt8Array], { type: 'application/pdf' })
    }
```

这里的content就是上面的那串base64格式的pdf了。只需要这两个方法，就可以完美实现了。



2.使用pdf.js进行预览。这种方式的话，稍微比上面这种方式比较麻烦。

优点就是无论什么浏览器，都可以完美的打开，另外你不需要什么功能的话，你可以注释掉，自定义性强。

缺点：文件较大，需要后期优化

步骤：

**一、下载 pdf.js** 

在哪里下载，当然是官网了啊，但是貌似最新版的pdf.js不支持ie了，你可以下载老版的，或者直接用我项目里的。或者说，你可以下载**babel-polyfill**来试试，之前我在写这个demo的时候，在ie上一直就会有某个方法报错，然后下载了babel-polyfill就完美解决了。

注意是这些文件：

![1637397772536](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1637397772536.png)

**二、将pdf文件夹扔到项目的public包里面** 

为什么要放到public包里面，原因就是webpack在进行打包的时候，是会将依赖到的东西打包的，但是open这种另一个网页的不算做是依赖到了这个文件，所以如果放到其他文件夹里面，可能不会被打包进去，而public包里面的内容原封不动的输出到dist文件夹里面的（网上的其他的教程也有说其他文件夹的，但是都是说的webpack会原封不动打包的那个文件夹）。所以说它的缺点也在这里，因为pdf.js的包还是蛮大的，所以最好就是放到静态资源服务器上，不要放到自己文件中，做个优化。

有些文章是需要对pdf.js里的内容进行修改的，我这个不需要，直接丢进去就得了。

**三、添加两个方法转换成pdf.js可以识别的格式** 

```js
viewPdf (content) {
      let url = this.createDownloadFileUrl('pdf预览', content)
      // console.log(url);
      window.open('/pdf/web/viewer.html?file=' + url)
    },
    createDownloadFileUrl (fileName, file) {
      var blob = this.dataURLtoFile(
        `data:application/pdf;base64,${file}`,
        fileName
      ) // application/zip 需要改成要下载文件的类型
      blob.lastModifiedDate = new Date()
      blob.name = fileName
      return URL.createObjectURL(blob)
    },
    dataURLtoFile (dataurl, filename) {
      // 生成Blob
      var arr = dataurl.split(',')
      var mime = arr[0].match(/:(.*?);/)[1]
      var bstr = atob(arr[1])
      var n = bstr.length
      var u8arr = new Uint8Array(n)
      while (n--) {
        u8arr[n] = bstr.charCodeAt(n)
      }
      return new Blob([u8arr], { type: mime })
    }
```

此步骤的特别注意：window.open('/pdf/web/viewer.html?file=' + url)  这个open的地址要特别注意，千万别写错了，不需要public，我们一般想的是打开public文件夹下面的pdf里的web，但是不需要，否则会报错。另外如果你的文件夹不是这么命名的，那么你就改成你自己命名的。

一般只需要这三步就可以完美解决了。之前写这个demo的时候参考了很多的文章和内容，走了许多的坑，最后总算是找到了这个非常简单的方法。另外的，还可以让用户自己上传pdf进行预览，这里就不说了，具体的可以去看我写的demo。



参考的文章：https://blog.csdn.net/shentibeitaokong/article/details/80011900

自己的demo地址：https://github.com/rui-rui-an/viewpdfbybase64
