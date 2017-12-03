# REQUEST RESPONSE JSON
Data response json ini di gunakan untuk kebutuhan integrasi data dari web app bappelitbangda ke simda keuangan.

Adapun secara garis besar, data yang kami butuhkan adalah :
- Data Instansi (keseluruhan, baik itu SKPD, Kecamatan dan Kelurahan)
- Data Renstra (sesuai tahun, id kantor dan id instansi saat request)
- Data Renja dan PRA RKA (sesuai tahun, id kantor dan id instansi saat request)

Berikut ini format keterangan saat response :
- code (kode status request)
- status (status request : success, failed)
- message (keterangan request)
- request (jenis request)
- datetime (waktu request)
- data (data request)

## Data Instansi
Request untuk mengambil semua data instansi. Adapun formatnya seperti di bawah ini:
- idKantor
- idInstansi
- jenis (ex : skpd, kecamatan, kelurahan)
- namaInstansi

```json
{
    "code" : 200,
    "status" : "success",
    "message" : "OKE",
    "request" : "instansi",
    "datetime" : "2017-12-02 08:12:12",
    "data" : [
        {
            "idKantor" : 1,
            "idInstansi" : 1,
            "jenis" : "skpd",
            "namaInstansi" : "Dinas Komunikasi dan Informatika"
        },
        ...
    ]
}
```

## Data Renstra
Request untuk mengambil data Renstra (visi, misi, tujuan dan sasaran) sesuai dengan idKantor, idInstansi dan tahun yang dipilih. Adapun formatnya seperti dibawah ini :
- idVisi
- namaVisi
- dataMisi
- idMisi
- namaMisi
- dataTujuan
- idTujuan
- namaTujuan
- dataSasaran
- idSasaran
- namaSasaran

```json
{
    "code" : 200,
    "status" : "success",
    "message" : "OKE",
    "request" : "instansi",
    "datetime" : "2017-12-02 08:12:12",
    "data" : [
        {
            "idVisi" : 20,
            "namaVisi" : "Terwujudnya tata kelola pemerintahan yang baik",
            "dataMisi" : [
                {
                    "idMisi" : 25,
                    "namaMisi" : "Meningkatkan pelayanan pendidikan",
                    "dataTujuan" : [
                        {
                            "idTujuan" : 40,
                            "namaTujuan" : "Meningkatkan kesempatan kerja",
                            "dataSasaran" : [
                                {
                                    "idSasaran" : 56,
                                    "namaSasaran" : "Meningkatnya jangkauan dan kualitas pendidikan"
                                },
                                ...
                            ]
                        },
                        ...
                    ]
                },
                ...
            ]
        }
    ]
}
```
