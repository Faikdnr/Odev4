using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Odev3.LabOdevi
{
    //Öğrenci
    class LabOdevleri
    {
        static ArrayList ogr = new ArrayList();
        public static void Islemler()
        {

            while (true)
            {
                Console.WriteLine("İşlemler");
                Console.WriteLine("#########");
                Console.WriteLine("1-Ögrenci ekle");
                Console.WriteLine("2-Ögrenci sil");
                Console.WriteLine("3-Tüm ögrencileri listele");
                Console.WriteLine("4-Kayıtlı öğrencilerin sayısı");
                Console.WriteLine("5-Genel not ortalamasını hesapla");
                Console.WriteLine("0-Çıkış");

                Console.Write("Seçiniz: ");
                byte i = Convert.ToByte(Console.ReadLine());
                if (i == 0) { break; }
                switch (i)
                {
                    case 1:
                        OgrenciEkle();
                        break;
                    case 2:
                        OgrSil();
                        break;
                    case 3:
                        OgrList();
                        break;
                    case 4:
                        OgrSayisi();
                        break;
                    case 5:
                        OgrNotOrt();
                        break;
                    default:
                        Console.WriteLine("Geçerli bir deger girin");
                        break;
                }
            }
            
        }
        private static void OgrenciEkle()
        {
            Console.Write("Numara = ");
            int num = Convert.ToInt32(Console.ReadLine());
            Console.Write("Ad = ");
            string ad = Console.ReadLine();
            Console.Write("Soyad = ");
            string soyad = Console.ReadLine();
            Console.Write("Not = ");
            int not = Convert.ToInt32(Console.ReadLine());
            Ogrenci ogrt = new Ogrenci(num,ad,soyad,not);
            ogr.Add(ogrt);
        }

        private static void OgrList()
        {
            int i = 1;
            foreach (Ogrenci a in ogr)
            {
                Console.WriteLine($"{i}- Numara-{a.Numara}-Ad-{a.Ad}-Soyad-{a.Soyad}-Not-{a.Not}");
                i++;
            }
            Console.ReadLine();
        }
        private static void OgrSil()
        {
            Console.Write("Numara = ");
            int num = Convert.ToInt32(Console.ReadLine());
            foreach(Ogrenci o in ogr)
            {
                if(o.Numara == num)
                {
                    ogr.Remove(o);
                }
                else
                {
                    Console.WriteLine("Girilen birisi yok");
                }
            }
        }
        private static void OgrSayisi()
        {
            Console.WriteLine(ogr.Count);
        }

        private static void OgrNotOrt()
        {
            double ort = 0;
            foreach(Ogrenci o in ogr)
            {
                ort += o.Not;
            }
            double ortlama = ort / ogr.Count;
            Console.WriteLine($"Ortalama = {ortlama}");
        }
    }

    public struct Ogrenci
    {
        public int Numara;
        public string  Ad;
        public string Soyad;
        public int Not;

        public Ogrenci(int num, string ad, string soyad, int not)
        {
            Numara = num;
            Ad = ad;
            Soyad = soyad;
            Not = not;
        }
    }
}
