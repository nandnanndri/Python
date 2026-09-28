# Spotify & YouTube Music Data Analysis 🎵

Feltáró adatelemzés (EDA) egy 20 000+ soros **Spotify + YouTube** zenei adathalmazon, `pandas`, `NumPy`, `matplotlib` és `seaborn` segítségével. A projekt célja az adattisztítás, hiányzóadat-kezelés, csoportos aggregálás, korrelációelemzés és vizualizáció bemutatása egy valós, hiányos és vegyes típusú adathalmazon.

## Tartalom

- [Az adathalmazról](#az-adathalmazról)
- [Használt eszközök](#használt-eszközök)
- [Mit csinál a notebook](#mit-csinál-a-notebook)
- [Futtatás](#futtatás)
- [Eredmények / kiemelt ábrák](#eredmények--kiemelt-ábrák)
- [Fájlstruktúra](#fájlstruktúra)

## Az adathalmazról

Az adathalmaz Spotify audio jellemzőket (pl. *danceability*, *energy*, *loudness*, *valence*, *tempo*) kapcsol össze a hozzájuk tartozó YouTube videó statisztikákkal (megtekintés, like, komment) és Spotify stream-számokkal. Összesen **~20 700 sor, 27 oszlop**.

## Használt eszközök

- **Python 3**
- **pandas** – adatbetöltés, tisztítás, csoportosítás, aggregáció
- **NumPy** – numerikus műveletek, típuskonverziók
- **matplotlib** / **seaborn** – vizualizáció (oszlopdiagram, boxplot, heatmap)

## Mit csinál a notebook

1. **Adatbetöltés és áttekintés** – `describe()`, `info()`, hiányzó értékek feltárása.
2. **Hiányzó adatok kezelése** – audio jellemzők (`Danceability`, `Energy`, `Loudness` stb.) hiányzó értékeinek pótlása **előadó szerinti csoportos átlaggal**, majd a maradék hiányos sorok eldobása.
3. **Típuskonverziók** – numerikus oszlopok `int`-té, logikai oszlopok valódi `bool`-lá alakítása; irreleváns oszlopok (`Url_spotify`, `Uri`) eltávolítása.
4. **Alap aggregációk** – legjobb *danceability* előadók, legtöbbet streamelt/nézett előadók (kettős tengelyes oszlopdiagram).
5. **Korrelációelemzés** – a top 10 legnépszerűbb dal audio jellemzőinek korrelációs hőtérképe.
6. **Kiegészítő elemzések:**
   - Hangulat (*Valence*) eloszlása albumtípus szerint (boxplot)
   - Hivatalos vs. nem hivatalos videók teljesítmény-összehasonlítása
   - Legenergikusabb / leghangosabb dalok rangsora
   - Licenszelt tartalom aránya és kapcsolata a stream-számmal
   - Hangnem (*Key*) eloszlás vizualizációja

## Futtatás

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook spotify_youtube_music_analysis.ipynb
```

A notebook egy `spotify_yt.csv` fájlt vár a gyökérmappában (Spotify + YouTube adathalmaz — pl. Kaggle-ről letölthető ["Spotify and YouTube" dataset](https://www.kaggle.com/)). A tisztított adatot a notebook `spotify_yt_cleaned.csv` néven exportálja.

## Eredmények / kiemelt ábrák

- **Top 10 streamelt előadó**: Post Malone, Ed Sheeran, Dua Lipa, XXXTENTACION és társaik vezetik a listát mind stream, mind YouTube megtekintés alapján.
- **Korreláció**: a *loudness* és *energy* jellemzők között erős pozitív korreláció figyelhető meg a legnépszerűbb számoknál.
- **Hangnem-eloszlás**: bizonyos hangnemek (pl. C#/Db, G) felülreprezentáltak a népszerű daloknál.

## Fájlstruktúra

```
.
├── spotify_youtube_music_analysis.ipynb   # Fő notebook (EDA + vizualizáció)
├── spotify_yt.csv                          # Bemeneti adathalmaz (nincs a repóban, külön letöltendő)
├── spotify_yt_cleaned.csv                  # Tisztított, exportált adathalmaz (a notebook generálja)
└── README.md
```

---

*Ez a projekt egyetemi adatelemzési feladat (data science beadandó) keretében készült, és portfólió célra lett kibővítve és dokumentálva.*
