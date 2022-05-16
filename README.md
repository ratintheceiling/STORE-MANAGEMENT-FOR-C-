#include <iostream>		// library input output
#include <conio.h>		// _getch(), _getche(), clrscr()
#include <ctime>		// menampilkan waktu dan tanggal
#include <stdlib.h>		// operasi pembanding dan operasi konversi
#include <string>		// berfungsi untuk melakukan manipulasi string
#include <fstream>		// output teks
#include <algorithm>
#include <sstream>


using namespace std;

void pilihan();  // deklarasi
void cekdata();
void masukandata();
void tampilkandata();
void ubahdata();
void hapusdata();
void admin();
void superAdmin();

string pilihAdmin, pilihSuper;

int main()
{
	int no, totalharga, harga, beli, total, kembalian, bayar, a, b, harga1[50], harga2[50], jml[50];
	string nama[50];
	string pilih, produk;
	string ngulang;

	// Tampilan Awal / Home
pertama:
	system("cls");
	cout << endl;
	cout << "################################################################" << endl;
	cout << "#--------------------------------------------------------------#" << endl;
	cout << "#                       Warung Vestarya                        #" << endl;
	cout << "#--------------------------------------------------------------#" << endl;
	cout << "################################################################" << endl;
	cout << endl;
	cout << "Pilihan" << endl;
	cout << "[1] SuperAdmin " << endl;
	cout << "[2] Admin " << endl;
	cout << "[3] Customer " << endl;
	cout << "[4] Keluar" << endl;
	cout << endl << endl;
	cout << "Masukkan Pilihan : ";
	cin >> pilih;					// input pilihan menu   

	// pilihan 1. Masuk sebagai admin
	if (pilih == "1")
	{
		string passSuper;
		char ch, go;
		system("cls");
		cout << "-------------------------" << endl;
		cout << "Anda Login sebagai SuperAdmin" << endl;
		cout << "-------------------------" << endl << endl;
		cout << "Masukan Password = ";
		cin >> passSuper;

		cout << endl;
		if (passSuper == "12345678")			// password 1
		{
			cout << "\nPassword Anda Benar\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			cin.ignore();
			cin.get();
			superAdmin();			// program admin 
		}
		else if (passSuper == "20202028")	// password 2
		{
			cout << "\nPassword Anda Benar\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			cin.ignore();
			cin.get();
			superAdmin();
		}
		else if (passSuper == "20202020")	// password 3
		{
			cout << "\nPassword Anda Benar\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			cin.ignore();
			cin.get();
			superAdmin();
		}
		else
		{
			cout << "\nPassword Anda Salah\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			go = _getch();
			system("cls");
			goto pertama;
		}

		goto pertama;
	}

	if (pilih == "2")
	{
		string pass;
		char ch, go;
		system("cls");
		cout << "-------------------------" << endl;
		cout << "Anda Login sebagai Admin" << endl;
		cout << "-------------------------" << endl << endl;
		cout << "Masukan Password = ";
		cin >> pass;

		cout << endl;
		if (pass == "12345678")			// password 1
		{
			cout << "\nPassword Anda Benar\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			cin.ignore();
			cin.get();
			admin();			// program admin 
		}
		else if (pass == "20202028")	// password 2
		{
			cout << "\nPassword Anda Benar\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			cin.ignore();
			cin.get();
			admin();			// program admin 
		}
		else if (pass == "20202020")	// password 3
		{
			cout << "\nPassword Anda Benar\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			cin.ignore();
			cin.get();
			admin();			// program admin 
		}
		else
		{
			cout << "\nPassword Anda Salah\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			go = _getch();
			system("cls");
			goto pertama;
		}

		goto pertama;
	}

	// pilihan 2. Pembayaran
	else if (pilih == "3")
	{
		totalharga = 0;
		b = 0;
	ulang:
		system("cls");
		cout << "-----------------------" << endl;
		cout << "Menu Pemesanan" << endl;
		tampilkandata();
		cout << "-----------------------" << endl << endl;
		cout << "Masukkan Nama Produk : ";
		cin >> produk;
		nama[b] = produk;
		fstream data;
		string isi;
		data.open("data.txt", ios::in);

		do // pengulangan barang yang dibeli
		{
			getline(data, isi);
			getline(data, isi);
		} while (isi != produk);
		getline(data, isi);
		cout << " " << endl;
		cout << "Harga Produk :  " << isi << endl;
		data.close();
		harga = atoi(isi.c_str());
		harga1[b] = harga;
		cout << endl;
		cout << "Jumlah		: ";
		cin >> beli;
		jml[b] = beli;
		cout << endl;
		total = harga * beli;
		harga2[b] = total;
		b++;
		totalharga += total;

	awal2:
		cout << " " << endl; // pilihan tambah produk atau tidak
		cout << "Tambah Produk ? (y/n): ";
		cin >> ngulang;

		if (ngulang == "y" || ngulang == "Y")
		{
			goto ulang;
		}
		else if (ngulang == "n" || ngulang == "N")
		{
			cout << endl;
			cout << "------------------------" << endl;
			cout << "   Barang Yang Dibeli   " << endl;
			cout << "------------------------" << endl;
			for (a = 0; a < b; a++)
			{
				cout << nama[a] << "\t" << jml[a] << "\t" << harga1[a] << "\t" << harga2[a] << endl;
			}
			cout << " " << endl;
			cout << "Total Harga : Rp.  " << totalharga << endl;
			cout << endl;
			cout << "Bayar       : Rp.  ";
			cin >> bayar;
			cout << endl;
			kembalian = bayar - totalharga;
			// menampilkan waktu dan tanggal pada nota

			//time_t t;
			//time(&t);
			//char *tanggal = ctime(&t);
			system("cls");

			// Output Nota
			cout << "--------------------------------------------------------------" << endl;
			cout << "                                                              " << endl;
			cout << "                        RASING MART                           " << endl;
			cout << "                 JL. In AJA Dulu no. 1 YaKamuLah              " << endl;
			cout << "                                                              " << endl;
			cout << "--------------------------------------------------------------" << endl;
			//cout << "                       " << tanggal << "						 " << endl;
			cout << "--------------------------------------------------------------" << endl;
			cout << "Nama" << "\t" << "Jumlah Harga" << "\t" << "Total" << endl;

			for (a = 0; a < b; a++)
			{
				cout << nama[a] << "\t" << jml[a] << "\t" << harga1[a] << "\t" << harga2[a] << endl;
			}

			cout << endl;
			cout << "-----------------------------------------------------------------" << endl;
			cout << "   " << "\t" << "\t" << "Total     : Rp. " << "\t" << "\t" << totalharga << endl;
			cout << "   " << "\t" << "\t" << "Bayar     : Rp. " << "\t" << "\t" << bayar << endl;
			cout << "   " << "\t" << "\t" << "Kembali   : Rp. " << "\t" << kembalian << endl;
			cout << "-----------------------------------------------------------------" << endl << endl;
			cout << "                Terima Kasih Telah Membeli Di Toko Kami          " << endl;
			cout << "-----------------------------------------------------------------" << endl << endl;
			cout << endl;

			fstream data3; // menampilkan .txt struk pembelian
			data3.open("struk.txt", ios::trunc | ios::out);
			data3 << endl << endl;
			data3 << "===================================================" << endl;
			cout << "#                  Warung Vestarya                        #" << endl;
			data3 << "===================================================" << endl;
			//data3 << "                   " << tanggal << endl;
			data3 << "Nama       Jumlah        Harga          Total " << endl;

			for (a = 0; a < b; a++)
			{
				data3 << nama[a] << "\t" << "\t" << jml[a] << "\t" << harga1[a] << "\t" << "\t" << harga2[a] << endl;
			}
			data3 << "----------------------------------------------" << endl;
			data3 << endl;
			data3 << "\t" << "\t" << "\t" << "Total    Rp. " << "\t" << totalharga << endl;
			data3 << "\t" << "\t" << "\t" << "Tunai    Rp. " << "\t" << bayar << endl;
			data3 << "\t" << "\t" << "\t" << "Kembali  Rp. " << "\t" << kembalian << endl;
			data3 << endl;
			data3 << "----------------------------------------------" << endl << endl;
			data3 << "   Terima Kasih Telah Membeli Di Toko Kami    " << endl;
			data3 << "----------------------------------------------" << endl << endl;
			data3.close();
			a = _getch();
			system("cls");
			goto pertama;
		}
		else	
		{
			cout << "Input Invalid" << endl;
			goto awal2; 
		}
	}
	else if (pilih == "3")
	{ 
		goto akhir; 
	}
	else
	{
		system("cls");
		goto pertama;
	}
akhir:
	cout << "Terima Kasih" << endl;
	return 0;
}

