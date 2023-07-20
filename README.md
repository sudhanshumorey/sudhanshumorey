<!DOCTYPE html>
<html>
<head>
  <title>Bajra Yield Line Chart</title>
  <style>
    canvas {
      border: 1px solid #ccc;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>Bajra Yield Line Chart</h1>
  <canvas id="chart" width="800" height="400"></canvas>

  <script>
    
    const data = [
      { year: 2001, yield: 281 },
      { year: 2002, yield: 277 },
      { year: 2003, yield: 275 },
      { year: 2004, yield: 457 },
      { year: 2005, yield: 200 },
      { year: 2006, yield: 280 },
      { year: 2007, yield: 150 }
    ];
 
    const canvas = document.getElementById('chart');
    const ctx = canvas.getContext('2d');
   
    const chartWidth = canvas.width - 40;
    const chartHeight = canvas.height - 40;
   
    const maxYield = Math.max(...data.map(item => item.yield));
  
    const xScale = chartWidth / (data.length - 1);
    const yScale = chartHeight / maxYield;
   
    ctx.beginPath();
    ctx.moveTo(20, 20);
    ctx.lineTo(20, canvas.height - 20);
    ctx.lineTo(canvas.width - 20, canvas.height - 20);
    ctx.strokeStyle = '#000';
    ctx.stroke();

    ctx.beginPath();
    ctx.moveTo(20, canvas.height - 20 - (data[0].yield * yScale));
    ctx.fillStyle = '#ff0000';
    ctx.strokeStyle = '#ff0000';
    for (let i = 1; i < data.length; i++) {
      const x = 20 + i * xScale;
      const y = canvas.height - 20 - (data[i].yield * yScale);
      ctx.lineTo(x, y);
      ctx.arc(x, y, 5, 0, Math.PI * 2);
      ctx.fillText(data[i].yield, x - 10, y - 10);
    }
    ctx.stroke();

    </script>
</body>
</html>
