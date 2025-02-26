
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cek Stok</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f7f7f7;
    }
    .container {
      width: 80%;
      max-width: 400px;
      margin: 40px auto;
      padding: 20px;
      background-color: #fff;
      border: 1px solid #ddd;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    #result {
      margin-top: 20px;
    }
    table {
      border-collapse: collapse;
      width: 100%;
    }
    th, td {
      border: 1px solid #ddd;
      padding: 10px;
      text-align: left;
    }
    th {
      background-color: #f2f2f2;
      font-weight: bold;
    }
    .stok-hijau {
      color: #008000;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Cek Stok</h1>
    <div id="result"></div>
  </div>

  <script>
    const resultDiv = document.getElementById('result');

    fetch('https://panel.khfy-store.com/api/api-xl-v7/cek_stock_akrab', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/x-www-form-urlencoded',
        'Accept': 'application/json'
      }
    })
    .then(response => response.json())
    .then(data => {
      const stok = data.message.split('\n');
      const table = document.createElement('table');
      const thead = document.createElement('thead');
      const tbody = document.createElement('tbody');
      table.appendChild(thead);
      table.appendChild(tbody);
      resultDiv.innerHTML = '';
      resultDiv.appendChild(table);

      const row = document.createElement('tr');
      thead.appendChild(row);
      const th1 = document.createElement('th');
      th1.innerHTML = 'Produk';
      row.appendChild(th1);
      const th2 = document.createElement('th');
      th2.innerHTML = 'Stok';
      row.appendChild(th2);

      stok.forEach(item => {
        const [produk, stoknya] = item.split(': ');
        const row = document.createElement('tr');
        tbody.appendChild(row);
        const td1 = document.createElement('td');
        td1.innerHTML = produk;
        row.appendChild(td1);
        const td2 = document.createElement('td');
        td2.innerHTML = stoknya;
        td2.classList.add('stok-hijau');
        row.appendChild(td2);
      });
    })
    .catch(error => {
      resultDiv.innerHTML = 'Error: ' + error.message;
    });
  </script>
</body>
</html>
