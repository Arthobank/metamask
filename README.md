# metamask
Proyek infura

Daftar
anataliocs
/
Memulai-Dengan-Infura
Publik
Memulai dengan Infura

Lisensi
 lisensi MIT
 12 bintang 3 garpu 
Kode
Masalah
Tarik permintaan
Tindakan
Proyek
Keamanan
Wawasan
anataliocs/Memulai-Dengan-Infura
Komitmen terbaru
@anataliocs
anataliocs
…
on Nov 24, 2022
Statistik Git
File
README.md
Memulai Proyek Sampel Infura
Contoh Proyek 1 - Kirim Transaksi
Contoh Proyek 2 - IPFS
Contoh Proyek 3 - Notifikasi
Contoh Proyek 4 - Mencetak NFT
Memulai dengan Artikel Infura

Jalankan Proyek Secara Lokal
1. Instalasi
Klon proyek

  git clone git@github.com:anataliocs/Getting-Started-With-Infura.git
Pergi ke direktori proyek

  cd Getting-Started-With-Infura
Instal dependensi

  yarn
2. Variabel Lingkungan
Buat file variabel lingkungan

  cp template.env .env
Anda harus mendaftar akun Infura dan membuat proyek Ethereum dan proyek IPFS.

Tambahkan ID dan Rahasia proyek Infura Anda ke .envfile.

Kami akan menggunakan testnet Goerli.

Instal dotenv:

npm i dotenv
Siapkan file .env Anda:


  # Send Transaction Variables
  NEXT_PUBLIC_WEB3_TEST_ETHEREUM_NETWORK=goerli
  NEXT_PUBLIC_WEB3_INFURA_API_KEY=[Your WEB3 Infura Project]

  # IPFS Variables
  NEXT_PUBLIC_INFURA_IPFS_ENDPOINT=https://ipfs.infura.io:5001
  NEXT_PUBLIC_INFURA_IPFS_PROJECT_ID=[Your IPFS Infura Project ID]
  NEXT_PUBLIC_INFURA_IPFS_PROJECT_SECRET=[Your IPFS Infura Project Secret]

  # Minting Variables
  WALLET_MNEMONIC=
  NEXT_PUBLIC_MINTING_INFURA_PROJECT_ID=[Your WEB3 Infura Project]
  NEXT_PUBLIC_SMART_CONTRACT_ADDRESS=[The hash of the deployed contract on goerli]
3. Jalankan Proyek
  yarn dev
Contoh Proyek 1 - Kirim Transaksi
Dalam proyek ini pengguna akan menghubungkan dompet MetaMask mereka, mengirim transaksi, dan kemudian meninjau transaksi, semuanya menggunakan API Infura .

1 - Danai Dompet Anda Dengan Testnet Ether
Di dompet MetaMask Anda, alihkan ke Goerli Test Network(Anda mungkin harus mengeklik "tampilkan/sembunyikan jaringan uji" dan alihkan pengaturan untuk melihat jaringan Goerli)

Buka https://faucet.paradigm.xyz/ , sambungkan dompet Anda, lalu minta pengiriman ETH uji ke akun Anda.

2 - Hubungkan Dompet
Buka http://localhost:3000/transaction/connect dan klikConnect Wallet

Di /api/balance.tskami menggunakan Infura API eth_getBalance untuk mendapatkan saldo ETH saat ini di akun dompet yang terhubung.

3 - Transfer ETH
Masukkan alamat dompet untuk dompet yang akan Anda transfer (Anda dapat membuat akun tambahan di dompet MetaMask Anda untuk dikirim )

Masukkan jumlah testnet Ether yang ingin Anda transfer (yaitu 0,001 ETH)

Hit Submitdan jika dompet Anda memiliki dana yang cukup, transaksi akan ditambang (Perhatikan bahwa transaksi mungkin memakan waktu cukup lama untuk diselesaikan, testnet seringkali agak lambat)

