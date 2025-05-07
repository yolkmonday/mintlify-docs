---
title: Akun Rekanpay
description: "Informasi Akun Rekanpay"
---

# Informasi Akun

## Request API
::code-group
  ::code-block{label="URL API" url api}

  ::alert{type="info"}
  :badge[POST]{type="warning"}
  
  https://api.rekanpay.id/v1/akun
  :copy-button{content="https://api.rekanpay.id/v1/akun"}
  ::
  ::code-block{label="Body" body}
  <table>
    <tr>
      <th>Parameter</th>
      <th>Contoh</th>
      <th>Tipe</th>
      <th>Wajib</th>
      <th>Keterangan</th>
    </tr>
    <tr>
      <td>merchant_id</td>
      <td>MC723923J823989</td>
      <td>String</td>
      <td>Ya</td>
      <td>Merchant ID</td>
    </tr>
    <tr>
      <td>signature</td>
      <td>fea96b6f104582768ddaf921fe3648d2</td>
      <td>String</td>
      <td>Ya</td>
      <td>formula md5 dari MERCHANT_ID:SECRET</td>
    </tr>
  </table>
  ::
  ::code-block{label="Contoh Request" contoh-request}
  ```json
  {
    "merchant_id":"MC723923J823989",
    "signature":"c76e6a5f1f4d87a59b782f6c8f8be00d"
  }
  ```
  ::
::

## Response API

::code-group
  ::code-block{label="Data akun"}
  ```json
  {
      "data": {
          "merchant_id": "MC723923J823989",
          "merchant_name": "d",
          "saldo": 236056,
          "saldo_kliring": 49120
      },
      "status": 1
  }
  ```
  ::
::

