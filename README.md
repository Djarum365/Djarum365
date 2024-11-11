
 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Img Txt Ovrly</title>
    <style>
        body {
            background-image: url('https://imgur.com/nX2N6sn.jpeg');
            background-size: cover;
            background-repeat: no-repeat;
            background-attachment: fixed;
            color: white;
            font-family: 'Arial Black', sans-serif;
        }
        #a {
            text-align: center;
            margin-top: 30px;
            padding: 20px;
            border-radius: 10px;
        }
        .b {
            margin-bottom: 20px;
            display: block;
            margin: 10px auto;
            width: 80%;
            padding: 10px;
            font-size: 16px;
            background: rgba(255, 255, 255, 0.8);
            border: none;
            border-radius: 5px;
        }
        #c {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
            background: rgba(255, 255, 255, 0.8);
            border: none;
            border-radius: 5px;
        }
        #d {
            border: 1px solid black;
            margin-top: 20px;
        }
        #resultText {
            margin-top: 20px;
            padding: 20px;
            background: rgba(0, 0, 0, 0.8);
            border-radius: 10px;
            color: white;
            text-align: left;
            width: 80%;
            margin: 20px auto;
            font-size: 16px;
            line-height: 1.6;
        }
        #marqueeContainer {
            margin-bottom: 10px;
        }
        .marquee {
            color: white;
            font-size: 20px;
            font-weight: bold;
        }
        #o {
            margin-bottom: 10px;
            padding: 10px 20px;
            font-size: 18px; /* Perbesar ukuran font */
            cursor: pointer;
            background: rgba(255, 255, 255, 0.8);
            border: none;
            border-radius: 5px;
        }
    </style>
</head>
<body>

<div id="marqueeContainer">
    <marquee class="marquee" behavior="scroll" direction="left"> Jika ada link yang tidak bisa diakses, mohon diganti manual terlebih dahulu pada saat ingin post ya guys ^^ </marquee>
</div>

<div id="a">
    <input type="text" class="b" id="h" placeholder="Tanggal" />
    <input type="text" class="b" id="i" placeholder="PRIZE 1" />
    <input type="text" class="b" id="k" placeholder="PRIZE 2" />
    <input type="text" class="b" id="m" placeholder="PRIZE 3" />
    <input type="text" class="b" id="j" placeholder="Masukkan Shio Dengan Huruf Kapital Semua" />
    <button id="o">SUBMIT</button>
    <br>
    <canvas id="p" width="600" height="600"></canvas>
    <div id="resultText"></div> <!-- Menambahkan div untuk teks hasil di bawah kanvas -->
</div>

