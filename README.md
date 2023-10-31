# **Texture Mapping - webGL**

<div align=justify>

Berikut adalah Repository untuk pengerjaan Texture Mapping mata kuliah Grafika Komputer yang berisi _source code_, dokumentasi atau penjelasan, dan _screenshot output_.

# **Identitas**

Ahmad Rafif Hikmatiar
<br>
5025211247

# **Texture Mapping**

Berikut adalah dokumentasi serta _screenshot output_ dari code yang ada untuk pembuatan kubus dengan setiap sisinya berupa gambar.

## **Penjelasan**

Fungsi yang diubah dalam _file_ `index.html` fungsi `initGL()`.

```js
let img = [];
for (let i = 0; i < 6; i++) {
  img[i] = new Image();
  img[i].onload = function () {
    textureObjects[i] = gl.createTexture();
    gl.bindTexture(gl.TEXTURE_2D, textureObjects[i]);
    gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA, gl.UNSIGNED_BYTE, img[i]);
    gl.generateMipmap(gl.TEXTURE_2D);
    if (i === 5) draw();
  };
  img[i].src = textureURLs[i];
}
```

Dalam potongan kode di atas, terdapat sebuah array yang disebut img, yang digunakan untuk menyimpan gambar-gambar. Gambar-gambar ini diubah menjadi tekstur agar bisa digunakan dalam lingkungan WebGL. Setelah semua gambar dimuat, fungsi draw dipanggil untuk memulai menggambar objek 3D. Oleh karena itu, dilakukan loop sebanyak enam kali karena ada enam sisi gambar yang harus dimuat.

Pada setiap iterasi loop, sebuah objek gambar baru dibuat dan dilengkapi dengan penangan acara (event handler). Ketika gambar telah selesai dimuat, objek tekstur WebGL diciptakan dan dihubungkan dengan gambar tersebut. Setelah keenam sisi diinisialisasi sebagai tekstur WebGL, fungsi draw dipanggil untuk memulai proses menggambar objek 3D sesuai dengan tekstur yang telah dimuat.

Fungsi yang diubah dalam _file_ `index.html` fungsi `draw()`.

```js
drawSquare(textureObjects[0]); //Front
mat4.rotateY(modelview, modelview, 0.5 * Math.PI);
drawSquare(textureObjects[1]); //Right
mat4.rotateY(modelview, modelview, 0.5 * Math.PI);
drawSquare(textureObjects[2]); //Back
mat4.rotateY(modelview, modelview, 0.5 * Math.PI);
drawSquare(textureObjects[3]); //Left
mat4.rotateY(modelview, modelview, 0.5 * Math.PI);
mat4.rotateX(modelview, modelview, 0.5 * -Math.PI);
drawSquare(textureObjects[4]); //Top
mat4.rotateX(modelview, modelview, Math.PI);
drawSquare(textureObjects[5]); //Bottom
```

Dalam potongan kode tersebut, fungsi drawSquare dipanggil enam kali, sesuai dengan jumlah sisi kubus. Sebelum pemanggilan fungsi tersebut, terjadi rotasi pada modelview matrix agar sesuai dengan sisi kubus yang akan diberikan gambar. Untuk sisi bagian atas dan bawah, terjadi rotasi pada sumbu X, sementara untuk sisi lainnya hanya terjadi rotasi pada sumbu Y.

## **_Screenshot Ouput_**

Berikut adalah _Screenshot output_ dari perubahan code tersebut:

<img width="1532" alt="Screenshot 2023-10-31 at 14 11 42" src="https://github.com/arafifh/texture-mapping/assets/89500557/c8953e35-c16d-4a4e-892e-f9c3ceca4eae">
<img width="1532" alt="Screenshot 2023-10-31 at 14 11 50" src="https://github.com/arafifh/texture-mapping/assets/89500557/2a744a07-2ab4-418f-ba21-efc70527e50b">
<img width="1532" alt="Screenshot 2023-10-31 at 14 11 58" src="https://github.com/arafifh/texture-mapping/assets/89500557/e680d117-d9cf-4466-b5da-6a199c44425e">
