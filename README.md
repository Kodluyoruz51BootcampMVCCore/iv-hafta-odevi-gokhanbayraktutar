# iv-hafta-odevi
*  Geri dönen bilgiye göre yeşil renkte onay mesajı gösterilmesi. (örneğin:view bag)

*  AddMVC - AddMVCCore - AddDateAnnotations nedir? Nerelerde eklenmelidir?

 * Shanpshot nedir? nasıl değişir? neden alınır?

*  Jquery Calender--> [Datapicker](https://jqueryui.com/datepicker/) --> DueAt'i takvim tipinde eklemek nasıl yapılır? Araştırınız. (DateTimeUffset tipinden atamalar oluşucak)

*  First- FirstOrDefault ve Single- SingleOrDefault nedir? Aralarındaki farkı araştırınız.

*  En kısa null check nasıl yapılır?

* partial view nedir?

* Farklı authentication bulup,aynı işleri farklı yollar ile yapanları araştırınız.

* Ödev- Razor Pages/MVC Projects karşılaştırmasını yapınız.



# AddMVC – AddMVCCore

Asp.Net Core MVC özelliğini/hizmetini projede kullanmak için AddMvc eğer Core özelliğini kullanmak istersek Startup classının içine;
services.AddMvc();
services.AddMvcCore();   metotları eklenmelidir.

# Data Annotations Nedir?
MVC uygulamasında veri tabanı tablolarını Code First yöntemi ile oluşturmaya başladığımızda yapılan validasyon işlemlerine Data Annotations denir. 
(https://docs.microsoft.com/tr-tr/ef/ef6/modeling/code-frst/data-annotations)
(https://medium.com/@ibrahimcobani/entity-framework-dataannotations-c26a3c16fd09)

# Shanpshot nedir? nasıl değişir? neden alınır?

(https://softdevpractice.com/blog/entity-framework-core-snapshot/)

# First- FirstOrDefault ve Single- SingleOrDefault nedir?

LINQ sorgularında kullanılar Single, SingleOrDefault, First ve FirstOrDefault extension metodları bulunmaktadır. Bu metodların birbirlerinden farkları mevcuttur, bunları inceleyelim;
//int tipinde bir dizimiz olduğunu varsayalım.
int[] oddNumbers = { 1, 3, 5, 7, 11}; 
SingleOrDefault: Eğer dizi içinden sadece bir tane sayı seçmek istiyorsak ve seçim şartımız sağlanmıyorsa, bu durumda int tipinin varsayılan değeri olan 0(sıfır) döndürülsün istiyorsak SingleOrDefault seçimini kullanmalıyız. Eğer seçim sonucunda birden fazla değer dönerse InvalidOperationException fırlatılacaktır.

Single: Eğer seçimimiz sonucunda sadece bir tane eleman geleceği kesin ise, bu durumda Single seçimini kullanabiliriz. Eğer şartımızı sağlayan hiçbir eleman dönmezse veya şartımızı sağlayan birden fazla eleman dönerse, bu iki durumda da istisnalar fırlatılacak ve hata ile karşılaşmış olacağız.

First: Dönen sonuçlardan ilkini getirir yoksa hata verir.
FirstOrDefault: Bu seçimde de mantık SingleOrDefault ile aynıdır. Ancak bu seçimde istenen şartta ilk eleman seçilir. Örneğin dizinin ilk elemanı, dizinin 2’den büyük ilk elemanı gibi.

# En kısa null check nasıl yapılır?

Projelerimizde sıklıkla, değeri null olan değişkenler üzerinden işlem yapmaya çalışıp hatalar alırız. Bu hataların önüne geçebilmek için yine sıklıkla değişkenlerimizin null olup olmadığını kontrol etmemiz gerekir. C# dilinde bir değerin null olup olmadığını kontrol etmenin birden fazla yolu var. Bence en pratik ve kod kirliliği yaratmayan yöntem ise "??" operatörünü kullanmak.
     Kod örneği 1 :     
private void btnClick_Click(object sender, EventArgs e)
{
    string text = null;
    if (text == null)
    {
        MessageBox.Show("Null değer");
    }
    else
    {
        MessageBox.Show(text);
    }
}
    
    Kod örneği 2 :     
private void btnClick_Click(object sender, EventArgs e)
{
    string text = null;
    MessageBox.Show(text ?? "Null değer");
}
     Yukarıdaki 2 kod örneği tamamen aynı işi yapıyor. text isimli string değişkenin null olup olmadığı kontrol ediliyor; eğer null ise "Null değer" şeklinde bir messagebox gösteriliyor. Eğer null değilse string değişkenin kendisini messageboxta gösteriyoruz. Ancak ikinci örnekte işlem çok daha kısa ve kod okunurluğu yüksek. "??" operatörü kendisinin solundaki değerin null olup olmadığını kontrol eder. Eğer null değilse solundaki değeri; null ise sağındaki değeri döndürür.

# Partial view nedir?

Birden fazla yerde kullanılabilecek sayfaları Partial sayfa olarak oluşturup ilgili alana eklenmesi ile çalışan bir yapıdır. Partial view kullanımı için incelediğim kaynak;
(http://cagatayyildiz.com/mvc-partial-view-kullanimi/)

# Razor Pages/MVC Projects karşılaştırması

Razor Pages, asp.net core 2 ile birlikte gelen yeni bir özelliktir. Razor Pages, sayfa bazlı senaryolar için bildiğimiz mvc (model view controller)’a göre daha kolay uygulama geliştirmeyi sağlayan bir platformdur. Frontend çatılarda kullanılan yaklaşım olan mvvm (model view view model) yapısına benzeşen çift yönlü bağlantı (two way binding) özelliğini desteklemektedir.

Razor Pages’in tek sorumluluk prensibine (single responsibility) uygun bir yaklaşımı var. Öncelikle basit bir html sayfa geliştirmek için daha az dosya kullanılıyor ve dosya hiyerarşisi daha basit. Bildiğiniz gibi genel olarak dotnet web uygulaması geliştirmek için kullandığımız asp.net mvc çatısında controller’in içerisinde pek çok sayfa ile ilgili actionlar vardı. Controller’a bağlı tüm sayfaların actionlarını tek bir dosyada tutuyorduk. Bu durumda controller dosyası büyüyor böylece kodun okunurluğu azalıyor ve mental bir karmaşa yaratıyordu. Çok sayfalı web uygulamaları için bu bir handikap aslında.Razor Pages bu yönüyle bir avantaj sağlıyor. Mvc yapısı üzerinde geliştirildiği için, mvc de var olan herşeyi destekliyor. (Routing, ModelState vs…). Sözkonusu yapı bize daha önce webforms’ta olup ta istemediğimiz viewstate gibi yapılardan arındırılmış, kompakt bir dosya hiyerarşisi ile birlikte hızlı ve pratik uygulama geliştirmeye yönelik bir çatı sunuyor.

Razor Pages’i mvc ile karşılaştıracak olursak, sayfa ile ilgili olmak kaydıyla controller ve model (viewmodel) objesinin PageModel’e dönüşmüş hali diyebiliriz.