<script>
    const q = 'https://imgur.com/rffAzOK.jpeg';
    const r = document.getElementById('p');
    const s = r.getContext('2d');
    const t = document.getElementById('h');
    const u = document.getElementById('i');
    const v = document.getElementById('j');
    const w = document.getElementById('k');
    const y = document.getElementById('m');
    const aa = document.getElementById('o');
    const resultDiv = document.getElementById('resultText'); // Ambil elemen div hasil

    // Function to format date to "13 Agustus 2024"
    function formatDateForText(dateString) {
        const [day, month, year] = dateString.split(' - ');
        const months = ["Januari", "Februari", "Maret", "April", "Mei", "Juni", "Juli", "Agustus", "September", "Oktober", "November", "Desember"];
        const monthIndex = parseInt(month, 10) - 1;
        return `${parseInt(day, 10)} ${months[monthIndex]} ${year}`;
    }

    const ab = new Date();
    const ac = ab.getDate().toString().padStart(2, '0') + ' - ' +
              (ab.getMonth() + 1).toString().padStart(2, '0') + ' - ' +
              ab.getFullYear();
    t.value = ac;

    const ad = new Image();
    ad.src = q;
    ad.onload = () => {
        s.drawImage(ad, 0, 0, r.width, r.height);
    };

    aa.addEventListener('click', () => {
        const ae = t.value.trim(); // Tanggal untuk canvas tetap dalam format aslinya
        const formattedDate = formatDateForText(ae); // Format tanggal untuk bagian bawah
        const af = u.value.trim().split('').join(' ');
        const ag = v.value.trim();
        const ah = w.value.trim().split('').join(' ');
        const aj = y.value.trim().split('').join(' ');

        s.clearRect(0, 0, r.width, r.height);
        s.drawImage(ad, 0, 0, r.width, r.height);

        s.fillStyle = 'rgba(0, 0, 0, 0.5)'; // black

        if (ae) {
            s.font = 'bold 30.3px Arial Black'; // Menggambar teks bayangan sedikit di bawah dan di kanan
            s.fillText(ae, r.width / 2.9 - s.measureText(ae).width / 10 + 2, 192); // Bayangan
         }
        s.fillStyle = 'white'; // Warna teks utama
        if (ae) {s.fillText(ae, r.width / 2.9 - s.measureText(ae).width / 10, 190); // Teks utama
         }
        s.fillStyle = 'white';
        if (af) {
            s.font = 'bold 65px Arial Black';
            s.fillText(af, r.width / 2.9 - s.measureText(af).width / 10, 305);
        }
        s.fillStyle = 'white';
        if (ag) {
            // Kondisi untuk menentukan ukuran font berdasarkan shio
            if (["NAGA", "KUDA", "ULAR"].includes(ag)) {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.9 - s.measureText(ag).width / 1.8, 332);
            } else if (ag === "KELINCI") {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.8 - s.measureText(ag).width / 1.8, 332);
            } else if (ag === "HARIMAU") {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.8 - s.measureText(ag).width / 1.8, 332);
            } else if (ag === "KERBAU") {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.8 - s.measureText(ag).width / 1.8, 332);
            } else if (ag === "TIKUS") {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.9 - s.measureText(ag).width / 1.8, 332);
            } else if (ag === "BABI") {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.9 - s.measureText(ag).width / 1.8, 332);
            } else if (ag === "ANJING") {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.8 - s.measureText(ag).width / 1.8, 332);
            } else if (ag === "AYAM") {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.9 - s.measureText(ag).width / 1.8, 332);
            } else if (ag === "MONYET") {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.8 - s.measureText(ag).width / 1.8, 332);
            } else if (ag === "KAMBING") {
                s.font = 'bold 15px Arial Black';
                s.fillText(ag, r.width / 1.8 - s.measureText(ag).width / 1.8, 332);
            } else {
                // Default font size jika shio tidak cocok
                s.font = 'bold 30px Arial Black';
                s.fillText(ag, r.width / 2.8 - s.measureText(ag).width / 4.3, 277);
            }
        }
        s.fillStyle = 'white';
        if (ah) {
            s.font = 'bold 50px Arial Black';
            s.fillText(ah, r.width / 5 - s.measureText(ah).width / 4.4, 422);
        }
        s.fillStyle = 'white';
        if (aj) {
            s.font = 'bold 50px Arial Black';
            s.fillText(aj, r.width / 1.55 - s.measureText(aj).width / 4.4, 422);
        }

        // Update the result text below the canvas
        let resultText = `Angka Result Pasaran HONGKONG hari ini adalah :<br/><br/>Tanggal : ${formattedDate}<br/>Hasil Result : ${af}<br/>Shio : ${ag}<br/>Selamat Kepada Pemenang !!<br/><br/>Link Live Draw : rabta.shop/HongkongLotto<br/>Link Mudah Akses Terpercaya : https://many.link/djarumsport<br/>Telegram : @Djarum365_id<br/>Instagram : @djarum365.sport<br/>Twitter : @Djarum_365<br/><br/>Untuk caption pada twitter cukup hapus saja twitternya ya guys.`;
        resultDiv.innerHTML = resultText;
    });
</script>

</body>
</html>
