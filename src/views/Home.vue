<template>
  <div class="home">
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="date" label="审批日期" width="180"> </el-table-column>
      <el-table-column prop="name" label="审批人" width="180"> </el-table-column>
      <el-table-column prop="baseFile" label="审批意见">
        <template  slot-scope="scope">
          <div class="viewItem" @click="viewPdf(scope.row.baseFile)">
            预览
          </div>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  name: 'Home',
  components: {},
  data () {
    return {
      tableData: [
        {
          date: '2021-05-02',
          name: '王小虎',
          baseFile: 'JVBERi0xLjQKJeLjz9MKMiAwIG9iaiA8PC9MZW5ndGggNzUzL0ZpbHRlci9GbGF0ZURlY29kZT4+c3RyZWFtCnicrZY/TxRBGIcXEy220d5mQgUF47zzf7EzUYyFkeMSTSSnggfGSAGKxMrSGDDQSExMSCz8EnZ+DS2s/AAmRhIbfOd218DtvHO3BMgdl/3NPvvsb2bnWM+vdXNlmReWdR/ngs2A9eHT9W4+n68PXpLdwmAuF9ywrdx7rpjTlknDJZOCbfTzhSoDUPg3hNpw5YZT47l3g9gabtRQLKXmGujYF7zQZKyM4bqEgwEuh/NSW/pSG3xEG8NSeyittDEuL3wyrrWpuNIm4lob40r7ZF5qg0hoY5jSxjilTcWVNhHX2hjT2raQtHYIE9ohTmiTcalNxZV2iBPaTie0MUxpY5zSpuJKm4hrbYwT2sYmtI1Nahub1KbiSpuIa21jU9oq8UiGMKWtko8kGVfaRFxrq8YjOR82S2ACf4HJcC5zHnfLtfzKDWCAO+gKbpbdjQBS+IOwqUcX3359Nvfw6nT3KW6imAEexc31GKkQvGDOwH+QOAZSNai3u3CYgABYDmNg7n9aenX7S/deCuWAWz0a1bnc+9v/8/53AiWV4+BGo5Y/9+0IlBKSj0EK9zeCpAG4GLOqMH2pqcN1KJlTEpdCxSoCaiqDcNZQr1JyW8RG799cuvThW+QMC1xBlC8zkUHmsxl8l/guM50xPOayWfxUNFlSWu7NGbEKyfHxOBNWVSHoJipWoRus8ubo59urv+gCY/TTFtiC5ZGlMk8X2JoV8VIWt8poJ9uH/TdrH8XE67t3Fqf3z2/97L1892P3+9Hiys7kzuTRBDUZtrANLUVORmT04ILkbMTwre+6mo02rAJZkFjObVmYNVla+DAbEdbe5vpq5+DFBXGO7N35hoAm95HI6FUIE04XH+GfuvgWrGLAiqyguvizYGlwg+KbrL3NzkGidCsaFzf0Ym+OTu48MXr7mqrKW7MSa70lS0fXOv6TJqKdbB8+6DxZTpSum98cll7pzdEjvjFj/Na3V9c+Ngvw6Cy+Is9sXfupWf8AJ3cIwAplbmRzdHJlYW0KZW5kb2JqCjQgMCBvYmo8PC9QYXJlbnQgMyAwIFIvQ29udGVudHMgMiAwIFIvVHlwZS9QYWdlL1Jlc291cmNlczw8L1Byb2NTZXQgWy9QREYgL1RleHQgL0ltYWdlQiAvSW1hZ2VDIC9JbWFnZUldL0ZvbnQ8PC9GMSAxIDAgUj4+Pj4vTWVkaWFCb3hbMCAwIDU5NSA4NDJdPj4KZW5kb2JqCjUgMCBvYmo8PC9Gb250QkJveCBbLTI1IC0yNTQgMTAwMCA4ODBdL0NhcEhlaWdodCA4ODAvU3R5bGU8PC9QYW5vc2UoAQUCAgQAAAAAAAAAKT4+L1R5cGUvRm9udERlc2NyaXB0b3IvU3RlbVYgOTMvRGVzY2VudCAtMTIwL0ZsYWdzIDYvRm9udE5hbWUvU1RTb25nLUxpZ2h0L0FzY2VudCA4ODAvSXRhbGljQW5nbGUgMD4+CmVuZG9iago2IDAgb2JqPDwvQmFzZUZvbnQvU1RTb25nLUxpZ2h0L0NJRFN5c3RlbUluZm88PC9PcmRlcmluZyhHQjEpL1JlZ2lzdHJ5KEFkb2JlKS9TdXBwbGVtZW50IDQ+Pi9XIFsxWzIwN10xNFszNzVdMTcgMjYgNDYyIDI3WzIzOF1dL1R5cGUvRm9udC9TdWJ0eXBlL0NJREZvbnRUeXBlMC9Gb250RGVzY3JpcHRvciA1IDAgUi9EVyAxMDAwPj4KZW5kb2JqCjEgMCBvYmo8PC9EZXNjZW5kYW50Rm9udHNbNiAwIFJdL0Jhc2VGb250L1NUU29uZy1MaWdodC1VbmlHQi1VQ1MyLUgvVHlwZS9Gb250L0VuY29kaW5nL1VuaUdCLVVDUzItSC9TdWJ0eXBlL1R5cGUwPj4KZW5kb2JqCjMgMCBvYmo8PC9UeXBlL1BhZ2VzL0NvdW50IDEvS2lkc1s0IDAgUl0+PgplbmRvYmoKNyAwIG9iajw8L1R5cGUvQ2F0YWxvZy9QYWdlcyAzIDAgUj4+CmVuZG9iago4IDAgb2JqPDwvUHJvZHVjZXIoaVRleHQgMi4wLjcgXChieSBsb3dhZ2llLmNvbVwpKS9Nb2REYXRlKEQ6MjAyMTA2MzAwOTU1NDkrMDgnMDAnKS9DcmVhdGlvbkRhdGUoRDoyMDIxMDYzMDA5NTU0OSswOCcwMCcpPj4KZW5kb2JqCnhyZWYKMCA5CjAwMDAwMDAwMDAgNjU1MzUgZiAKMDAwMDAwMTM3OCAwMDAwMCBuIAowMDAwMDAwMDE1IDAwMDAwIG4gCjAwMDAwMDE1MDEgMDAwMDAgbiAKMDAwMDAwMDgzNSAwMDAwMCBuIAowMDAwMDAwOTkxIDAwMDAwIG4gCjAwMDAwMDExODEgMDAwMDAgbiAKMDAwMDAwMTU1MSAwMDAwMCBuIAowMDAwMDAxNTk1IDAwMDAwIG4gCnRyYWlsZXIKPDwvUm9vdCA3IDAgUi9JRCBbPDk5MGVjNjU1ZDZhODIzODRlYWFlODBkY2FhNzRiNjNiPjwyNDRjNjQ1Yzc5NWRkZWQ5MmI1NTM2MzViNGE3NmY2Zj5dL0luZm8gOCAwIFIvU2l6ZSA5Pj4Kc3RhcnR4cmVmCjE3MjYKJSVFT0YK'
        }
      ]
    }
  },
  methods:{
    viewPdf(content){
       if (!content) {
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
    },
  }
}
</script>
<style lang="less" scoped>
.home{
  .viewItem{
    cursor: pointer;
    width: 80px;
    color: #0094ff;
  }
}
</style>