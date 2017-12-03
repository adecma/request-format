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
- lainnya (... dimaksudkan jika data tersebut lebih dari satu)

## Data Instansi
Request untuk mengambil semua data *instansi*. Adapun formatnya seperti di bawah ini:
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
Request untuk mengambil data *Renstra* (visi, misi, tujuan dan sasaran) sesuai dengan idKantor, idInstansi dan tahun yang dipilih. Adapun formatnya seperti dibawah ini :
- idVisi, namaVisi, dataMisi
- idMisi, namaMisi, dataTujuan
- idTujuan, namaTujuan, dataSasaran
- idSasaran, namaSasaran

```json
{
    "code" : 200,
    "status" : "success",
    "message" : "OKE",
    "request" : "renstra",
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

## Data Renja Akhir dan Pra RKA
Request untuk mengambil data *Renja Ahir* yang berstatus *disetujui* serta data *Pra Rka*, sesuai dengan idKantor, idInstansi dan tahun yang dipilih. Adapun formatnya seperti dibawah ini :
- idJenisUrusan, namaJenisUrusan, dataUrusan
- idUrusan, namaUrusan, dataProgram
- idProgram, idRenjaAkhir, namaProgram, lokasiProgram, dataIndikatorProgram, dataKegiatan
- indikatorProgram, volume, satuan
- idKegiatan, idRka, namaKegiatan, lokasiKegiatan, sumberDana, pagu, kelompokSasaran, dataIndikatorKegiatan, dataBelanja
- indikatorKegiatan, volume, satuan
- rekAkun, namaRekAkun, dataRekKelompok
- rekKelompok, namaRekKelompok, dataRekBelanja
- rekBelanja, namaRekBelanja, dataRekBagian
- rekBagian, namaRekBagian, dataSubBagian
- rekSubBagian, namaSubBagian, dataRincian
- idRincian, namaRincian, dataSubRincian
- idSubRincian, namaSubRincian, volume1, satuan1, volume2, satuan2, volume3, satuan3, nilai, jumlah

```json
{
    "code" : 200,
    "status" : "success",
    "message" : "OKE",
    "request" : "renjaakhir_rka",
    "datetime" : "2017-12-02 08:12:12",
    "data" : [
        {
            "idJenisUrusan" : 1,
            "namaJenisUrusan" : "Wajib",
            "dataUrusan" : [
                {
                    "idUrusan" : 7,
                    "namaUrusan" : "Perhubungan",
                    "dataProgram" : [
                        {
                            "idProgram" : 16,
                            "idRenjaAkhir" : 7248,
                            "namaProgram" : "Program Rehabilitasi dan Pemeliharaan Prasarana dan Fasilitas LLAJ",
                            "lokasiProgram" : "Dinas Perhubungan Informatika dan Komunikasi",
                            "dataIndikatorProgram" : [
                                {
                                    "indikatorProgram" : "Meningkatnya Keselamatan dan Kenyamanan transportasi Umum",
                                    "volume" : 79,
                                    "satuan" : "Persen"
                                },
                                ...
                            ],
                            "dataKegiatan" : [
                                {
                                    "idKegiatan" : 4,
                                    "idRka" : 8688,
                                    "namaKegiatan" : "Sosialisasi Perda Perparkiran",
                                    "lokasiKegiatan" : "Telaga Langsat",
                                    "sumberDana" : "Pendapatan Daerah",
                                    "pagu" : 17155000,
                                    "kelompokSasaran" : "Pengelola dan Juru Parkir",
                                    "dataIndikatorKegiatan" : [
                                        {
                                            "indikatorKegiatan" : "Terlaksananya Sosialisasi Perda Perparkiran 1 Paket",
                                            "volume" : 1,
                                            "satuan" : "Paket"
                                        },
                                        ...
                                    ],
                                    "dataBelanja" : [
                                        {
                                            "rekAkun" : 5,
                                            "namaRekAkun" : "Belanja",
                                            "dataRekKelompok" : [
                                                "rekKelompok" : 2,
                                                "namaRekKelompok" : "Belanja Langsung",
                                                "dataRekBelanja" : [
                                                    {
                                                        "rekBelanja" : 2,
                                                        "namaRekBelanja" : "Belanja Barang dan Jasa",
                                                        "dataRekBagian" : [
                                                            {
                                                                "rekBagian" : 3,
                                                                "namaRekBagian" : "Belanja Jasa Kantor",
                                                                "dataSubBagian" : [
                                                                    {
                                                                        "rekSubBagian" : 6,
                                                                        "namaSubBagian" : "Belanja kawat/faksimili/internet",
                                                                        "dataRincian" : [
                                                                            {
                                                                                "idRincian" : 45042,
                                                                                "namaRincian" : "Belanja Jaringan Internet",
                                                                                "dataSubRincian" : [
                                                                                    {
                                                                                        "idSubRincian" : 123267,
                                                                                        "namaSubRincian" : "Internet",
                                                                                        "volume1" : 2,
                                                                                        "satuan1" : "Rek",
                                                                                        "volume2" : 12,
                                                                                        "satuan2" : "Bulan",
                                                                                        "volume3" : 1,
                                                                                        "satuan3" : "Tahun",
                                                                                        "nilai" : 800000,
                                                                                        "jumlah" : 19200000,
                                                                                    },
                                                                                    ...
                                                                                ]
                                                                            },
                                                                            ...
                                                                        ]
                                                                    },
                                                                    ...
                                                                ]
                                                            },
                                                            ...
                                                        ]
                                                    },
                                                    ...
                                                ]
                                            ]
                                        },
                                        ...
                                    ]
                                },
                                ...
                            ]
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
```
