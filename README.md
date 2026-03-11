# simple-calculator
namespace BasitHesapMakinesi
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("--- Basit Hesap Makinesi ---");
            Console.WriteLine("Lütfen yapmak istediğiniz işlemi adım adım girin.\n");

            // Kullanıcıdan birinci sayıyı alıyoruz
            Console.Write("Birinci sayıyı girin: ");
            double sayi1;
            // Kullanıcının harf girmesi ihtimaline karşı basit bir kontrol yapılabilir ancak 
            // şimdilik en temel haliyle Convert kullanıyoruz.
            sayi1 = Convert.ToDouble(Console.ReadLine());

            // Kullanıcıdan işlem türünü alıyoruz
            Console.Write("İşlemi seçin (+, -, *, /): ");
            string islem = Console.ReadLine();

            // Kullanıcıdan ikinci sayıyı alıyoruz
            Console.Write("İkinci sayıyı girin: ");
            double sayi2 = Convert.ToDouble(Console.ReadLine());

            double sonuc = 0;
            bool islemBasarili = true;

            // Seçilen işleme göre hesaplamayı yapıyoruz
            switch (islem)
            {
                case "+":
                    sonuc = sayi1 + sayi2;
                    break;
                case "-":
                    sonuc = sayi1 - sayi2;
                    break;
                case "*":
                    sonuc = sayi1 * sayi2;
                    break;
                case "/":
                    // Sıfıra bölünme hatasını engelliyoruz
                    if (sayi2 != 0)
                    {
                        sonuc = sayi1 / sayi2;
                    }
                    else
                    {
                        Console.WriteLine("\nHata: Bir sayı sıfıra bölünemez!");
                        islemBasarili = false;
                    }
                    break;
                default:
                    Console.WriteLine("\nHata: Geçersiz bir işlem operatörü girdiniz.");
                    islemBasarili = false;
                    break;
            }

            // Eğer işlemde hata yoksa sonucu ekrana yazdırıyoruz
            if (islemBasarili)
            {
                Console.WriteLine($"\nSonuç: {sayi1} {islem} {sayi2} = {sonuc}");
            }

            Console.WriteLine("\nUygulamadan çıkmak için herhangi bir tuşa basın...");
            Console.ReadKey();
        }
    }
}
