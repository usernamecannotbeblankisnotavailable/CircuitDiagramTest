<!DOCTYPE html>
<html>
  <head>
    <title>PDF Viewer</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.10.377/pdf.min.js"></script>
  </head>
  <body>
    <canvas id="pdf-canvas"></canvas>
    <script>
      const url = '[<Your GitHub PDF URL>](https://raw.githubusercontent.com/usernamecannotbeblankisnotavailable/CircuitDiagramTest/main/98903_98925_Master_ElectricalCircuitDiagram%20(1).PDF)'; // Replace with your PDF's URL

      pdfjsLib.getDocument(url).promise.then(function(pdfDoc_) {
        const pdfDoc = pdfDoc_;
        const pageNum = 1; // You can add controls for navigation here
        pdfDoc.getPage(pageNum).then(function(page) {
          const canvas = document.getElementById('pdf-canvas');
          const ctx = canvas.getContext('2d');
          const viewport = page.getViewport({ scale: 1 });
          canvas.height = viewport.height;
          canvas.width = viewport.width;
          page.render({ canvasContext: ctx, viewport: viewport });
        });
      });
    </script>
  </body>
</html>
