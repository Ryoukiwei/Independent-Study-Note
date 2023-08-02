#IndependentStudy 

> 筆者： 109612011 葉騏緯

## 什麼是YAML？

YAML 就跟XML、JSON 一樣，是一種給人讀寫的資料格式。
實務上，JSON 與 YAML 應用的場景不盡相同。JSON 大多用於資料傳輸，YAML 大多用於組態設定。

## YAML 簡介

YAML 格式中，含有一個到多個節點 (node)，每個節點必定是純量 (Scalar)、序列 (Sequence)、映射(Mapping)資料中的其中一種。

### - 純量 (Scalar)
運用零個或多個 Unicode 字元，以表示自定義資料 (opaque datum)。
可以理解成他是一個用文字表述的單位資料。
```yaml
kiwi bird #is cute
```

### - 序列 (Sequence)
有序的節點清單，內容並未限定類型。
```yaml
- 48763
- "Starbusrt" 
- 3.1415926
```

### - 映射(Mapping)
簡單的Key: Value 形式，Key作為索引必須為唯一值。
```
name: bird
```

- - -
## YAML 語法

根據[官方說明]([YAML Syntax — Ansible Documentation](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html))：
>There’s another small quirk to YAML. All YAML files (regardless of their association with Ansible or not) can optionally begin with `---` and end with `...` . This is part of the YAML format and indicates the start and end of a document.

一個YAML的文件應該會長這樣：
```yaml
---
# An employee record
name: Martin D'vloper
job: Developer
skill: Elite
employed: True
foods:
  - Apple
  - Orange
  - Strawberry
  - Mango
languages:
  perl: Elite
  python: Elite
  pascal: Lame
education: |
  4 GCSEs
  3 A-Levels
  BSc in the Internet of Things---
# An employee record
name: Martin D'vloper
job: Developer
skill: Elite
employed: True
foods:
  - Apple
  - Orange
  - Strawberry
  - Mango
languages:
  perl: Elite
  python: Elite
  pascal: Lame
education: |
  4 GCSEs
  3 A-Levels
  BSc in the Internet of Things
```

值得多做說明的便是當我們想要表達多行資料時，我們可以使用`|` 與`>` 來實現。
- `|` 表示後面的文字，**每一行資料都視為獨立的資料**。
```yaml
node: | 
  This is a book. 
  It is a pen.
```
取回的node是會像這樣：
```
This is a book.
It is a pen.
```

- `>` 表示後面的文字，只有在 **縮行改變** 或 **空行** 時，YAML 才會視為新的資料。
```yaml
node: >
  This is a book.
  it is a pen.
    I want to supermark.
```
取回的node是會像這樣：
```
 This is a book. It is a pen.
 I want to supermark.
```

以上為常見的YAML語法。
- --

參考資料：
- [YAML Syntax — Ansible Documentation](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html)
- [14. 延伸補充 - YAML - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天](https://ithelp.ithome.com.tw/articles/10206454)
