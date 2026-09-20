# Yapay zekâ: öküz bağlama yerleri

Yapay zekâ normalde taş ocağı başına en fazla 3 öküz bağlama yeri inşa eder. Ayrıca bir taş ocağı her inşa edildiğinde veya yeniden yapıldığında otomatik olarak bir bağlama yeri yerleştirir.

Bu otomatik bağlama yerleri, yapay zekânın konut kapasitesini doldurarak yeni köylülerin gelmesini engelleyebilir. Bu eklenti, bunları devre dışı bırakmanıza ve ek bağlama yerlerinin ne zaman inşa edileceğini ayarlamanıza olanak tanır.

**İlişkili bir öküz bağlama yeri**, işçisinin en son taş aldığı taş ocağına aittir. Bu ilişki sabit olmak yerine dinamik olarak güncellenir.

## Özellikler
- Taş ocağı başına 3’ten fazla öküz bağlama yerine izin verme
- Ek öküz bağlama yerlerinin inşasına ilişkin karar kurallarını özelleştirme
- Kuralları AIC üzerinden her yapay zekâ için ayrı ayrı özelleştirme

## AIC parametreleri

### `AIOxTethers_Logic`
0: Oyunun özgün mantığı.
1: Aşağıdaki sınırları ve taş yükü kurallarını kullanan dinamik mantık.

### `AIOxTethers_MaxOxTethers`
Oyuncu başına toplam öküz bağlama yeri sınırı.

### `AIOxTethers_DynamicMaxOxTethers`
Toplam öküz bağlama yeri sınırı = bu değer × taş ocağı sayısı.
Her zaman 2 toplam sınırdan düşük olanı geçerlidir.

### `AIOxTethers_ThresholdStoneLoad`
Bir taş ocağında `taş/ilişkili öküz bağlama yeri sayısı` bu değeri aşarsa sınırlar dâhilinde bir bağlama yeri daha inşa edilir. İlişkili bağlama yeri yoksa doğrudan taş miktarı kullanılır.

### `AIOxTethers_DisableInitialOxTether`
0: Taş ocağı her inşa edildiğinde veya yeniden yapıldığında otomatik olarak bir bağlama yeri yerleştirir.
1: Bu otomatik yerleştirmeyi devre dışı bırakır.

Bu ayar, dinamik mantıktan ve onun sınırlarından bağımsızdır.

### `AIOxTethers_MinimumOxTethersPerQuarry`
Bir taş ocağıyla ilişkili öküz bağlama yeri sayısı bu değerden azsa taş yüküne bakılmaksızın, toplam sınır dâhilinde bir tane daha inşa edilir.

### `AIOxTethers_MaximumOxTethersPerQuarry`
Taş yüküne göre bir taş ocağı için inşa edilen ilişkili öküz bağlama yerlerinin sınırı. Minimum bu sınırı aşmamalıdır.
