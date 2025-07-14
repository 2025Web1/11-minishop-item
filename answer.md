---
sort: 5
---

# 課題の解答

以下は、課題の解答例です。
課題に合格されなかった方は、こちらのコードを参考にしてください。

**product/product_detail.php**

```php
<?php
// ジャンル別商品一覧から送られてきた商品番号を受け取る(穴埋め)
$ident = $_GET['ident'];
// product.phpを読み込む(穴埋め)
require_once __DIR__ . '/../classes/product.php';
// Productオブジェクトを生成する(穴埋め)
$product = new Product();
// 送られてきた商品番号で商品を抽出するメソッドを呼び出し、抽出された商品データを受け取る(穴埋め)
$item = $product->getItem($ident);
?>
<!DOCTYPE html>
<html lang="ja">

<head>
  <meta charset="UTF-8">
  <title>ショッピングサイト</title>
  <link rel="stylesheet" href="../css/minishop.css">
</head>

<body>
<h3>商品詳細</h3>
<!-- 「cart_add.php」はカートに商品を入れる処理を行うphp。以降の章で実装する。 -->
<form method="POST" action="../cart/cart_add.php">
  <!-- 商品番号をhiddenで送る(穴埋め) -->
  <input type="hidden" name="ident" value="<?= $item['ident'] ?>">
  <table>
    <tr>
      <th>商品名</th>
      <!-- 商品名を出力する(穴埋め) -->
      <td><?= $item['name'] ?></td>
    </tr>
    <tr>
      <td colspan="2">
        <div class="td_center">
          <!-- imgタグを使い、商品画像を出力する(穴埋め) -->
          <img class="detail_img" src="../images/<?= $item['image'] ?>">
        </div>
      </td>
    </tr>
    <tr>
      <th>メーカー・著者<br>アーティスト</th>
      <!-- メーカー・著者・アーティストを出力する(穴埋め) -->
      <td><?= $item['maker'] ?></td>
    </tr>
    <tr>
      <th>価 格</th>
      <!-- 価格を出力する、価格はカンマ(,)区切りにする必要がある。-->
      <!--「product_select.php」で同様のやり方をしているので参考にすること(穴埋め) -->
      <td>&yen;<?= number_format($item['price']) ?></td>
    </tr>
    <tr>
      <th>注文数</th>
      <td><select name="quantity">
          <?php
          for ($i = 1; $i <= 10; $i++) {
            echo '<option value="' . $i . '">' . $i . '</option>'; // ①
          }
          ?>
        </select></td>
    </tr>
    <tr>
      <th colspan="2"><input type="submit" value="カートに入れる"></th>
    </tr>
  </table>
</form>
<br>
 <!-- ジャンル別商品一覧画面に戻る際に使用する「ジャンル」のデータを併せて送る-->
<a href="product_select.php?genre=<?= $item['genre']; ?>">ジャンル別商品一覧に戻る</a>
</body>
</html>
```
