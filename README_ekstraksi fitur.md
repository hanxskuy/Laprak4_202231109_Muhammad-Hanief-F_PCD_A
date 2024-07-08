
## Penjelasan Ekstraksi Fitur

### Import library 

```bash
import cv2
import matplotlib.pyplot as plt
import numpy as np
import skimage
from skimage.feature import graycomatrix, graycoprops
```
- cv2 digunakan untuk pemrosesan gambar.
- matplotlib.pyplot digunakan untuk visualisasi.
- numpy digunakan untuk manipulasi array.
- skimage adalah library untuk pemrosesan gambar.
- graycomatrix dan graycoprops digunakan untuk menghitung matriks ko-occurence dan proporsinya.

### Membaca dan mengkonversi gambar

```bash
img = skimage.data.rocket()  # Membaca gambar contoh dari skimage
img_hsv = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)  # Mengkonversi gambar dari RGB ke HSV
```
- skimage.data.rocket membaca gambar contoh (gambar roket).
- cv2.cvtColor mengkonversi gambar dari format RGB ke HSV.

### Menampilkan gambar RGB dan HSV

```bash
fig, axs = plt.subplots(1, 2, figsize=(10, 10))
ax = axs.ravel()

ax[0].imshow(img)
ax[0].set_title('RGB')
ax[1].imshow(img_hsv, cmap='hsv')
ax[1].set_title('HSV')
```
- plt.subplots membuat dua subplot dalam satu baris.
- ax[0].imshow menampilkan gambar RGB.
- ax[0].set_title memberikan judul pada subplot pertama.
- ax[1].imshow menampilkan gambar HSV.
- ax[1].set_title memberikan judul pada subplot kedua.

### Menghitung rata-rata dan standar deviasi dari gambar HSV

```bash
mean = np.mean(img_hsv.ravel())
std = np.std(img_hsv.ravel())
print("rata-rata : ", mean)
print("standar deviasi : ", std)
```

### Mendapatkan komponen Hue dan menghitung matriks ko-occurence

```bash
hue = img_hsv[0, :, :]
hue.shape

glmc = graycomatrix(hue, distances=[1], angles=[0], levels=256, symmetric=True, normed=True)

print(glmc)
```
- img_hsv[0, :, :] mengambil komponen Hue dari gambar HSV.
- graycomatrix menghitung matriks ko-occurence untuk komponen Hue dengan parameter yang ditentukan.
- print menampilkan matriks ko-occurence.

### Menghitung dan menampilkan proporsi dari matriks ko-occurence untuk komponen Hue

```bash
contrast = graycoprops(glmc, 'contrast')[0, 0]
dissimilarity = graycoprops(glmc, 'dissimilarity')[0, 0]
homogeneity = graycoprops(glmc, 'homogeneity')[0, 0]
energy = graycoprops(glmc, 'energy')[0, 0]
correlation = graycoprops(glmc, 'correlation')[0, 0]

print(f'contrast: {contrast}')
print(f'dissimilarity: {dissimilarity}')
print(f'homogeneity: {homogeneity}')
print(f'energy: {energy}')
print(f'correlation: {correlation}')
```
- graycoprops menghitung proporsi dari matriks ko-occurence (kontras, dissimilarity, homogenitas, energi, dan korelasi).
- print menampilkan nilai proporsi tersebut.

### Mendapatkan komponen Saturation dan menghitung matriks ko-occurence

```bash
saturation = img_hsv[:, 1, :]
saturation.shape

glmc = graycomatrix(saturation, distances=[1], angles=[0], levels=256, symmetric=True, normed=True)

print(glmc)
```
- img_hsv[:, 1, :] mengambil komponen Saturation dari gambar HSV.
- graycomatrix menghitung matriks ko-occurence untuk komponen Saturation dengan parameter yang ditentukan.
- print menampilkan matriks ko-occurence.

### Menghitung dan menampilkan proporsi dari matriks ko-occurence untuk komponen Saturation

```bash
contrast = graycoprops(glmc, 'contrast')[0, 0]
dissimilarity = graycoprops(glmc, 'dissimilarity')[0, 0]
homogeneity = graycoprops(glmc, 'homogeneity')[0, 0]
energy = graycoprops(glmc, 'energy')[0, 0]
correlation = graycoprops(glmc, 'correlation')[0, 0]

print(f'contrast: {contrast}')
print(f'dissimilarity: {dissimilarity}')
print(f'homogeneity: {homogeneity}')
print(f'energy: {energy}')
print(f'correlation: {correlation}')
```
- graycoprops menghitung proporsi dari matriks ko-occurence (kontras, dissimilarity, homogenitas, energi, dan korelasi).
- print menampilkan nilai proporsi tersebut.

### Mendapatkan komponen Value dan menghitung matriks ko-occurence

```bash
value = img_hsv[:, :, 2]
value.shape

glmc = graycomatrix(value, distances=[1], angles=[0], levels=256, symmetric=True, normed=True)

print(glmc)
```
- img_hsv[:, :, 2] mengambil komponen Value dari gambar HSV.
graycomatrix menghitung matriks ko-occurence untuk komponen Value dengan parameter yang ditentukan.
- print menampilkan matriks ko-occurence.

### Menghitung dan menampilkan proporsi dari matriks ko-occurence untuk komponen Value

```bash
contrast = graycoprops(glmc, 'contrast')[0, 0]
dissimilarity = graycoprops(glmc, 'dissimilarity')[0, 0]
homogeneity = graycoprops(glmc, 'homogeneity')[0, 0]
energy = graycoprops(glmc, 'energy')[0, 0]
correlation = graycoprops(glmc, 'correlation')[0, 0]

print(f'contrast: {contrast}')
print(f'dissimilarity: {dissimilarity}')
print(f'homogeneity: {homogeneity}')
print(f'energy: {energy}')
print(f'correlation: {correlation}')
```
- graycoprops menghitung proporsi dari matriks ko-occurence (kontras, dissimilarity, homogenitas, energi, dan korelasi).
- print menampilkan nilai proporsi tersebut.


