# Python3
# Selenium ilə Davamiyyət Məlumatlarını Yoxlamaq üçün README

Bu layihə `Selenium` və `BeautifulSoup` istifadə edərək tələbə məlumatlarının davamiyyətini yoxlamaq üçün hazırlanmış bir Python skriptidir. Skript istifadəçinin daxil etdiyi məlumatlar əsasında **sso.aztu.edu.az** saytına daxil olur, tələbə məlumatlarını çəkir və davamiyyət hesabatını ekranda göstərir.

## Tələblər
Bu skripti istifadə etməzdən əvvəl aşağıdakı alətlər və kitabxanalar qurulmalıdır:

### Proqram təminatı
- **Python 3.x** (Ən azı 3.7 versiyası tövsiyə olunur)
- **Google Chrome** brauzeri
- **ChromeDriver** (Google Chrome-un versiyasına uyğun)

### Python Kitabxanaları
- `selenium`
- `beautifulsoup4`

### Kitabxanaları Qurmaq
Aşağıdakı əmr vasitəsilə lazım olan kitabxanaları quraşdıra bilərsiniz:
```bash
pip install -r requirements.txt
```

### requirements.txt Faylı
Lazım olan kitabxanaları `requirements.txt` faylında qeyd edin:
```
selenium
beautifulsoup4
```

## Skriptin İşləmə Prinsipi

### Əsas Addımlar
1. **İstifadəçi adı və şifrə daxil edilir**: Skript işlədikdə istifadəçidən `sso.aztu.edu.az` saytına giriş üçün istifadəçi adı və şifrə tələb olunur.
2. **Sayta daxil olma**: `Selenium WebDriver` vasitəsilə sayt açılır və daxil edilmiş istifadəçi məlumatları ilə giriş edilir.
3. **Navigasiya**: Tələbə keçidi, fənlər bölməsi və davamiyyət səhifəsi ardıcıl olaraq açılır.
4. **Məlumatların Çəkilməsi**: `BeautifulSoup` istifadə edərək davamiyyət məlumatları çəkilir və formatlanır.
5. **Nəticələrin Çapı**: Skript davamiyyət məlumatlarını konsolda göstərir.

## İstifadə Qaydası

### Addım 1: Skripti Çalışdırmaq
Skripti çalışdırmaq üçün aşağıdakı əmri icra edin:
```bash
python skript_adı.py
```

### Addım 2: İstifadəçi adı və şifrəni daxil edin
Program işlədikdə istifadəçi adı və şifrə soruşulacaq:
```bash
İstifadəçi adınızı daxil edin: <istifadəçi adı>
Şifrənizi daxil edin: <şifrə>
```

### Addım 3: Davamiyyət məlumatlarını baxın
Skript məlumatları yüklədikdən sonra konsolda davamiyyət hesabatını formatlanmış şəkildə göstərir.

### Çıxış nümunəsi
```plaintext
Davamiyyət Məlumatları:
------------------------------
Tarix: 2024-12-01, Status: İştirak Edib
Tarix: 2024-12-05, Status: İştirak Etməyib
...
```

## Əsas Kodun İzahı

### Modullar
- `selenium`: Veb elementlərini tapmaq və idarə etmək üçün istifadə olunur.
- `beautifulsoup4`: HTML strukturundan məlumat çıxarmaq üçün istifadə olunur.

### Funksionallıqlar
1. **Giriş Formasını Doldurmaq**: `find_element` metodu istifadə edərək istifadəçi adı və şifrə daxil edilir.
2. **Düymələrin Kliklənməsi**: `WebDriverWait` ilə elementlərin yüklənməsi gözlənilir və `click()` metodu ilə kliklənir.
3. **HTML Parsinqi**: `BeautifulSoup` kitabxanası ilə HTML məzmunu analiz edilir və tələb olunan məlumatlar çıxarılır.

### Davamiyyət Məlumatlarının Çəkilməsi
Davamiyyət məlumatları aşağıdakı kod hissəsində tapılır:
```python
soup = BeautifulSoup(driver.page_source, 'html.parser')
dates = soup.find_all('font', {'style': 'font-size:11px;'})
attendance = soup.find_all('span', {'class': 'attend-label ie'})
```

## Problemlərin Həlli

### Ümumi Səhvlər və Həlləri
1. **ChromeDriver versiya uyğunsuzluğu**:
   - ChromeDriver-i Google Chrome-un versiyasına uyğun olaraq yeniləyin.
   - Versiyanı yoxlamaq üçün terminalda aşağıdakı əmri istifadə edin:
     ```bash
     chrome --version
     ```

2. **Element tapılmadı xətası**:
   - Saytın HTML strukturu dəyişmiş ola bilər. XPath-ları yenidən yoxlayın və uyğun düzəliş edin.

3. **Sayt çox yavaş yüklənir**:
   - Gözləmə müddətini artırmaq üçün aşağıdakı sətiri redaktə edin:
     ```python
     time.sleep(10)  # Müddəti artırın
     ```

## Təhlükəsizlik Tövsiyələri
- Heç vaxt skript daxilində istifadəçi adı və şifrə saxlamayın.
- Şifrəni təhlükəsiz yolla ötürməyə diqqət yetirin.
- Saytdan çəkilən məlumatları üçüncü tərəflərlə paylaşmayın.
