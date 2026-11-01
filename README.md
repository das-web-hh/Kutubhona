# Kutubxona

Репозиторий с APK и автоматической распаковкой/пересборкой.

## Как получить пересобираемый проект

**Через GitHub Actions (без установки программ):**
1. Загрузите репозиторий на GitHub.
2. Вкладка **Actions** → **Decompile and rebuild APK** → **Run workflow**.
3. После завершения скачайте артефакты:
   - `decoded-project` — проект apktool (манифест, ресурсы, smali), можно править и собирать;
   - `java-sources` — Java-код от jadx, только для чтения;
   - `rebuilt-apk` — APK, пересобранный из `decoded-project`.

**Локально:**
```
java -jar apktool.jar d Kutubxona_1.apk -o decoded
# правки в decoded/
java -jar apktool.jar b decoded -o new.apk
```
Затем выровняйте (`zipalign`) и подпишите (`apksigner`) APK.

## Ограничения
Из APK нельзя восстановить оригинальные исходники (Kotlin/Java, Gradle-проект). Apktool даёт smali и ресурсы; код jadx даёт для чтения, но не для сборки.
