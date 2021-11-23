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
- [C. CIDR pada GNS3](#c-cidr-pada-gns3)
  - [1. CIDR Subnetting](#1-cidr-subnetting)
  - [2. CIDR Routing](#2-cidr-routing)

B. Kendala

- [Kendala](#kendala)

---

## A. Topologi

Pembagian IP menggunakan Prefix IP yang telah ditentukan pada modul pengenalan. Prefix IP Address kelompok E14 kami adalah `10.36`. <br>
![topologi](img/topologi.PNG)

## B. VLSM pada CPT

   **1. VLSM Subnetting**<br>
     Berdasarkan topologi, ditemukan 15 subnet termasuk subnet untuk server dan router. Polanya seperti yang terlihat pada gambar di bawah ini. Selain itu ditambahkan juga besar netmask dari subnet tersebut berdasarkan jumlah ip yang dibutuhkan masing-masing subnet.
     <br> 
     ![alt_text](img/vlsm-subnetting.PNG)
     <br>
     Pembagian IP menggunakan teknik VLSM memang tidak fleksible namun dalam pemakaian ip cukup efisien. Caranya terlihat seperti gambar di bawah ini.
     <br>
     ![alt_text](img/vlsm-ip-arr.PNG)<br>
   **2. VLSM Routing**<br>
     a. Foosha<br>
     Jalankan command berikut pada cmd router Foosha.
     
     ip route 10.36.27.0 255.255.255.128 10.36.27.150	    #A1
     ip route 10.36.16.0 255.255.252.0 10.36.27.150		    #A2
     ip route 10.36.0.0 255.255.248.0 10.36.27.150		    #A4
     ip route 10.36.20.0 255.255.252.0 10.36.27.154		    #A7
     ip route 10.36.24.0 255.255.254.0 10.36.27.154		    #A12
     ip route 10.36.27.128 255.255.255.240 10.36.27.154	    #A13
     ip route 10.36.26.0 255.255.255.0 10.36.27.154		    #A8
     ip route 10.36.12.0 255.255.252.0 10.36.27.154		    #A11
     ip route 10.36.27.164 255.255.255.252 10.36.27.154	    #A15
        
  b. Water7<br>
     Jalankan command berikut pada cmd router Water7.
        
     ip route 0.0.0.0 0.0.0.0 10.36.27.149			    #FOOSHA
     ip route 10.36.27.0 255.255.255.128 10.36.27.146	    #A1
     ip route 10.36.0.0 255.255.248.0 10.36.27.146		    #A4
        
        
  c. Pucci<br>
     Jalankan command berikut pada cmd router Pucci.<br>
     
     ip route 0.0.0.0 0.0.0.0 10.36.27.145			    #WATER7
     
        
  d. Guanhao<br>
        Jalankan command berikut pada cmd router Pucci.<br>
     
     ip route 0.0.0.0 0.0.0.0 10.36.27.149			    #FOOSHA
     ip route 10.36.27.128 255.255.255.240 10.36.24.2	    #A13
     ip route 10.36.26.0 255.255.255.0 10.36.27.158		    #A8
     ip route 10.36.12.0 255.255.252.0 10.36.27.158		    #A11
     ip route 10.36.27.164 255.255.255.252 10.36.27.158  	    #A15
     
        
  e. Alabasta<br>
     Jalankan command berikut pada cmd router Alabasta.<br>
    
     ip route 0.0.0.0 0.0.0.0 10.36.24.1			    #GUANHAO
    

  f. Oimo<br>
     Jalankan command berikut pada cmd router Oimo.<br>
    
     ip route 0.0.0.0 0.0.0.0 10.36.24.1			    #GUANHAO
     ip route 10.36.12.0 255.255.252.0 10.36.26.2		    #A11
     

  g. Seastone<br>
     Jalankan command berikut pada cmd router Seastone.<br>
     
     ip route 0.0.0.0 0.0.0.0 10.36.26.1			    #OIMO
    

## B. CIDR pada GNS3

   **1. CIDR Subnetting**<br>
         Berikut proses penggabungan subnet-subnet dari paling bawah pada topologi:
         ![langkah-1](img/CIDR/langkah-1.jpg)
         ![langkah-2](img/CIDR/langkah-2.jpg)
         ![langkah-3](img/CIDR/langkah-3.jpg)
         ![langkah-4](img/CIDR/langkah-4.jpg)
         ![langkah-5](img/CIDR/langkah-5.jpg)
         ![langkah-6](img/CIDR/langkah-6.jpg)
         ![langkah-7](img/CIDR/langkah-7.jpg)
         ![langkah-8](img/CIDR/langkah-8.jpg)
         ![langkah-9](img/CIDR/langkah-9.jpg)
         Dari pengelompokan subnet tersebut didapatkan subnet terbesar memiliki 15 bit, sehingga pohon pembagian IP dapat dibuat menjadi sebagai berikut:
         ![pohon](img/CIDR/pohon.jpg)
         Setelah didapatkan IP pada setiap subnet paling bawah, maka dicari netmask dan broadcast pada setiap subnet tersebut. Hasilnya sebagai berikut,
         <table>
            <thead>
               <tr>
                     <th  style="text-align: center;">Subnet</th>
                     <th  style="text-align: center;">Bit</th>
                     <th  style="text-align: center;">Network ID</th>
                     <th  style="text-align: center;">Netmask</th>
                     <th  style="text-align: center;">Broadcast Address</th>
               </tr>
            </thead>
            <tbody>
               <tr>
                     <td  style="text-align: center;">A1</td>
                     <td  style="text-align: center;">/25</td>
                     <td  style="text-align: center;">10.37.8.0</td>
                     <td  style="text-align: center;">255.255.255.128</td>
                     <td  style="text-align: center;">10.37.8.127</td>
               </tr>
                  <tr>
                     <td  style="text-align: center;">A2</td>
                     <td  style="text-align: center;">/22</td>
                     <td  style="text-align: center;">10.37.32.0</td>
                     <td  style="text-align: center;">255.255.255.0</td>
                     <td  style="text-align: center;">10.37.35.255</td>
               </tr>
                  <tr>
                     <td  style="text-align: center;">A3</td>
                     <td  style="text-align: center;">/30</td>
                     <td  style="text-align: center;">10.37.16.0</td>
                     <td  style="text-align: center;">255.255.255.252</td>
                     <td  style="text-align: center;">10.37.16.3</td>
               </tr>
                  <tr>
                     <td  style="text-align: center;">A4</td>
                     <td  style="text-align: center;">/21</td>
                     <td  style="text-align: center;">10.37.0.0</td>
                     <td  style="text-align: center;">255.255.248.0</td>
                     <td  style="text-align: center;">10.37.7.255</td>
               </tr>
                  <tr>
                     <td  style="text-align: center;">A5</td>
                     <td  style="text-align: center;">/22</td>
                     <td  style="text-align: center;">10.37.128.0</td>
                     <td  style="text-align: center;">255.255.252.0</td>
                     <td  style="text-align: center;">10.37.131.255</td>
               </tr>
                  <tr>
                     <td  style="text-align: center;">A6</td>
                     <td  style="text-align: center;">/30</td>
                     <td  style="text-align: center;">10.37.64.0</td>
                     <td  style="text-align: center;">255.255.255.252</td>
                     <td  style="text-align: center;">10.37.64.3</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A6</td>
                     <td  style="text-align: center;">/30</td>
                     <td  style="text-align: center;">10.37.64.0</td>
                     <td  style="text-align: center;">255.255.255.252</td>
                     <td  style="text-align: center;">10.37.64.3</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A7</td>
                     <td  style="text-align: center;">/22</td>
                     <td  style="text-align: center;">10.36.36.0</td>
                     <td  style="text-align: center;">255.255.252.0</td>
                     <td  style="text-align: center;">10.36.39.255</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A8</td>
                     <td  style="text-align: center;">/24</td>
                     <td  style="text-align: center;">10.36.4.0</td>
                     <td  style="text-align: center;">255.255.255.0</td>
                     <td  style="text-align: center;">10.36.4.255</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A9</td>
                     <td  style="text-align: center;">/22</td>
                     <td  style="text-align: center;">10.36.0.0</td>
                     <td  style="text-align: center;">255.255.252.0</td>
                     <td  style="text-align: center;">10.36.3.255</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A10</td>
                     <td  style="text-align: center;">/30</td>
                     <td  style="text-align: center;">10.36.64.0</td>
                     <td  style="text-align: center;">255.255.255.252</td>
                     <td  style="text-align: center;">10.36.64.3</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A11</td>
                     <td  style="text-align: center;">/30</td>
                     <td  style="text-align: center;">10.36.16.0</td>
                     <td  style="text-align: center;">255.255.255.252</td>
                     <td  style="text-align: center;">10.36.16.3</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A12</td>
                     <td  style="text-align: center;">/30</td>
                     <td  style="text-align: center;">10.36.128.0</td>
                     <td  style="text-align: center;">255.255.255.252</td>
                     <td  style="text-align: center;">10.36.128.3</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A13</td>
                     <td  style="text-align: center;">/23</td>
                     <td  style="text-align: center;">10.36.32.0</td>
                     <td  style="text-align: center;">255.255.254.0</td>
                     <td  style="text-align: center;">10.36.33.255</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A14</td>
                     <td  style="text-align: center;">/30</td>
                     <td  style="text-align: center;">10.36.8.0</td>
                     <td  style="text-align: center;">255.255.255.252</td>
                     <td  style="text-align: center;">10.36.8.3</td>
               </tr>
               <tr>
                     <td  style="text-align: center;">A15</td>
                     <td  style="text-align: center;">/28</td>
                     <td  style="text-align: center;">10.36.34.0</td>
                     <td  style="text-align: center;">255.255.255.240</td>
                     <td  style="text-align: center;">10.36.34.15</td>
               </tr>
            </tbody>
         </table>
**2. CIDR Routing**<br>