Saat transaksi ditambang, Anda akan melihat layar konfirmasi dengan transaction hash, salin hash ke clipboard untuk langkah selanjutnya

4 - Ulasan
Tempel hash transaksi Anda dari langkah sebelumnya dan klikReview

Anda kemudian harus melihat rincian transaksi.

Contoh Proyek 2 - Unggah ke IPFS
Dalam proyek ini, pengguna akan mengunggah gambar png/jpeg dan json metadata ke IPFS, kemudian menggunakan tokenURI untuk mengambil dan menampilkan gambar dan metadatanya.

1 - Siapkan variabel lingkungan
Tambahkan nilai dari dasbor Infura Anda untuk ketiga variabel lingkungan ini.

  # IPFS Variables
  NEXT_PUBLIC_INFURA_IPFS_ENDPOINT=
  NEXT_PUBLIC_INFURA_IPFS_PROJECT_ID=
  NEXT_PUBLIC_INFURA_IPFS_PROJECT_SECRET=
2 - Jalankan proyek
Catatan: Anda harus memulai ulang server proyek setelah menyimpan variabel lingkungan baru.

  yarn dev
3 - Unggah gambar
Gunakan formulir di /ipfs/upload untuk mengunggah gambar dan metadata ke IPFS. .pngdan .jpeggambar saat ini adalah satu-satunya format yang didukung.

Di bagian belakang unggahan ini, pertama-tama kita mengunggah gambar ke IPFS, lalu membuat objek json menggunakan metadata dan menambahkan hash IPFS dari gambar ke objek tersebut. Ini adalah format umum untuk NFT, dan objek json terlihat seperti ini setelah diunggah:

  {
    "name": "NFT Name",
    "description": "Description of NFT",
    "image": "<ipfs hash for image>",
    "attributes": [
      { "trait_type": "Color", "value": "Blue" },
      { "trait_type": "fileSize", "value": "71.4 KB" },
      { "trait_type": "fileType", "value": "image/png" },
      { "trait_type": "objectHash", "value": "<ipfs hash for this metadata object>" }
    ]
  }
Di layar sukses, salin hash IPFS.

4 - Tampilkan gambar Anda
Gunakan formulir di /ipfs/display untuk memasukkan hash IPFS yang Anda salin pada langkah sebelumnya dan klik submit.

Ini akan mengambil gambar Anda dan metadatanya dari IPFS dan menampilkannya.

Contoh Proyek 3 - Pemberitahuan Transaksi
Dalam proyek ini, Anda akan berlangganan alamat ETH dan menerima notifikasi untuk transaksi yang tertunda.

1 - Penyiapan proyek
Ikuti penyiapan aplikasi utama dan isi variabel env ini. Jaringan seharusnyagoerli

NEXT_PUBLIC_WEB3_TEST_ETHEREUM_NETWORK=goerli
NEXT_PUBLIC_WEB3_INFURA_API_KEY=[Your WEB3 Infura Project]
Instal dan atur akun Metamask, alihkan jaringan kegoerli

Instal dependensi proyek

yarn
Mulai aplikasi

yarn dev
Arahkan ke halaman demo Notifikasi

http://localhost:3000/notifications
2 - Hubungkan Dompet Metamask Anda
Klik mulai di Landasan notifikasi untuk dibawa ke layar koneksi.
Setelah dompet Anda terhubung, lanjutkan ke langkah 3
3 - Berlangganan ke Akun
Masukkan alamat ETH yang ingin Anda terima pemberitahuannya
Anda akan dibawa ke layar menunggu notifikasi yang akan terisi setelah transaksi ditemukan
4 - Kirim transaksi
Menggunakan Metamask atau Demo Kirim Transaksi (di tab baru), kirim transaksi ke alamat akun yang Anda masukkan di langkah 3.
5 - Terima pemberitahuan
Pada langkah peninjauan notifikasi, setelah transaksi terdeteksi, Anda akan melihat notifikasi terbaru terisi di halaman, serta semua notifikasi terbaru di bawah bel notifikasi di bagian atas.
Sample Project 4 - Mint an NFT
Dalam proyek ini, pengguna akan menerapkan kontrak cerdas menggunakan Truffle, mengunggah ke IPFS, dan membuat NFT.