void pilihan()
{
	string memilih;
	system("cls");
	cout << "--------------------------" << endl;
	cout << "Anda Login Sebagai Admin" << endl;
	cout << "--------------------------" << endl;
	cout << endl;
	cout << "Menu : " << endl;
	cout << "[1] Tambah Produk" << endl;
	cout << "[2] List Produk" << endl;
	cout << "[3] Ubah Produk" << endl;
	cout << "[4] Hapus Produk" << endl;
	cout << "[5] Keluar" << endl;
	cout << " " << endl;
	cout << "Masukan Pilihan : ";
	cin >> pilihAdmin;					//string
	/*stringstream milih(memilih);	//convert str ke int
	milih >> pilih;					//masukin hasil convert ke int
	return pilih;*/
}

void pilihanSuper()
{
	string memilihSuper;
	system("cls");
	cout << "--------------------------" << endl;
	cout << "Anda Login Sebagai SuperAdmin" << endl;
	cout << "--------------------------" << endl;
	cout << endl;
	cout << "Menu : " << endl;
	cout << "[1] Cek Hasil Penjualan" << endl;
	cout << "[2] Keluar" << endl;
	cout << " " << endl;
	cout << "Masukan Pilihan : ";
	cin >> pilihSuper;					//string
	/*stringstream milih(memilihSuper);	//convert str ke int
	milih >> pilih;					//masukin hasil convert ke int
	return pilih;*/
}

