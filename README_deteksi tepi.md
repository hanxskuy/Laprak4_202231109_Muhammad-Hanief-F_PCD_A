
## Penjelasan Deteksi Tepi

### Import library

```bash
import numpy as np 
import cv2 
import matplotlib.pyplot as plt
%matplotlib inline
import skimage
```
- numpy digunakan untuk manipulasi array.
- cv2 adalah library OpenCV untuk pemrosesan gambar.
- matplotlib.pyplot digunakan untuk visualisasi.
- %matplotlib inline digunakan untuk menampilkan plot langsung di notebook.
- skimage adalah library tambahan untuk pemrosesan gambar.

### Membaca dan menampilkan gambar asli

```bash
parkiran = cv2.imread("1.jpg")

cv2.imshow("gambar parkir", parkiran)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
- cv2.imread membaca gambar dari file "1.jpg".
- cv2.imshow menampilkan gambar dengan jendela bernama "gambar parkir".
- cv2.waitKey(0) menunggu tombol ditekan untuk menutup jendela.
- cv2.destroyAllWindows() menutup semua jendela OpenCV.

### Mengubah gambar menjadi grayscale dan mendeteksi tepi

```bash
gray = cv2.cvtColor(parkiran, cv2.COLOR_BGR2GRAY)
edges= cv2.Canny(parkiran,100,150) 
```
- cv2.cvtColor mengubah gambar dari format BGR (standar OpenCV) ke grayscale.
- cv2.Canny mendeteksi tepi pada gambar dengan batas bawah 100 dan batas atas 150.

### Menampilkan gambar asli dan hasil deteksi tepi menggunakan matplotlib

```bash
fig, axs = plt.subplots(1, 2, figsize=(10, 10))
ax = axs.ravel()

axs[0].imshow(gray, cmap="gray")
axs[0].set_title("gambar asli")

axs[1].imshow(edges, cmap="gray")
axs[1].set_title("gambar hasil deteksi")
```
- plt.subplots membuat dua subplot dalam satu baris.
- axs[0].imshow menampilkan gambar grayscale.
- axs[0].set_title memberikan judul pada subplot pertama.
- axs[1].imshow menampilkan gambar hasil deteksi tepi.
- axs[1].set_title memberikan judul pada subplot kedua.

### Mendeteksi garis menggunakan Hough Transform dan menggambar garis pada gambar asli

```bash
lines = cv2.HoughLinesP(edges, 1, np.pi/180, 20, maxLineGap=5)
image_line = parkiran.copy()

for line in lines:
    x1, y1, x2, y2 = line[0]
    cv2.line(image_line, (x1, y1), (x2, y2), (100, 8, 255), 3)
```
- cv2.HoughLinesP mendeteksi garis pada gambar tepi dengan parameter yang ditentukan.
- parkiran.copy() membuat salinan gambar asli.
- cv2.line menggambar garis pada salinan gambar asli dengan warna (100, 8, 255) dan ketebalan 3 piksel.

### Menampilkan gambar asli dan gambar dengan garis yang terdeteksi menggunakan matplotlib

```bash
fig, axs = plt.subplots(1, 2, figsize=(10, 10))
ax = axs.ravel()

axs[0].imshow(gray, cmap="gray")
axs[0].set_title("gambar asli")

axs[1].imshow(image_line, cmap="gray")
axs[1].set_title("gambar setelah")
```
- plt.subplots membuat dua subplot dalam satu baris.
- axs[0].imshow menampilkan gambar grayscale.
- axs[0].set_title memberikan judul pada subplot pertama.
- axs[1].imshow menampilkan gambar dengan garis yang terdeteksi.
- axs[1].set_title memberikan judul pada subplot kedua.
