package tugaspboteori;

import java.util.Scanner;

abstract class Penumpang{
    protected String nama;
    protected String noTiket;
    
    public Penumpang(String nama,String noTiket){
        this.nama = nama;
        this.noTiket = noTiket;
    }
    
    public abstract double hitungHargaTiket();
    
    public void tampilkanData(){
        System.out.println("Nama : "+nama);
        System.out.println("No Tiket : "+noTiket);
        System.out.println("Harga Tiket : Rp"+hitungHargaTiket());
    }
}

class PenumpangReguler extends Penumpang{
    PenumpangReguler(String nama,String noTiket){
        super(nama,noTiket);
    }
    
    public double hitungHargaTiket(){
        double hargabiasa = 25000;
        return hargabiasa;
    }
    
    public void tampilkanData(){
        System.out.println("Nama : "+nama);
        System.out.println("No Tiket : "+noTiket);
        System.out.println("Harga Tiket : Rp"+hitungHargaTiket());
    }
}

class PenumpangVIP extends Penumpang{
    PenumpangVIP(String nama,String noTiket){
        super(nama,noTiket);
    }
    
    public double hitungHargaTiket(){
        double hargavip = 50000;
        return hargavip;
    }
    
    public void tampilkanData(){
        System.out.println("Nama : "+nama);
        System.out.println("No Tiket : "+noTiket);
        System.out.println("Harga Tiket : Rp"+hitungHargaTiket());
    }
}

class InputPenumpang{
    protected Scanner input = new Scanner(System.in);
}

class main extends InputPenumpang {
    String nama, notiket;
    int pilih;

    public void jalankan() {
        System.out.println("=== Input Data Penumpang ===");
        System.out.print("Nama      : ");
        nama = input.nextLine();

        System.out.print("No Tiket  : ");
        notiket = input.nextLine();

        System.out.println("\nPilih Jenis Penumpang:");
        System.out.println("1. Reguler");
        System.out.println("2. VIP");
        System.out.print("Pilihan (1/2): ");
        pilih = input.nextInt();
        input.nextLine(); 
        
        Penumpang p;

        if (pilih == 1) {
            p = new PenumpangReguler(nama, notiket);
            System.out.println();
            p.tampilkanData();
        } else if (pilih == 2) {
            p = new PenumpangVIP(nama, notiket);
            System.out.println();
            p.tampilkanData();
        } else {
            System.out.println("Pilihan tidak valid!");
        }
    }
}

public class TugasPBOTeori {
    public static void main(String[] args) {
        main fit = new main();
        fit.jalankan();
    }
}
