# Jarkom-Modul-4-E14-2021

**Anggota kelompok**:

- Dwi Wahyu Santoso (05111840000121)
- Khaela Fortunela (05111940000057)
- Husin Muhammad Assegaff (05111940000127)

---

## Tabel Konten

A. Jawaban

- [A. Topologi](#a-topologi)
- [B. VSLM pada CPT](#b-vlsm-pada-cpt)
  - [1. VLSM Subnetting](#1-vlsm-subnetting)
  - [2. VLSM Routing](#2-vlsm-routing)
  - [3. VLSM Testing](#3-vlsm-testing)
- [C. CIDR pada GNS3](#c-cidr-pada-gns3)
  - [1. CIDR Subnetting](#1-cidr-subnetting)
  - [2. CIDR Routing](#2-cidr-routing)
  - [3. CIDR Testing](#3-cidr-testing)

B. Kendala

- [Kendala](#kendala)

---

## A. Topologi

Pembagian IP menggunakan Prefix IP yang telah ditentukan pada modul pengenalan. Prefix IP Address kelompok E14 kami adalah `10.36`. <br>
![topologi](img/topologi.PNG)

## B. VLSM pada CPT

**1. VLSM Subnetting**<br>
     Berdasarkan topologi, ditemukan 15 subnet termasuk subnet untuk server dan router. Polanya seperti yang terlihat pada gambar di bawah ini. Selain itu ditambahkan juga besar netmask dari subnet tersebut berdasarkan jumlah ip yang dibutuhkan masing-masing subnet.<br> 
     ![alt_text](img/vlsm-subnetting.PNG)<br>
     Pembagian IP menggunakan teknik VLSM memang tidak fleksible namun dalam pemakaian ip cukup efisien. Caranya terlihat seperti gambar di bawah ini.
     ![alt_text](img/vlsm-ip-arr.PNG)<br>
**2. VLSM Routing**<br>
     a. Foosha
        Jalankan command berikut pada cmd router Foosha.
        ```
          ip route 10.36.27.0 255.255.255.128 10.36.27.150
          ip route 10.36.16.0 255.255.252.0 10.36.27.150
          ip route 10.36.0.0 255.255.248.0 10.36.27.150
          ip route 10.36.20.0 255.255.252.0 10.36.27.154
          ip route 10.36.24.0 255.255.254.0 10.36.27.154
          ip route 10.36.27.128 255.255.255.240 10.36.27.154
          ip route 10.36.26.0 255.255.255.0 10.36.27.154
          ip route 10.36.12.0 255.255.252.0 10.36.27.154
          ip route 10.36.27.164 255.255.255.252 10.36.27.154
        ```
        <br>
     b. Water7<br>
        Jalankan command berikut pada cmd router Water7.<br>
        ```
          ip route 0.0.0.0 0.0.0.0 10.36.27.149			          #FOOSHA
          ip route 10.36.27.0 255.255.255.128 10.36.27.146	  #A1
          ip route 10.36.0.0 255.255.248.0 10.36.27.146		    #A4
        ```
        <br>
     c. Pucci<br>
        Jalankan command berikut pada cmd router Pucci.<br>
        ```
          ip route 0.0.0.0 0.0.0.0 10.36.27.145			          #WATER7
        ```
        <br>
     d. Guanhao<br>
        Jalankan command berikut pada cmd router Pucci.<br>
        ```
          ip route 0.0.0.0 0.0.0.0 10.36.27.149			          #FOOSHA
          ip route 10.36.27.128 255.255.255.240 10.36.24.2	  #A13
          ip route 10.36.26.0 255.255.255.0 10.36.27.158		  #A8
          ip route 10.36.12.0 255.255.252.0 10.36.27.158		  #A11
          ip route 10.36.27.164 255.255.255.252 10.36.27.158	#A15
        ```
        <br>
     e. Alabasta<br>
        Jalankan command berikut pada cmd router Alabasta.<br>
        ```
        ip route 0.0.0.0 0.0.0.0 10.36.24.1			            #GUANHAO
        ```
        <br>
     f. Oimo<br>
        Jalankan command berikut pada cmd router Oimo.<br>
        ```
        ip route 0.0.0.0 0.0.0.0 10.36.24.1			            #GUANHAO
        ip route 10.36.12.0 255.255.252.0 10.36.26.2		    #A11
        ```
        <br>
     g. Seastone<br>
        Jalankan command berikut pada cmd router Seastone.<br>
        ```
        ip route 0.0.0.0 0.0.0.0 10.36.26.1			            #OIMO
        ```
        
**3. VLSM Testing**<br>

## B. CIDR pada GNS3

**1. CIDR Subnetting**<br>
**2. CIDR Routing**<br>
**3. CIDR Testing**<br>