void masukandata()			// input nama produk dan harga
{
	fstream data;
	char lanjut;
	string isi;
	do
	{
		data.open("data.txt", ios::out | ios::app); // mengubah data inputan menjadi .txt
		cout << endl;
		getline(cin, isi);
		cout << "Nama Produk:";
		getline(cin, isi);
		data << '\n' + isi;
		cout << "Harga Produk:";
		getline(cin, isi);
		data << '\n' + isi;
		data.close();

	u:
		cout << "Apakah Ingin Menambahkan (y,n) ";
		cin >> lanjut;
	} while (lanjut == 'y');

	if (lanjut != 'y' && lanjut != 'n')
	{
		cout << "Masukan Pilihan Yang Tepat";
		cout << endl;
		goto u;
	}
}

void tampilkandata()		// menampilkan data .txt yang sudah diinputkan 
{
	fstream data;
	string isi;
	int no;
	data.open("data.txt", ios::in);
	getline(data, isi);
	no = 1;
	cout << "No " << '\t' << '\t';
	cout << "Produk: "  << '\t' << '\t';
	cout << "Harga: " << endl;
	do
	{
		getline(data, isi);
		cout << no++ << '\t' << '\t';
		cout << isi << '\t' << '\t';
		getline(data, isi);
		cout << isi << endl;
	} while (!data.eof());
	data.close();
}

void ubahdata()				// mengubah data produk yang sudah diinput
{
	fstream data, data2;
	int no, i;
	string isi;
	cout << "Pilih Barang : "; cin >> no;
	data2.open("data2.txt", ios::trunc | ios::out);
	data.open("data.txt", ios::in);
	getline(data, isi);
	for (i = 1; i < no; i++)
	{
		getline(data, isi);
		data2 << '\n' + isi;
		getline(data, isi);
		data2 << '\n' + isi;
	}
	cout << "No " << '\t' << '\t';
	cout << "Produk: " << '\t';
	cout << "Harga: " << endl;
	getline(data, isi);
	cout << no++ << '\t' << '\t';
	cout << isi << '\t' << '\t';
	getline(data, isi);
	cout << isi << endl;

	cout << "Nama Produk   : ";
	getline(cin, isi);
	getline(cin, isi);
	data2 << '\n' + isi;
	cout << "Harga Produk :";
	getline(cin, isi);
	data2 << '\n' + isi;

	while (!data.eof())
	{
		getline(data, isi);
		data2 << '\n' + isi;
		getline(data, isi);
		data2 << '\n' + isi;
	}
	data2.close();
	data.close();

	data2.open("data2.txt", ios::in);
	data.open("data.txt", ios::trunc | ios::out);
	getline(data2, isi);

	do
	{
		getline(data2, isi);
		data << '\n' + isi;
		getline(data2, isi);
		data << '\n' + isi;
	} while (!data2.eof());

	data2.close();
	data.close();
}

