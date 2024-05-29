# USharp

USharp, Unreal Engine (4.23) için C# ile programlama imkanı sağlayan bir eklentidir.

Bu proje, çeşitli mono-ue kısımlarını adapte eder ve genel olarak benzerdir ancak Mono, .NET Framework ve .NET Core desteğine sahiptir. Kullanılan C++ kodu genellikle PInvoke yöntemleridir ve eşdeğer mono-ue arka uç kodu çoğunlukla [C# olarak yazılmıştır](https://github.com/pixeltris/USharp/tree/master/Managed/UnrealEngine.Runtime/UnrealEngine.Runtime/Internal).

_Bu proje şu anda çoğu kullanım senaryosu için kullanılabilir değil. Birçok hata ve eksik özellik bulunmaktadır. [Güncellemeler için yakında tekrar kontrol edin!](https://github.com/pixeltris/USharp/projects/2)_

Hızlı yardım / tartışma için gitter sohbet odasına katılın: [USharp Gitter Chat Room](https://gitter.im/USharp/Lobby)

- Serhat Çiftçi'nin katkılarıyla düzenlenmiş ve Türkçeleştirilmiştir. ❤️

## Özellikler

- Write C# using UObject exposed types (AActor, AGameMode, UActorComponent, etc). Define new UObject types and inherit existing ones. Exposed C# types can then be used in (or extended by) Blueprint.
- Access to [Unreal's reflection system](https://www.unrealengine.com/en-US/blog/unreal-property-system-reflection) (UClass, UFunction, UProperty, etc). 
- Hotreload
- Dynamically switch between .NET Framework, .NET Core and Mono for an improved debugging / runtime experience without having to reopen the editor
- Supports Windows, Mac and Linux

## Eklenti Kurulumu

[Eklentiyi nasıl kuracağınıza dair wiki'ye bakın](https://github.com/pixeltris/USharp/wiki/Plugin-Setup)

## Sorunlar / sakıncalar

- Bu proje, potansiyel olarak farklı C++ derleyicilerinde farklı davranabilecek birçok PInvoke işlevine bağlıdır. **Bu proje bazı hedef platformlarda çalışmayabilir.**
- Mono-ue gibi bu proje, çok miktarda üretilen kod ve IL dokuma bağımlılığına sahiptir. Performans için muhtemelen en iyisi değil ve her yerde büyük miktarda üretilmiş kod bulunmaktadır.
- Halihazırda dokunan IL'nin düzenle-ve-devam et hata ayıklamayı bozduğu görünmektedir (cecil ile ilgili bir sorun?)
- Şu anda yapılan aşırı derecede çok miktarda veri taşıma (struct'lar, koleksiyonlar (liste, harita, küme)) mevcuttur. Veri taşımanın, C# / native kod arasındaki önemsiz çağrılarda tüm koleksiyonların / struct'ların kopyalarını önlemek için yeniden tasarlanması gerekmektedir. Ayrıca delegelerin taşınması da yeniden tasarlanmalıdır (delegenin bir kopyası olarak referanslanması gibi çeşitli sorunlar bulunmaktadır).

---

**_Bu proje neden var? Bunun yerine neden bunlar mono-ue'ye katkı yapılmıyor?_** Başlangıçta bu proje sadece C# ile UObject sistemine erişim sağlamak için bir yol olarak düşünülmüş ve sonunda neredeyse mono-ue'nin bir kopyası olmuştur. Mono-ue'nin derleme süreleri / hata ayıklama süreci, Unreal hakkında çok az bilgiye sahip olarak katkıda bulunmayı zorlaştırdı.
