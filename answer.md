---
sort: 5
---

# 課題の解答

以下は、課題の解答例です。
課題に合格されなかった方は、こちらのコードを参考にしてください。

**product/product_detail.php**

```php
<?php
$ident = $_GET['ident'];
require_once __DIR__ . '/../classes/product.php';
$product = new Product();
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
<form method="POST" action="../cart/cart_add.php">
  <input type="hidden" name="ident" value="<?= $item['ident'] ?>">
  <table>
    <tr>
      <th>商品名</th>
      <td><?= $item['name'] ?></td>
    </tr>
    <tr>
      <td colspan="2">
        <div class="td_center">
          <img class="detail_img" src="../images/<?= $item['image'] ?>">
        </div>
      </td>
    </tr>
    <tr>
      <th>メーカー・著者<br>アーティスト</th>
      <td><?= $item['maker'] ?></td>
    </tr>
    <tr>
      <th>価 格</th>
      <td>&yen;<?= number_format($item['price']) ?></td>
    </tr>
    <tr>
      <th>注文数</th>
      <td><select name="quantity">
          <?php
          for ($i = 1; $i <= 10; $i++) {
            echo '<option value="' . $i . '">' . $i . '</option>';
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
<a href="product_select.php?genre=<?= $item['genre']; ?>">ジャンル別商品一覧に戻る</a>
</body>
</html>
```
