# Branch ve PR politikası

## Çalışma akışı

Tek geliştirici + AI desteği için `main` bütünleştirme dalıdır. Küçük ve tek amaçlı değişiklikler `docs/<konu>`, `feat/<konu>`, `fix/<konu>` veya `chore/<konu>` gibi kısa ömürlü dallarda hazırlanır ve PR ile birleştirilir. Sürekli bir develop dalı zorunlu değildir. Public depolarda private kaynak, plan, sır veya müşteri verisi yayımlanmaz.

PR; sorun/sonuç, ilgili görev, kabul ölçütleri, gerçek doğrulama komutları ve sonuçları, inceleme bulguları, kalan risk ve geri dönüş yolunu içerir. Çalıştırılmayan kontrol başarılı gösterilmez. Uygulanmayan kontrolün nedeni yazılır.

## Tek geliştirici ve AI incelemesi

- GitHub tarafından zorunlu tutulan insan onay sayısı **0**. PR yazarı kendi PR'sine onay veremediği için ikinci bir insanı zorunlu kılan Code Owner veya son push onayı şartı kullanılmaz.
- PR açılması zorunlu çalışma yöntemidir; sıfır onay inceleme yapılmaması anlamına gelmez. AI/Ponytail Review sonucu PR gövdesine veya inceleme kaydına eklenir. Riskli değişikliklerde mevcutsa ayrı bir inceleme oturumu tercih edilir; bağımsız inceleme yapılmadıysa açıkça belirtilir.
- AI değerlendirmesi bağımsız insan onayı veya GitHub review oyu değildir. Yetkili insan sorumluluğu korunur; AI yalnız kullanıcının verdiği yetki kapsamında merge yapabilir.
- Açık inceleme görüşmeleri çözülür; kritik doğrulanmış sorunlar ve başarısız zorunlu kontroller giderilmeden merge yapılmaz. Yeni anlamlı değişiklikte ilgili inceleme ve testler yenilenir.

## Merge ve dal düzeni

- Tek merge yöntemi **squash**; commit başlığı PR başlığı, açıklaması PR gövdesidir.
- Merge sonrası kaynak dal otomatik silinir. Aktif ortak çalışma dalı varsa kalıcı dalı PR kaynağı olarak kullanma.
- `main` için force-push ve dal silme yasaktır. Geçmişi düzeltmek yerine revert PR hazırlanır.
- Günlük iş akışı için bypass aktörü tanımlanmaz. Yönetici, AI veya GitHub App bypass listesine eklenmez. Yönetici ayarları değiştirebildiğinden bu bir değiştirilemez güvenlik sınırı değildir.
- Acil değişiklik de küçük bir PR ile yapılır. Kural değişikliği gerekirse kapsamı, nedeni, eski ayar yedeği ve geri alma koşulu kayıt edilir; insan yetkisi olmadan koruma düşürülmez.

## Kontroller ve uygulama sınırı

Henüz ürün CI hattı veya güvenilir check adı olmadığı için required status check listesi boş bırakıldı. Var olmayan bir kontrol adı merge'i süresiz kilitlememelidir. İlk gerçek build/test iş akışı birkaç PR üzerinde doğrulandıktan sonra sabit ve benzersiz check adları korumaya eklenir; bu ayrı kabul adımıdır.

İmzalı commit, merge queue, zorunlu deployment ve otomatik ücretli AI review bu başlangıç politikasında yoktur. Yeni uygulama kodu, altyapı veya dağıtım başlatılmaz. PR merge yetkisi üretim dağıtımı yetkisi değildir; bir dala push GitOps dağıtımı tetikliyorsa önce hedef ve yetki kontrol edilir.

## Doğrulama ve bakım

Repository ayarları ile branch kuralları ayrı doğrulanır. Squash-only ayarı, doğrudan Git push işlemini tek başına engellemez. PR şablonu ve manuel inceleme de sunucu tarafı güvenlik kontrolü değildir. Plan/ekip/CI değiştiğinde politika yeniden değerlendirilir.

Kaynaklar: [GitHub rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets), [protected branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches).

## Bu depodaki uygulama

**Public / GitHub Free:** aktif repository ruleset'i `main` üzerinde PR zorunluluğu, sıfır zorunlu insan onayı, çözülmüş inceleme görüşmeleri, linear history, force-push ve dal silme engeli uygular. Bypass listesi boştur. Repository squash-only ve merge sonrası dal temizliği ayarları açıktır. AI inceleme kanıtı halen çalışma yöntemidir; GitHub tarafından ayrı bir AI onay kapısı olarak zorlanmaz.
