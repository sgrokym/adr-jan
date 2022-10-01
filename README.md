# adr-jan
A Japanese Template of ADR  
日本語運用前提のADRテンプレート。

## 書き方

- 1つのアーキテクチャの1つの決定につき、1つのファイル
  - 再利用禁止。同一のアーキテクチャでも、新たな決定を行う際は新たにファイルを作成する
- Markdownのような軽量なテキストマークアップ言語を使う
- プロジェクトのリポジトリの doc/arch/adr-NNN-XXXX.md に配置する
  - NNNは作成順、XXXはタイトル
- 簡潔明瞭なドキュメントにする。それが作りやすさ、読みやすさにつながり、ADRの効果的な運用にもつながる

ADRの参考テンプレートは以下。
## 参考テンプレート
``` md: adr-001-SUGOIアーキテクチャの採用.md
# SUGOIアーキテクチャの採用
> タイトル。どんな内容の提案なのか、簡潔明瞭なタイトルにする。

Date: 2021-11-06
> 該当する決定を行った日付(YYYY-MM-DD形式)

## Status
> 提案に対してどう決定したのかのステータス。
承認
> 基本的に承認/却下/検討中の3つで十分と思われる。

## Context
> 決定の背景。
> まず今の課題と、議題にあげているアーキテクチャを採用した場合にどのような形でそれが解決できるか、どのようなメリットがあるかを書く。

現状、IMAICHIアーキテクチャを採用しているが、オートスケールが不可能で可用性が悪く、稼働率が70%程度になってしまっているという課題がある。
しかし、このSUGOIアーキテクチャを採用すれば、可用性を含めたパフォーマンスが大きく改善し、稼働率が99.9%になる上にランニングコストも50%程度下がることが見込まれる。
[SUGOIアーキテクチャのスペック](リンクのURL)

> 次に採用した場合のデメリット、弊害、プロジェクトを取り巻く環境などを書く。

SUGOIアーキテクチャを採用した場合のデメリットとして考えられるのは、プロジェクトメンバーに半月~1ヶ月程度の学習コストが発生することである。
来月に100個の新機能リリースを控えてる今の状況で採用した場合、スケジュールが破綻してしまう可能性がある。
また、2ヶ月後に議題のSUGOIアーキテクチャの倍のパフォーマンスが期待できるYABAIアーキテクチャがリリースされるという情報もある。
[YABAIアーキテクチャのPR記事](リンクのURL)

> 最終的にどう判断したかを書く。

上記の通り様々なことが検討されたが、ユーザーから稼働率に関する不満のフィードバックが多く、これがサービスとしての致命傷になリ得ると判断されたため、今回SUGOIアーキテクチャを採用することを決定した。

## Decision
>  決定事項。今回決まったことを書く。箇条書きが望ましい。

- 来月リリース予定の新機能のうち、優先度の高い新機能Aと新機能Bのリリース完了後にSUGOIアーキテクチャ導入作業に入ることとする
- 来月の10日になってプロジェクトメンバーのうち、2人が学習完了しなかった場合はSUGOIアーキテクチャの採用をいったん保留とする

## Conquences
> 決定を行った結果。
> 後日、その決定の結果を評価する。良かった点、悪かった点や次回のADRに向けてのコメントなどを書く。

SUGOIアーキテクチャを導入した結果、課題だった稼働率は99.9%になりユーザーからも稼働率に関しての不満がでることはなくなった。
やはり、IMAICHIアーキテクトのIMAICHI機構は採用するべきではなく、SUGOIアーキテクチャにあるようなSUGOI機構が可用性の担保には重要であった。
しかし、ランニングコストは想定よりも下がらず10%減にとどまったことと、スループットが旧アーキテクチャより下がってしまいコア機能の処理時間が増大してしまったことに関しては事前検証が甘かった。
YABAIアーキテクチャの採用も検討したいところだが、その際は同じ轍を踏まないようにこれら点も精査して設計に臨みたい。

```
## Reference
[Homepage of the ADR GitHub organization](https://adr.github.io/)