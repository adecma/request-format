# REQUEST RESPONSE JSON
Data response json ini di gunakan untuk kebutuhan integrasi data dari web app bappelitbangda ke simda keuangan.

Adapun secara garis besar, data yang kami butuhkan adalah :
- Data Instansi (keseluruhan, baik itu SKPD, Kecamatan dan Kelurahan)
- Data Renstra (sesuai tahun, id kantor dan id instansi saat request)
- Data Renja dan PRA RKA (sesuai tahun, id kantor dan id instansi saat request)

## Data Instansi
Request untuk mengambil semua data instansi :
- idKantor
- idInstansi
- jenis (ex : skpd, kecamatan, kelurahan)
- nama

```json
{
    {
        "idKantor" : 1,
        "idInstansi" : 1,
        "jenis" : "skpd",
        "nama" : "Dinas Komunikasi dan Informatika"
    },
    ...
}
```
