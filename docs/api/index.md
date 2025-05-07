---
title: API Rekanpay
description: "API Rekanpay"
---

# Transaksi

## Request API
::code-group
  ::code-block{label="URL API" url api}

::alert{type="info"}
:badge[POST]{type="warning"}

https://api.rekanpay.id/v1/transaksi
:copy-button{content="https://api.rekanpay.id/v1/transaksi"}
::
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
    <td>reff_id</td>
    <td>REF9283MKJI989232</td>
    <td>String</td>
    <td>Ya</td>
    <td>Kode unik setiap transaksi, kode unik yang sama dianggap cek status transaksi</td>
  </tr>
  <tr>
    <td>kode_channel</td>
    <td>QRIS</td>
    <td>String</td>
    <td>Ya</td>
    <td>Kode channel transaksi. Required jika tipe direct</td>
  </tr>
  <tr>
    <td>nominal</td>
    <td>10000</td>
    <td>Int</td>
    <td>Ya</td>
    <td>Nominal</td>
  </tr>
  <tr>
    <td>customer_name</td>
    <td>ahmad</td>
    <td>String</td>
    <td>Ya</td>
    <td>Nama Customer</td>
  </tr>
   <tr>
    <td>customer_email</td>
    <td>userahmad@gmail.com</td>
    <td>String</td>
    <td>Ya</td>
    <td>Email Customer</td>
  </tr>
   <tr>
    <td>customer_phone</td>
    <td>08220000000</td>
    <td>String</td>
    <td>Ya</td>
    <td>Nomor HP Customer</td>
  </tr>
    <tr>
    <td>redirect_url</td>
    <td>https://demo.apime.com</td>
    <td>String</td>
    <td>Tidak</td>
    <td>URL untuk mengalihkan pelanggan setelah melakukan pembayaran</td>
  </tr>
   <tr>
    <td>expired</td>
    <td>1731946377</td>
    <td>Int</td>
    <td>Ya</td>
    <td>Batas waktu pembayaran dalam format unix timestamp (https://www.unixtimestamp.com). Jika parameter 0 maka akan digunakan default sistem 24jam</td>
  </tr>
  <tr>
    <td>tipe</td>
    <td>direct/webpay</td>
    <td>String</td>
    <td>Ya</td>
    <td>Gunakan webpay jika ingin pembayaran melalui link webpay rekanpay</td>
  </tr>
   <tr>
    <td>signature</td>
    <td>fea96b6f104582768ddaf921fe3648d2</td>
    <td>String</td>
    <td>Ya</td>
    <td>formula md5 dari MERCHANT_ID:SECRET:REFF_ID</td>
  </tr>
</table>
  ::

  ::code-block{label="Contoh Request" contoh-request}

   ```json
  {
    "merchant_id": "MC723923J823989",
    "kode_channel": "",
    "nominal": 10000,
    "reff_id": "REF9283MKJI989232",
    "redirect_url": "https://demo.apime.com",
    "signature": "fea96b6f104582768ddaf921fe3648d2",
    "expired": 1731946377,
    "customer_name": "ahmad",
    "customer_email": "userahmad@gmail.com",
    "customer_phone": "08220000000",
   "tipe": "webpay"
}

  ```

::


## Response API Transaksi



::code-group
::code-block{label="Virtual Akun"}
```json
{
    "data": {
        "nominal": 10000,
        "status": "Pending",
        "total_diterima": 9796,
        "data": "463000012672",
        "tipe":"va",
    },
    "status": 1
}
```
::

::code-block{label="Emoney"}
```json
{
    "data": {
        "nominal": 10000,
        "data": "https://m.dana.id/n/cashier/new/checkout?bizNo=20241118111212800110166842024724692&timestamp=1731945746553&originSourcePlatform=IPG&mid=216620000383553341323&did=216650000481612347325&sid=216660000481408876322&sign=a8xZP8ri%2Fj5Qg4yzixpM6AE0u8LITPvDO6DgLiqvIl3yTNW73%2BlSJ9%2FWzOIY7vncRinEWY1CDSnXbZl%2FBp3oZsbHrPZ5ZQU2CCvX2r3lmrrXIztQuyoDpweKm4OIiIZhnwFeL44CSzwxV1tNLzrs671OJ35m%2BSQ23%2BXvRWGqd0EpIwDg97T2FvnQrhdErEqS%2FtUtPJ8m5uNBaWh3jqgFf3CL2A4GakaOaXN5yx8Ew2L0q2CNzAYHdIjOyEIHkcpf%2FSLd0UqhRJ8SGTHFFiPBDkrTP8GMLjz5EmrGWJD6F0t%2F%2FIrmOB14TZDbB8ct2fx3PrSA1eTHoGbXnrhVBBXZaQ%3D%3D&forceToH5=false",
        "status": "Pending",
        "tipe": "pay_link",
        "total_diterima": 9696
    },
    "status": 1
}
```
::


::code-block{label="QRIS"}
```json
{
    "data": {
        "nominal": 10000,
        "data": "00020101021226610016ID.SHOPEE.....",
        "status": "Pending",
        "total_diterima": 9880,
        "qr_link": "",
        "tipe": "qris",
    },
    "status": 1
}
```
::

::code-block{label="WebPay"}
```json
{
    "data": {
        "data": "https://webpay.rekanpay.id/pay",
        "tipe": "web_pay",
    },
    "status": 1
}
```
::


::

