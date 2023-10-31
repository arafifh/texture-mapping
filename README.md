﻿# **Texture Mapping - webGL**

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

![Img1](https://cdn.discordapp.com/attachments/1150687865420906517/1168784082826702939/Screenshot_1158.png?ex=65530600&is=65409100&hm=eaf1254d41c333735ac401c632afb16a3a2bf82ed732a2aa2655fde49bb8aade&)

![Img2](https://cdn.discordapp.com/attachments/1150687865420906517/1168784084118548480/Screenshot_1160.png?ex=65530600&is=65409100&hm=bbec28ec7c51f50c3f70e9ddf8b3b8c21d911157df105314c96727705f9523ca&)

![Img3](https://cdn.discordapp.com/attachments/1150687865420906517/1168784084546363393/Screenshot_1161.png?ex=65530600&is=65409100&hm=6bd6a66953d342fa6047891bef47f76af5d6aa88d6b8bc7995803dc32b6f1d9f&)

![Img4](https://cdn.discordapp.com/attachments/1150687865420906517/1168784367074685009/Screenshot_1162.png?ex=65530644&is=65409144&hm=a34a5177e92a18f840e0625c6aaa600cc4db36c90a6be79793538680b50992a4&)
