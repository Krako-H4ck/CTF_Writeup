# EVEN RSA CAN BE BROKEN??? (crypto) Easy 200pt

## Question

This service provides you an encrypted flag. Can you decrypt it with just N & e?

## Solution

サーバに接続すると、RSA暗号の公開鍵$`N,e`$と暗号文が渡されます。

$`N`$に注目すると桁数が小さいので、Msieveを使って素因数分解をしてみることにしました。
Msieveとは、素因数分解を高速で行うためのアルゴリズムを実装したライブラリです。

実行すると、以下のようになりました。

```shell
$ ./msieve -q -e -v 18184985738862465311285041992717372026103301792826151475718612877695005154773948291029074022167487148699857522388036098757267857485688708263023240892896058


Msieve v. 1.52 (SVN unknown)
Fri Mar 21 03:25:21 2025
random seeds: 21406116 7c7c215a
factoring 18184985738862465311285041992717372026103301792826151475718612877695005154773948291029074022167487148699857522388036098757267857485688708263023240892896058 (155 digits)
p1 factor: 2
prp154 factor: 9092492869431232655642520996358686013051650896413075737859306438847502577386974145514537011083743574349928761194018049378633928742844354131511620446448029
elapsed time 00:00:00
```

最初に見たときに気づかなかったのですが、$`N`$が偶数なので$`p`$か$`q`$どちらかが$`2`$になり、もう片方は$`N`$を$`2`$で割った数になります。
そのため、Msieveを使う必要はありませんでした。

この結果から、RSA暗号の秘密鍵$`d`$を求めることができるので、暗号文を復号するとフラグが出てきました。

## Flag
picoCTF{tw0_1$_pr!m33486c703}