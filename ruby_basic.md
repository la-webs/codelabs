author: Life_is_Tech!\_Web サービスプログラミングコース
summary: Ruby 基礎
id: ruby-basic
categories: ruby
environments: Web
status: Published
feedback link: <https://github.com/la-webs/codelabs>

# Ruby 基礎

## はじめに

このコードラボでは、実際に Cloud9 を使用しながら Ruby について学んでいきます。

Cloud9 で実際にコードを入力して手を動かしながら、進めていきましょう！

### 実行環境を整える

まずは、Cloud9 を開き、`enviroment`のフォルダの直下に、`sample.rb`という名前のファイルを作成しましょう。

下の写真のようになっていれば OK です。

![Cloud9が表示されているか](img/cloud9_ok.png)

### コメント

<!-- TODO: コメントの説明文書く -->

## Ruby を実行する

`sample.rb`に下のコードを書いてみましょう。

```ruby
puts "hello world"
```

### Ruby ファイルの実行

下のコマンドでファイルを実行しましょう。Ruby ファイルは、`ruby ファイル名`で実行することができます。

```sh
ruby sample.rb
```

下のようにコンソールに出力されたら OK です。

```sh
hello world
```

### 標準出力

標準出力は、コンソールに情報を表示することができます。

文字列をコンソールに出力したい場合

```ruby
puts "hoge"
```

```sh
hoge
```

変数の内容をコンソールに出力したい場合

```ruby
hoge = "hello"
puts hoge
```

```sh
hello
```

### チャレンジ

文字列の場合・変数を使う場合の 2 つのパターンで実際にコードを書いて出力させましょう

```sh
Cloud9を使って開発するよ
```

## 変数を知る

次に、変数について詳しく学んでいきましょう。

まず変数とは、データに名前をつけて区別できるようにする仕組みで、Ruby では以下のように定義します。また、Ruby は動的型付け言語なので、型宣言は不要です。

```ruby
キーワード = 初期値
```

### 変数の定義

```ruby
instructor = "kaikai"
puts instructor
```

下のように出力されるか確認してみよう

```sh
kaikai
```

## 型を知る

<!-- TODO: 型の種類について説明 -->

## 型: 文字列を知る

シングルウォートまたはダブルクォートで定義できる。

```ruby
instructor = 'kaikai'
instructor = "kaikai"
```

演算子で文字列同士の連結ができる

```ruby
instructor = 'kaikai'
puts 'hello ' + instructor + '!'
# -> hello kaikai!
```

ダブルクォートでは、式が展開できる

```ruby
instructor = 'kaikai'
puts "hello #{instructor}!"
# -> hello kaikai!
```

## 型: 数値を知る

整数

```ruby
number = 10
```

小数

```ruby
number = 10.0
```

演算を行う場合、一方が小数だと自動で小数型に型変換が行われ、演算が行われる。

```ruby
puts 10 + 10.1
puts 10 / 1.0
```

```sh
20.1
10.0
```

### 型: 配列を知る

```ruby
animals = ["dog", "cat", "mouse"]
puts animals[1]
```

```sh
cat
```

#### 要素の追加

`cat`が出力されたか確認してみよう

```ruby
animals = ["dog", "cat", "mouse"]
animals.push("rabbit")
puts animals
```

```ruby
animals = ["dog", "cat", "mouse"]
animals << "rabbit"
puts animals
```

```sh
["dog", "cat", "mouse", "rabbit"]
```

## 型: ハッシュを知る

配列の添付部分をシンボルや文字列で任意に指定できる

```ruby
colors = { green: "緑", red: "赤" }
puts colors[:green]
```

```sh
緑
```

存在しないものを送ると nil が帰ってくる

```ruby
colors = { green: "緑", red: "赤"}
puts colors[:blue]
```

```sh
nil
```

追加と削除

```ruby
colors = { green: "緑", red: "赤"}

colors[:blue] = "青"
puts colors

colors.delete(:red)
puts colors
```