1 - Dana dompet Anda
Di dompet MetaMask Anda, alihkan ke Goerli Test Network(Anda mungkin harus mengeklik "tampilkan/sembunyikan jaringan uji" dan alihkan pengaturan untuk melihat jaringan Goerli)

Go to https://faucet.paradigm.xyz/, connect your wallet, and then request the test ETH

2 - Terapkan Kontrak Cerdas
Install Truffle: yarn global add truffle

Truffle adalah lingkungan pengembangan, kerangka pengujian, dan pipa aset untuk blockchain menggunakan Ethereum Virtual Machine. Rangkaian alat Truffle cukup kuat, kita akan menggunakan kompilasi, penautan, penerapan, dan manajemen biner kontrak pintar bawaan Truffle.

The truffle project has already been initialized so you'll see contracts/, migrations/, and truffle-config.js already in the project structure.

Tambahkan mnemonik dompet Anda (frasa dua belas kata yang digunakan dompet untuk menghasilkan pasangan kunci publik/pribadi) dan ID proyek Infura Anda untuk proyek Ethereum (ini bisa menjadi ID proyek yang sama dengan Proyek Kirim Transaksi) ke variabel lingkungan Anda. Kami akan menggunakan jaringan goerli untuk contoh ini sehingga Anda dapat mempratinjau nft yang telah dicetak di OpenSea Testnets.

# Minting Variables
 WALLET_MNEMONIC=
 NEXT_PUBLIC_MINTING_INFURA_PROJECT_ID=[Your WEB3 Infura Project]
IMPORTANT: Be careful not to share or commit your wallet mnemonic, it can be used to access your wallet accounts and their contents.

In /contracts/NFTContract.sol you'll find a basic smart contract for minting NFTs. This contract uses OpenZeppelin - a trusted open-source library of Solidity smart contracts - to construct an ERC721 Token Contract. ERC721 is a token standard for representing ownership of non-fungible tokens (i.e. where each token is unique).

NFTContract.solBerikan koleksi NFT Anda nama dan simbol . Setiap NFT yang dicetak dengan kontrak ini akan memiliki nomor ID. Surat tokenCounterwasiat bertindak sebagai ID dan kontrak akan menambah penghitung saat NFT baru dicetak.

Di terminal Anda jalankan

truffle compile
Ini akan menambahkan build/folder ke struktur proyek (jangan hapus)

Migrasikan smart contract ke rantai dengan menjalankan

truffle migrate --network goerli
IMPORTANT: After your migration completes, copy the contract address in the cli output and add it to your environment variables

# Minting Variables
WALLET_MNEMONIC=
NEXT_PUBLIC_MINTING_INFURA_PROJECT_ID=
NEXT_PUBLIC_SMART_CONTRACT_ADDRESS=
3 - Mulai aplikasi
Di terminal Anda, jalankan

yarn dev
and go to http://localhost:3000/mint

4 - Unggah ke IPFS
Pilih file untuk NFT Anda dan beri nama, deskripsi, dan atribut (opsional), lalu klik UPLOADuntuk mengunggah metadata NFT ke IPFS.

Kunjungi dokumentasi IPFS di atas untuk detail lebih lanjut.

PENTING : Pastikan untuk menyalin tokenURI (hash IPFS) untuk objek yang diunggah.

5 - Mint
di http://localhost:3000/mint/minthalaman, tempel URI token yang Anda salin di langkah sebelumnya ke kolom input. Tekan kirim dan tunggu saat NFT Anda dicetak. Hasil akan ditampilkan saat proses selesai.

Anda dapat melihat koleksi Anda di OpenSea dengan mencari alamat kontrak di situs Testnet OpenSea.