void hapusdata()			// menghapus data yang sudah diinput
{
	fstream data, data2;
	string isi;
	int no, i;
	cout << "Pilih Barang : "; cin >> no;
	data2.open("data2.txt", ios::trunc | ios::out);
	data.open("data.txt", ios::in);
	getline(data, isi);

	for (i = 1; i < no; i++)
	{
		getline(data, isi);
		data2 << '\n' + isi;
		getline(data, isi);
		data2 << '\n' + isi;
	}
	cout << endl;
	cout << "No    " << '\t' << '\t';
	cout << "Produk: " << '\t';
	cout << "Harga : " << endl;
	getline(data, isi);
	cout << no++ << '\t' << '\t';
	cout << isi << '\t' << '\t';
	getline(data, isi);
	cout << isi << endl;

	while (!data.eof())
	{
		getline(data, isi);
		data2 << '\n' + isi;
		getline(data, isi);
		data2 << '\n' + isi;
	}

	data2.close();
	data.close();

	data2.open("data2.txt", ios::in);
	data.open("data.txt", ios::trunc | ios::out);
	getline(data2, isi);
	do
	{
		getline(data2, isi);
		data << '\n' + isi;
		getline(data2, isi);
		data << '\n' + isi;
	} while (!data2.eof());

	data2.close();
	data.close();

	cout << "Produk telah dihapus" << endl;
}

void hasiljual()			// hasil jualan
{
	fstream data;
	string isi;
	int no;
	data.open("data.txt", ios::in);
	getline(data, isi);
	no = 1;
	cout << "No " << '\t' << '\t';
	cout << "Produk: " << '\t';
	cout << "Harga: " << endl;
	do
	{
		getline(data, isi);
		cout << no++ << '\t' << '\t';
		cout << isi << '\t' << '\t';
		getline(data, isi);
		cout << isi << endl;
	} while (!data.eof());
	data.close();
}

void admin()				// program masuk ke admin setelah dimasukan password 
{
	fstream data, data2;

ulang:

	int no;
	string salur, isi, datane, ulang;
	pilihan();

	if (pilihAdmin == "1") {
		system("cls");
		cout << "-------------------" << endl;
		cout << "   Tambah Produk" << endl;
		cout << "-------------------" << endl;
		masukandata();
		goto ulang;
	}

	if (pilihAdmin == "2") {
		system("cls");
		cout << "-------------------" << endl;
		cout << "     List Barang" << endl;
		cout << "-------------------" << endl;
		tampilkandata();
		cout << endl << "Tekan tombol apapun untuk kembali" << endl;
		no = _getch();
		goto ulang;
	}

	if (pilihAdmin == "3") {
		system("cls");
		cout << "-------------------" << endl;
		cout << "     Ubah Barang" << endl;
		cout << "-------------------" << endl;
		tampilkandata();
		ubahdata();
		cout << endl << "Ubah data berhasil" << endl;
		cout << "Tekan tombol apapun untuk kembali" << endl;
		no = _getch();
		goto ulang;
	}

	if (pilihAdmin == "4") {
		system("cls");
		cout << "-------------------" << endl;
		cout << "     Hapus Data" << endl;
		cout << "-------------------" << endl;
		tampilkandata();
		hapusdata();
		no = _getch();
		goto ulang;
	}
	if (pilihAdmin == "5") {
		system("cls");
		goto akhir;
	}
	else 
	{
		cout << "Input Invalid" << endl;
		cout << "Tekan tombol apapun untuk kembali" << endl;
		no = _getch();
		goto ulang;
	}
akhir:
	cout << endl;
}

void superAdmin()				// program masuk ke superadmin setelah dimasukan password 
{
	fstream data, data2;

ulang:

	int no;
	string salur, isi, datane, ulang;
	pilihanSuper();

	if (pilihSuper == "1") {
		system("cls");
		cout << "-------------------" << endl;
		cout << "  Hasil Penjualan  " << endl;
		cout << "-------------------" << endl;
		hasiljual();
		goto ulang;
	}

	if (pilihSuper == "2") {
		system("cls");
		goto akhir;
	}

	else 
	{
		cout << "Input Invalid" << endl;
		cout << "Tekan tombol apapun untuk kembali" << endl;
		no = _getch();
		goto ulang;
	}
akhir:
	cout << endl;
}