```sh
{ green: "緑", red: "赤", blue: "青" }
{ green: "緑", blue: "青" }
```

## 型変換を知る

```ruby
puts "3" + "4"
puts 3 + 4
```

```sh
34
7
```

型の違うオブジェクトの演算は TypeError になるので、型変換が必要

```ruby
puts "3" + 4
```

```sh
TypeError: no implicit conversion of Integer into String
```

型変換を行うことで演算が可能になる

```ruby
puts "3".to_i + 4
```

```sh
7
```

```ruby
# 文字列から整数に型変換（数値に変換できない場合、0となる）
"string".to_i

# 文字列から小数に型変換（数値に変換できない場合、0となる）
"string".to_f

# 整数から小数に型変換
10.to_f

# 数値から文字列に型変換
10.to_s
```

## ループを知る

while を使う

```ruby
x = 4

while x >= 1
  puts x
  x = x - 1
end
```

```sh
4
3
2
1
```

for を使う

```ruby
for i in 1..4 do
  puts i
end
```

```sh
1
2
3
4
```

```ruby
animals = ["dog", "cat", "mouse"]

animals.each do |animal|
  puts animal
end
```

```sh
dog
cat
mouse
```

## 条件分岐を知る

```ruby
x = 4

if x == 0
  puts "zero"
elsif x % 2 == 0
  puts "even"
else
  puts "odd"
end
```

```sh
even
```

````ruby
x = 4

unless x == 0
  puts "non zero"
else
  puts "zero"
end

```sh
non zero
````

## クラスとインスタンスを知る

- クラス
  変数とメソッドが入る設計図
- インスタンス
  その実体

講師クラスの場合

class instructor
変数 name, course
メソッド teach, answer

instance かいかい
変数
name -> かいかい
course -> Web サービス
メソッド
teach, answer

instance ちゃんりか
変数
name -> ちゃんりか
course -> Web サービス
メソッド
teach, answer

## クラスとインスタンス: 変数を使う

変数を使う

```ruby
class Instructor
  def initialize(name, course)
    @name = name
    @course = course
  end
end
```

## クラスとインスタンス: インスタンスを使う

```ruby
kaikai = Instructor.new("かいかい", "Webサービス")
puts kaikai.name
```

```sh
かいかい
```

ちゃんりかの場合も同様にやってみましょう！

メソッド

```ruby
class Instructor
  ..
  def answer(student)
    puts "#{student}の質問に答える"
  end
end

kaikai = Instructor.new("かいかい", "Webサービス")
kaikai.answer("がっしー")
```

```sh
がっしーの質問に答える
```

teach メソッドを作って、`Rubyについて教える`と`Sinatraについて教える`を返すメソッドをつくってみよう！

## Ruby の命名規則

|            | 命名規則             | 例  |
| ---------- | -------------------- | --- |
| クラス     | UpperCamelCase       |     |
| モジュール | UpperCamelCase       |     |
| メソッド   | snake_case           |     |
| 変数       | snake_case           |     |
| 定数       | SNAKE_WITH_UPPERCASE |     |

## まとめ

Ruby は、究極のオブジェクト指向だ！
Ruby はすべてがオブジェクト

例えば、文字列は String クラスのインスタンス

```ruby
instructor = 'chanrika' # Stringクラスのインスタンス
puts instructor.include?('a') # Stringクラスのメソッドが使える -> 戻り値はTrueクラスのインスタンス
puts instructor.to_i # Stringクラスのメソッドが使える -> 戻り値はIntegerクラスのインスタンス
```

```sh
true
0
```

```ruby
animals = ["dog", "cat", "mouse"] # Arrayクラスのインスタンス
animals.each do |animal| # Arrayクラスのメソッドが使える
  puts animal # 戻り地はStringクラスのインスタンス
end
```

```sh
dog
cat
mouse
```

## Challenge: じゃんけんアプリを作ろう

## Challenge: あっち向いてホイアプリを作ろう
