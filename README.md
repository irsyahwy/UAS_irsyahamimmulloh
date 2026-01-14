# UAS_irsyahamimmullohimport time

print('-------------------------------------------')
print(' Selamat datang di aplikasi pinjam GusPay ')
print('-------------------------------------------')

print('Sebelum melakukan pinjaman silakan masukan data diri')
nama = input('Nama        : ')
umur = input('Umur        : ')
hp = input('Nomor HP    : ')
pekerjaan = input('Pekerjaan  : ')
penghasilan = int(input('Penghasilan/Upah (Rp) : '))

print('\nSetelah kami melakukan pengecekan data', end="")
for i in range(5):
    time.sleep(1)
    print('.', end='', flush=True)

# ================= CEK KREDIT =================
if penghasilan < 2000000:
    print('\nMohon maaf data anda tidak lolos')
    print('Penghasilan belum mencukupi')
    print('Silakan kembali lain waktu')
    exit()
elif penghasilan == 2000000:
    print('\nData anda lolos dengan kredit standar')
else:
    print('\nKredit anda sangat bagus')

# ================= MENU UTAMA =================
while True:
    print('\n--------------------------------------------')
    print('1. Cek Limit')
    print('2. Cek Kredit')
    print('3. Ajukan Pinjaman')
    print('4. Pengembalian Pinjaman')
    print('5. Keluar')

    menu = int(input('Pilih menu (1-5): '))

    # ===== CEK LIMIT =====
    if menu == 1:
        print('\nMengecek limit pinjaman', end="")
        for i in range(5):
            time.sleep(1)
            print('.', end='', flush=True)

        if penghasilan == 2000000:
            limit = 500000
        elif 2000000 < penghasilan <= 5000000:
            limit = 5000000
        else:
            limit = 999999999

        print(f'\nLimit pinjaman anda: Rp {limit:,}')

    # ===== CEK KREDIT =====
    elif menu == 2:
        print('\nStatus kredit anda: AMAN')

    # ===== AJUKAN PINJAMAN =====
    elif menu == 3:
        print('\n===== AJUKAN PINJAMAN =====')
        narek = input('Nama Rekening     : ')
        rekening = input('No Rekening       : ')
        tempo = int(input('Tempo Pinjaman (bulan 1-12): '))
        nominal = int(input('Nominal Pinjaman (Rp): '))

        if tempo <= 6:
            bunga = 0.15
        else:
            bunga = 0.25

        total_bunga = nominal * bunga
        total_bayar = nominal + total_bunga

        print('\nMelakukan Transfer', end="")
        for i in range(5):
            time.sleep(1)
            print('.', end='', flush=True)

        print('\n----- RINCIAN PINJAMAN -----')
        print('Nama Rekening   :', narek)
        print('Nominal         : Rp', nominal)
        print('Tempo           :', tempo, 'bulan')
        print('Bunga           :', int(bunga*100), '%')
        print('Total Bunga     : Rp', int(total_bunga))
        print('Total Bayar     : Rp', int(total_bayar))

    # ===== PENGEMBALIAN PINJAMAN =====
    elif menu == 4:
        print('\n===== PENGEMBALIAN PINJAMAN =====')
        nama_peminjam = input('Nama Peminjam        : ')
        nominal = int(input('Jumlah Pinjaman (Rp) : '))
        tempo = int(input('Tempo Pinjaman (bulan): '))
        telat = int(input('Keterlambatan (hari) : '))

        if tempo <= 6:
            bunga = 0.15
        else:
            bunga = 0.25

        total_bunga = nominal * bunga
        denda = telat * 5000
        total_tagihan = nominal + total_bunga + denda

        print('\n------ RINCIAN TAGIHAN ------')
        print('Nama           :', nama_peminjam)
        print('Pinjaman       : Rp', nominal)
        print('Bunga          : Rp', int(total_bunga))
        print('Denda Telat    : Rp', denda)
        print('TOTAL BAYAR    : Rp', int(total_tagihan))

        bayar = int(input('\nMasukkan jumlah pembayaran (Rp): '))

        if bayar >= total_tagihan:
            print('\n✅ PEMBAYARAN BERHASIL')
            print('Status : LUNAS')
            print('Kembalian : Rp', bayar - total_tagihan)
        else:
            print('\n❌ PEMBAYARAN BELUM LUNAS')
            print('Sisa Tagihan : Rp', total_tagihan - bayar)

    # ===== KELUAR =====
    elif menu == 5:
        print('\nTerima kasih telah menggunakan GusPay')
        break

    else:
        print('\nMenu tidak tersedia')
