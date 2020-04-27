---
title: ATL 登錄器和巴格斯格式 (BNF) 語法
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 0f07a39863b586d524d060dc3df7117e2c930b3e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168705"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>了解巴格斯格式 (BNF) 語法

本主題將使用 BNF 語法來說明 ATL 登錄器所使用的指令碼，其使用下表所示的標記法。

|慣例/符號|意義|
|------------------------|-------------|
|::=|對等用法|
|&#124;|或者|
|X+|一或多個 X。|
|\[X]|X 是選擇性的。 選擇性的分隔符號會由 \[] 來表示。|
|任何**粗體**文字|字串常值。|
|任何「斜體」** 文字|如何建構字串常值。|

如上表所示，登錄器指令碼會使用字串常值。 這些值是必須出現在您的指令碼中的實際文字。 下表說明 ATL 登錄器指令碼中所使用的字串常值。

|字串常值|動作|
|--------------------|------------|
|**ForceRemove**|完全移除下一個機碼 (若有的話)，然後重新建立它。|
|**NoRemove**|不要在取消登錄期間移除下一個機碼。|
|**初始值**|指定 `<Key Name>` 實際上是具名的值。|
|**刪除**|在登錄期間刪除下一個機碼。|
|**今日**|指定下一個值為字串 (REG_SZ)。|
|**d**|指定下一個值為 DWORD (REG_DWORD)。|
|**分鐘**|指定下一個值為 multistring (REG_MULTI_SZ)。|
|**位元組**|指定下一個值為二進位值 (REG_BINARY)。|

## <a name="bnf-syntax-examples"></a>BNF 語法範例

以下數個語法範例可協助您了解標記法和字串常值如何在 ATL 登錄器指令碼中運作。

### <a name="syntax-example-1"></a>語法範例 1

> \<登錄運算式>：： = \<新增金鑰>

指定 `registry expression` 相當於 `Add Key`。

### <a name="syntax-example-2"></a>語法範例 2

> \<登錄運算式>：： = \<新增金鑰> |\<刪除金鑰>

指定 `registry expression` 相當於 `Add Key` 或 `Delete Key`。

### <a name="syntax-example-3"></a>語法範例 3

> \<索引鍵名稱>：： =\<' 英數位元>+ '

`Key Name`指定相當於一或多個`AlphaNumeric`值。

### <a name="syntax-example-4"></a>語法範例 4

> \<新增金鑰>：： = [**ForceRemove** | **NoRemove** | **val**]\<機碼名稱>

指定 `Add Key` 相當於`Key Name`，而且字串常值 `ForceRemove`、`NoRemove` 和 `val` 均為選擇性。

### <a name="syntax-example-5"></a>語法範例 5

> \<英數位元>：： =*任何字元 NOT Null，也就是 ASCII 0*

指定 `AlphaNumeric` 相等於任何非 NULL 字元。

### <a name="syntax-example-6"></a>語法範例 6

```rgs
val 'testmulti' = m 'String 1\0String 2\0'
```

指定機碼名稱 `testmulti` 為 `String 1` 和 `String 2` 所組成的 multistring 值。

### <a name="syntax-example-7"></a>語法範例 7

```rgs
val 'testhex' = d '&H55'
```

指定機碼名稱 `testhex` 是設定為十六進位 55 (十進位 85) 的 DWORD 值。 請注意，此格式遵守如同可在 Visual Basic 規格中找到的 **&H** 標記法。

## <a name="see-also"></a>另請參閱

[建立註冊機構腳本](../atl/creating-registrar-scripts.md)
