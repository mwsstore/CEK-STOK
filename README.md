

<html>
<head>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f2f2f2;
    }
    #stok-table {
      border-collapse: collapse;
      width: 46%;
      margin: 40px auto;
      background-color: #c6efce;
      border: 1px solid #3e8e41;
    }
    #stok-table th, #stok-table td {
      border: 1px solid #3e8e41;
      padding: 10px;
      text-align: left;
    }
    #stok-table th {
      background-color: #3e8e41;
      color: #ffffff;
    }
    #stok-table td {
      background-color: #c6efce;
    }
    #stok-table tr:nth-child(even) {
      background-color: #b3dfb5;
    }
    #stok-table tr:hover {
      background-color: #a1d9a3;
    }
    /* Tambahkan kode CSS berikut untuk membuat layout responsif */
    @media only screen and (max-width: 768px) {
      #stok-table {
        width: 90%;
        margin: 20px auto;
      }
      .container {
        display: block;
      }
      .container div {
        margin-bottom: 20px;
      }
    }
    #tombol {
      background-color: #34C759;
      color: #ffffff;
      padding: 15px 35px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin: 0 auto;
      display: block;
    }
    #tombol:hover {
      background-color: #2E865F;
    }
  </style>
</head>
<body>
  <BR>
  <button id="tombol"><b>Cek Stok</b></button>
  <table id="stok-table">
    <thead>
      <tr>
        <th>Nama</th>
        <th>Stok</th>
        <th>Harga</th>
      </tr>
    </thead>
    <tbody id="stok-body">
    </tbody>
  </table>
  <div class="container">
  </div>
  <script>
    const apiUrl = 'https://sheetdb.io/api/v1/i6leb6wvx8zlq';
    const stokTable = document.getElementById('stok-table');
    const stokBody = document.getElementById('stok-body');
    const tombol = document.getElementById('tombol');

    tombol.addEventListener('click', () => {
      fetch(apiUrl)
        .then(response => response.json())
        .then(data => {
          stokBody.innerHTML = '';
          data.forEach(item => {
            const row = document.createElement('tr');
            const namaCell = document.createElement('td');
            const stokCell = document.createElement('td');
            const hargaCell = document.createElement('td');
            namaCell.innerHTML = item.nama.replace(/\n/g, '<br>');
            stokCell.textContent = item.stok;
            hargaCell.textContent = item.harga;
            row.appendChild(namaCell);
            row.appendChild(stokCell);
            row.appendChild(hargaCell);
            stokBody.appendChild(row);
          });
        })
        .catch(error => {
          console.error(error);
        });
    });
  </script>
</body>
</html>
