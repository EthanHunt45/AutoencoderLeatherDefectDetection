<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  
</head>

<body>

<h1>🧵 Industrial Anomaly Detection on Leather Surfaces</h1>
<li>
    <a href="https://www.kaggle.com/datasets/ipythonx/mvtec-ad"
       target="_blank"
       rel="noopener noreferrer">
        MVTec Anomaly Detection Dataset (Leather)
    </a>
</li>

<img src="https://github.com/user-attachments/assets/ffbc44ac-28af-491f-8501-f79a327d843f" width="25"> [Open In Colab](https://colab.research.google.com/drive/11qoG17084wztYSzU8SSvkDEli6VRORAp?usp=sharing)

<p>
Bu proje, yüksek dokulu (texture) endüstriyel yüzeylerde — özellikle <strong>deri</strong> —
oluşan anomalileri tespit etmek amacıyla geliştirilmiş bir
<strong>Convolutional Autoencoder (CAE)</strong> çalışmasıdır.
</p>

<ul>
    <li>Standart kayıp fonksiyonlarının (MSE) limitlerinin analizi</li>
    <li>SSIM tabanlı rekonstrüksiyon ile doku korunumu</li>
    <li>Patch-based lokalize anomali skorlaması</li>
</ul>

<h2>🚀 Öne Çıkan Özellikler</h2>

<ul>
    <li><strong>Yüzey Korunumlu Rekonstrüksiyon:</strong> MSE yerine SSIM Loss</li>
    <li><strong>Lokalize Skorlama:</strong> Patch-based maksimum bozulma tespiti</li>
    <li><strong>Endüstriyel Metrik İyileştirmesi:</strong> Separation Ratio’da %40 artış</li>
</ul>

<h2>🧠 Metodoloji ve Teknik Zorluklar</h2>

<h3>Problem: MSE ve Regression to the Mean</h3>

<p>
MSE, piksel bazlı farklara odaklandığı için yüksek dokulu yüzeylerde iki temel probleme yol açar:
</p>

<ul>
    <li><strong>Bulanık Rekonstrüksiyon:</strong> Doku detaylarının bastırılması</li>
    <li><strong>Sinyal Kaybı:</strong> Yapısal bozulmaların gürültü içinde kaybolması</li>
</ul>

<h3>Çözüm: SSIM Loss + Patch-based Scoring</h3>

<p>
SSIM, insan görsel algısına daha yakın bir metrik olup:
</p>

<ul>
    <li>Parlaklık</li>
    <li>Kontrast</li>
    <li>Yapısal bütünlük</li>
</ul>

<p>
bileşenlerini ayrı ayrı değerlendirir. Patch-based yaklaşım ise
<strong>global ortalama yerine lokal maksimum bozulmayı</strong> skor olarak kullanır.
</p>

<h2>📊 Performans Karşılaştırması</h2>

<table>
    <thead>
        <tr>
            <th>Metrik</th>
            <th>Baseline (MSE)</th>
            <th>Optimized (SSIM + Patch)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Normal MSE / Dist</td>
            <td>0.001763 ± 0.000239</td>
            <td>0.011679 ± 0.001842</td>
        </tr>
        <tr>
            <td>Anomaly MSE / Dist</td>
            <td>0.001578 ± 0.000336</td>
            <td>0.015265 ± 0.005005</td>
        </tr>
        <tr>
            <td><strong>Separation Ratio</strong></td>
            <td><strong>0.89x (Başarısız)</strong></td>
            <td><strong>1.31x (%40 İyileşme)</strong></td>
        </tr>
    </tbody>
</table>

<div class="highlight">
<strong>Not:</strong> Mutlak hata değerlerinden ziyade,
<strong>normal ve anomali dağılımlarının ayrışması</strong> esas performans kriteridir.
</div>

<h2>🖼️ Görsel Sonuçlar</h2>

<h3>1️⃣ MSE Tabanlı İlk Deneme</h3>
<ul>
    <li>Bulanık rekonstrüksiyonlar</li>
    <li>Anlamlı olmayan heatmap’ler</li>
    <li>İç içe geçmiş histogramlar</li>
</ul>
<img width="1314" height="590" alt="image" src="https://github.com/user-attachments/assets/34e91258-f65b-4045-9432-8b6868cd5038" />
<img width="993" height="547" alt="image" src="https://github.com/user-attachments/assets/950faba0-8e37-4845-93b4-5508a03c43c3" />
Normal MSE: 0.001763 ± 0.000239
Anomaly MSE: 0.001578 ± 0.000336
Separation ratio: 0.89x

<h3>2️⃣ SSIM + Patch-based Yaklaşım</h3>
<ul>
    <li>Doku sürekliliği korunur</li>
    <li>Anomaliler lokalize edilir</li>
    <li>Dağılımlar ayrışmaya başlar</li>
</ul>
<img width="1314" height="590" alt="image" src="https://github.com/user-attachments/assets/012f50b0-a934-4154-8d7f-66eb7796fa53" />
<img width="988" height="547" alt="image" src="https://github.com/user-attachments/assets/ef21927b-c0b2-4c64-a67b-e62f954d6d21" />
Normal MSE: 0.011679 ± 0.001842
Anomaly MSE: 0.015265 ± 0.005005
Separation ratio: 1.31x


<h2>🛠️ Kullanılan Teknolojiler</h2>

<ul>
    <li>TensorFlow / Keras (CAE)</li>
    <li>OpenCV, Scikit-image (SSIM)</li>
    <li>Matplotlib, Seaborn</li>
    <li>MVTec Anomaly Detection Dataset (Leather)</li>
</ul>

<h2>📈 Sonuç</h2>

<p>
Bu çalışma, endüstriyel kalite kontrolde
<strong>doku takibinin</strong> ve
<strong>kayıp fonksiyonu seçiminin</strong>
model performansı üzerindeki kritik etkisini net biçimde ortaya koymuştur.
</p>


<h2>▶️ Nasıl Kullanılır?</h2>

<pre>
Google Colaba linkine tıklayın.
Kaggle username ve passwordu secret olarak ekleyin.
Tüm blokları çalıştırın ve sonucu görün.
</pre>

</body>
</html>
