<!-- <template>
    <div>
      <canvas ref="canvas" v-for="(canvas, index) in canvases" :key="index"></canvas>
      <button @click="convertToPDF">Convert to PDF</button>
    </div>
  </template>
  
  <script>
  import html2canvas from 'html2canvas';
  import jsPDF from 'jspdf';
  
  export default {
    data() {
      return {
        canvases: [], // Initialize the canvases array
      };
    },
    mounted() {
      // Example: Dynamically add canvases to the array
      const canvas1 = document.createElement('canvas');
      // Configure and render canvas1
      this.canvases.push(canvas1);
  
      const canvas2 = document.createElement('canvas');
      // Configure and render canvas2
      this.canvases.push(canvas2);
    },
    methods: {
      convertToPDF() {
        const doc = new jsPDF();
  
        const promises = this.canvases.map((canvas, index) => {
          return new Promise((resolve) => {
            html2canvas(canvas).then((canvasImage) => {
              const imgData = canvasImage.toDataURL('image/png');
              doc.addImage(imgData, 'PNG', 10, 10, 190, 0);
              if (index < this.canvases.length - 1) {
                doc.addPage();
              }
              resolve();
            });
          });
        });
  
        Promise.all(promises).then(() => {
          doc.save('converted.pdf');
        });
      },
    },
  };
  </script>
  
  <style scoped>
  canvas {
    border: 1px solid #000;
    margin-bottom: 10px;
  }
  </style>
   -->



   <template>
    <div>
      <canvas ref="canvas" v-for="(canvas, index) in canvases" :key="index"></canvas>
      <button @click="convertToPDF">Convert to PDF</button>
    </div>
  </template>
  
  <script>
  import html2canvas from 'html2canvas';
  import jsPDF from 'jspdf';
  
  export default {
    data() {
      return {
        canvases: [],
      };
    },
    mounted() {
      // Initialize canvases here or dynamically add them
    },
    methods: {
    //   convertToPDF() {
    //     const doc = new jsPDF('p', 'mm', 'a4');
  
    //     const promises = this.canvases.map((canvas) => {
    //       return new Promise((resolve) => {
    //         html2canvas(canvas).then((canvasImage) => {
    //           const imageData = canvasImage.toDataURL('image/png');
    //           doc.addImage(imageData, 'PNG', 10, 10, 190, 0);
    //           resolve();
    //         });
    //       });
    //     });
  
    //     Promise.all(promises).then(() => {
    //       doc.save('converted.pdf');
    //     });
    //   },

    // Multiple canvas to muliple pdf sheets
    convertToPDF() {
  const doc = new jsPDF('p', 'mm', 'a4');
  const promises = [];

  this.canvases.forEach((canvas, index) => {
    promises.push(
      new Promise((resolve) => {
        html2canvas(canvas).then((canvasImage) => {
          const imageData = canvasImage.toDataURL('image/png');
          doc.addImage(imageData, 'PNG', 10, 10, 190, 0);

          if (index < this.canvases.length - 1) {
            doc.addPage();
          }

          resolve();
        });
      })
    );
  });

  Promise.all(promises).then(() => {
    doc.save('converted.pdf');
  });
},



    },
  };
  </script>
  
  <style scoped>
  canvas {
    border: 1px solid #000;
    margin-bottom: 10px;
  }
  </style>
  