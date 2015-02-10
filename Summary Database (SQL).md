# Konsep Database

Singkatnya, **database merupakan kumpulan dari data-data yang bisa diolah menjadi informasi**
dimana di setiap kumpulan data-data tersebut, terdapat satu data yang disebut *Primary Keyword*

sebelum mengarah ke praktek pengolahan database, perlu anda ketahui bahwa
pada perkembangannya, terdapat beberapa aplikasi yang dapat digunakan untuk mengolah database.
diantaranya :
  - text file
  - Database Management System (DBMS)
  - SQL Server
dan lainnya.

Nah, pada tulisan ini saya akan mencoba menjelaskan pengolahan database menggunakan SQL Server Management Studio

didalam database terdapat perintah-perintah utama yang biasa digunakan dalam pengolahan data, seperti :
  - *select*          : perintah untuk mengekstrak data dari database
  - *update*          : perintah untuk memperbarui data di dalam database
  - *delete*          : perintah untuk menghapus data dari database
  - *insert into*     : perintah untuk memasukan data baru ke dalam database
  - *create database* : perintah untuk membuat database 
  - *alter database*  : perintah untuk memodifikasi database
  - *drop table*      : perintah untuk menghapus tabel
  - *create index*    : perintah untuk membuat index
  - *drop index*      : perintah untuk menghapus index

Membuat database dengan SQL Server Management Studio
1. Pastikan di PC anda memiliki aplikasi SQL Server Management Studio
2. Kemudian akses SQL pada PC anda
3. Setelah dibuka, akan tampil GUI (Connect to Server) => Connect
4. Pada 'Database' => klik kanan => New Database => beri nama database misal (lab1)
5. Pada 'lab1' => klik kanan => New Query

Akan tampil berupa terminal yang dapat dipergunakan oleh anda dalam mengolah database 

untuk permulaan, buatlah program berikut pada database anda :
```SQL
CREATE TABLE [dbo].[mahasiswa]( --membuat tabel dengan nama mahasiswa
	--berikut yang akan ditampilkan dalam data
	[nim] [char](10) NOT NULL,
	[nama] [varchar](50) NULL,
	[tgllahir] [date] NULL,
	[tmplahir] [varchar](50) NULL,
	[kodejurusan] [char](2) NOT NULL,
 CONSTRAINT [PK_mahasiswa] PRIMARY KEY CLUSTERED 
(
	[nim] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]


CREATE TABLE [dbo].[jurusan]( --membuat table baru jurusan 
	[kodejurusan] [char](2) NOT NULL,
	[namajurusan] [varchar](50) NULL,
	[kodefakultas] [char](2) NOT NULL,
 CONSTRAINT [PK_jurusan] PRIMARY KEY CLUSTERED 
(
	[kodejurusan] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]


CREATE TABLE [dbo].[fakultas]( --membuat table baru fakultas
	[kodefakultas] [char](2) NOT NULL,
	[namafakultas] [varchar](50) NULL,
 CONSTRAINT [PK_fakultas] PRIMARY KEY CLUSTERED 
(
	[kodefakultas] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]

--perintah insert into untuk memasukan data baru ke dalam database yaitu kelompok fakultas 
insert into fakultas values('01', 'FAPERTA') 
insert into fakultas values('02', 'FATETA')
insert into fakultas values('03', 'FEMA')
insert into fakultas values('04', 'FMIPA')
insert into fakultas values('05', 'FAHUTAN')

--untuk fakultas FAPERTA memiliki kode '01', dst..

select * from mahasiswa

insert into jurusan values('01', 'Agronomi dan Holtikultura', '01')
insert into jurusan values('02', 'Proteksi Tanaman', '01')
insert into jurusan values('07', 'Fisika', '04')
insert into jurusan values('10', 'Ilmu Keluarga dan Konsumen', '03')
insert into jurusan values('03', 'Teknologi Hasil Hutan', '05')
insert into jurusan values('08', 'Teknologi Pangan', '02')
insert into jurusan values('04', 'Teknologi Industri Pertanian', '02')
insert into jurusan values('05', 'Statistika', '04')
insert into jurusan values('09', 'Sains Komunikasi dan Pengembangan Masyarakat', '03')
insert into jurusan values('06', 'Ilmu Komputer', '03')

select * from mahasiswa

insert mahasiswa values  ('001', 'Rizky Amelia', '1993-08-09','Jakarta', '01')
insert mahasiswa values  ('002', 'Della Tiaraputri Aldrifisia', '1994-01-07','Padang', '04')
insert mahasiswa values  ('003', 'Nida Nurlivi Fauziyah', '1993-09-05','Cianjur', '06')
insert mahasiswa values  ('004', 'Ni Kadek Tri Semarandani', '1993-03-08','Sampit', '07')
insert mahasiswa values  ('005', 'Lutpita Mahardika', '1993-05-02','Purwakarta', '10')
insert mahasiswa values  ('006', 'Raytisa Sirgin Sitepu', '1993-03-05','Medan', '02')
insert mahasiswa values  ('007', 'Yulina Jayanti', '1993-06-07','Lampung', '03')
insert mahasiswa values  ('008', 'Nadia Septiani', '1993-09-09','Bogor', '05')
insert mahasiswa values  ('009', 'Faza Ardelia', '1993-08-08','Jakarta', '09')
insert mahasiswa values  ('010', 'Khusnul Khotimah', '1993-07-09','Jakarta', '08')

select * from mahasiswa

select nim, nama, tgllahir, tmplahir, namajurusan, namafakultas from mahasiswa 
inner join jurusan on mahasiswa.kodejurusan=jurusan.kodejurusan 
inner join fakultas on jurusan.kodefakultas=fakultas.kodefakultas
```


untuk penjelasannya, akan saya lanjutkan besok, bye ;-) 


