



<template>
  <div>
    <button @click="downloadPdf">Download PDF</button>
  </div>
</template>

<script>
export default {
  name: 'StaticPdfDownloader',
  methods: {
    downloadPdf() {
      const base64Pdf = `
JVBERi0xLjQKJcfsj6IKNSAwIG9iago8PC9UeXBlL1BhZ2UvUGFyZW50IDMgMCBSL1Jlc291cmNl
czw8L0V4dEdTdGF0ZTw8L0dTIChUaGlzIGlzIGEgdGVzdCBwZGYpPj4+Pi9NZWRpYUJveFswIDAg
NjEyIDc5Ml0vQ29udGVudHMgNiAwIFIvR3JvdXA8PC9TL1RyYW5zcGFyZW5jeT4+Pj4KZW5kb2Jq
CjYgMCBvYmoKPDwvTGVuZ3RoIDcyPj4Kc3RyZWFtCkJUIApGMSAxMiBUZgowIDUwMCBUZAooSGVs
bG8sIFZ1ZSEpIFRqCkVUCmVuZHN0cmVhbQplbmRvYmoKMiAwIG9iago8PC9UeXBlL1BhZ2VzL0tp
ZHMgWzUgMCBSXS9Db3VudCAxPj4KZW5kb2JqCjcgMCBvYmoKPDwvVHlwZS9DYXRhbG9nL1BhZ2Vz
IDIgMCBSPj4KZW5kb2JqCjggMCBvYmoKPDwvQ3JlYXRvciAoU2ltcGxlIFBERiBUZXN0KS9Qcm9k
dWNlciAoVnVlKSB+IFBERiBFeGFtcGxlPj4KZW5kb2JqCjEgMCBvYmoKPDwvVHlwZS9Eb2N1bWVu
dC9QYWdlcyAyIDAgUi9PcGVuQWN0aW9uWy9WaWV3L1ByaW50XS9UeXBlL1BhZ2VzL1BhZ2VMYXlv
dXQvT25lQ29sdW1uPj4KZW5kb2JqCnhyZWYKMCA5CjAwMDAwMDAwMDAgNjU1MzUgZiAKMDAwMDAw
MDA5MCAwMDAwMCBuIAowMDAwMDAwMTgxIDAwMDAwIG4gCjAwMDAwMDAyMzIgMDAwMDAgbiAKMDAw
MDAwMDM0MCAwMDAwMCBuIAowMDAwMDAwNDE1IDAwMDAwIG4gCjAwMDAwMDA0NzAgMDAwMDAgbiAK
MDAwMDAwMDUxOSAwMDAwMCBuIAowMDAwMDAwNjAwIDAwMDAwIG4gCnRyYWlsZXIKPDwvU2l6ZSA5
L1Jvb3QgMSAwIFIvSW5mbyA4IDAgUj4+CnN0YXJ0eHJlZgowCiUlRU9GCg
      `.replace(/\s+/g, ''); // remove whitespace/newlines

      this.downloadBase64Pdf(base64Pdf, 'example.pdf');
    },

    downloadBase64Pdf(base64String, filename) {
      const linkSource = `data:application/pdf;base64,${base64String}`;
      const downloadLink = document.createElement('a');
      downloadLink.href = linkSource;
      downloadLink.download = filename;

      // Required for Safari
      document.body.appendChild(downloadLink);
      downloadLink.click();
      document.body.removeChild(downloadLink);
    }
  }
};
</script>
