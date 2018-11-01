---
title: ATL 登錄器和 Backus Nauer Form (BNF) 語法
ms.date: 11/04/2016
helpviewer_keywords:
- BNF notation
- Backus Nauer Form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: b14e2a4f1c29860b9a624b09805959a9f6b550f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596725"
---
# <a name="understanding-backus-nauer-form-bnf-syntax"></a>了解 Backus Nauer Form (BNF) 語法

ATL 註冊機構所使用的指令碼以使用 backus-naur form，BNF 語法，使用下表所示的標記法本主題所述。

|慣例/符號|意義|
|------------------------|-------------|
|::=|對等項目|
|&#124;|OR|
|X +|一或多個 Xs。|
|[X]|X 是選擇性的。 表示選擇性的分隔符號\[]。|
|任何**粗體**文字|字串常值。|
|任何*斜體*文字|如何建構字串常值。|

上表所示，登錄器指令碼會使用字串常值。 這些值是必須出現在您的指令碼中的實際文字。 下表說明 ATL 登錄器指令碼中使用的字串常值。

|字串常值|動作|
|--------------------|------------|
|**ForceRemove**|（若有的話） 會完全移除下一個索引鍵，然後重新建立。|
|**NoRemove**|在取消註冊期間，不會移除下一個索引鍵。|
|**val**|指定`<Key Name>`實際上是具名的值。|
|**刪除**|註冊期間，刪除下一個索引鍵。|
|**s**|指定的下一個值是字串 (REG_SZ)。|
|**d**|指定的下一個值為 DWORD (REG_DWORD)。|
|**m**|指定的下一個值是 multistring (REG_MULTI_SZ)。|
|**b**|指定的下一個值是二進位值 (REG_BINARY)。|

## <a name="bnf-syntax-examples"></a>Backus-naur form，BNF 語法範例

以下是幾個語法範例，以協助您了解的標記法和字串常值中的 ATL 登錄器指令碼的運作方式。

### <a name="syntax-example-1"></a>語法範例 1

```
<registry expression> ::= <Add Key>
```

指定`registry expression`相當於`Add Key`。

### <a name="syntax-example-2"></a>語法範例 2

```
<registry expression> ::= <Add Key> | <Delete Key>
```

指定`registry expression`相當於`Add Key`或`Delete Key`。

### <a name="syntax-example-3"></a>語法範例 3

```
<Key Name> ::= '<AlphaNumeric>+'
```

指定`Key Name`相當於一或多個`AlphaNumerics`。

### <a name="syntax-example-4"></a>語法範例 4

```
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>
```

指定`Add Key`相當於`Key Name`，且字串常值`ForceRemove`， `NoRemove`，和`val`，是選擇性的。

### <a name="syntax-example-5"></a>語法範例 5

```
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0
```

指定`AlphaNumeric`相等的任何非 NULL 字元。

### <a name="syntax-example-6"></a>語法範例 6

```
val 'testmulti' = m 'String 1\0String 2\0'
```

指定的索引鍵名稱`testmulti`multistring 值組成`String 1`和`String 2`。

### <a name="syntax-example-7"></a>語法範例 7

```
val 'testhex' = d '&H55'
```

指定的索引鍵名稱`testhex`的 DWORD 值設定為十六進位 55 (十進位 85)。 請注意，此格式會遵守 **& H**標記法，做為位於 Visual Basic 規格。

## <a name="see-also"></a>另請參閱

[建立登錄器指令碼](../atl/creating-registrar-scripts.md)

