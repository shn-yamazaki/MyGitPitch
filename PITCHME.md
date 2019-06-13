### null安全



2019/6/13 若手技術共有会
C1 山﨑瞬
---
![](nullpo-ga.jpg)
---
null安全とは
---
安全にnullが使えるということ
---
```cs
class NullPoTest
{
  public static void Main()
  {
    Person someone = null;
    var name = someone.Name;
  }
}
```
@[6](System.NullReferenceException)
---
nullチェックする
```cs
class NullPoTest
{
  public static void Main()
  {
    Person someone = null;
    if (someone != null)
    {
      var name = someone.Name;
    }
  }
}
```
@[6-9](これで安心できる)
---
本当に安心できるか？
---
- nullチェック漏れはないか
- テストケースに漏れがないか |
- 稼働中にぬるぽしたらどうしよう |
**- 不安で夜も眠れない** |
---
>"I call it my billion-dollar mistake." by Tony Hoare
---
もしもC#がnull安全だったら
---
```cs
class NullPoTest
{
  public static void Main()
  {
    Person someone = null;
    var name = someone.Name;
  }
}
```
@[6](コンパイルエラー)
---
null安全とは、nullが原因で実行時にエラーにならないこと
---
実行時にnullになる可能性があるとコンパイルエラーとして報告してくれる
---
```cs
class NullPoTest
{
  public static void Main()
  {
    Person someone = null;
    if (someone != null)
    {
      Console.WriteLine(someone.Name);
    }
  }
}
```
@[6-9](こうするとコンパイルエラーじゃなくなる)
---
### 再掲
![](nullpo-ga.jpg)
---
ぬるぽを起こしてしまい殴られる危険性がない = 安全
---
C# 8.0でC#にもnull安全が導入予定
---
nullと上手に付き合う
```csharp
hoge?.fuga
hoge ?? fuga
hoge?[0]
```
---
### 参考
- [アントニー・ホーア - Wikipedia](https://ja.wikipedia.org/wiki/%E3%82%A2%E3%83%B3%E3%83%88%E3%83%8B%E3%83%BC%E3%83%BB%E3%83%9B%E3%83%BC%E3%82%A2)
- [null安全でない言語は、もはやレガシー言語だ - Qiita](https://qiita.com/koher/items/e4835bd429b88809ab33)
- [null安全を誤解している人達へのメッセージ - Qiita](https://qiita.com/omochimetaru/items/ee29d4c6eb0d78f02b15)
- [C# 8 で null 安全が導入されるらしいので、??（null 合体演算子）、?. ?[]（null 条件演算子）を復習する - Qiita](https://qiita.com/Nossa/items/1fd4881a0b97a5f32901)
---
EOF
