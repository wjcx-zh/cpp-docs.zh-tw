---
title: 整數降級
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: aee0a5041cd37b1fbad785b760b8cefde74eb195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218880"
---
# <a name="demotion-of-integers"></a>整數降級

**ANSI 3.2.1.2**：將整數轉換為較短的帶正負號整數的結果，或將不帶正負號的整數轉換為長度相等的帶正負號整數的結果 (如果值無法表示的話)。

當 **`long`** 整數轉換成 **`short`** ，或 **`short`** 轉換為時 **`char`** ，會保留最不重要的位元組。

例如，在下列程式碼中

```
short x = (short)0x12345678L;
```

指派值 0x5678 給 `x`，以及下列程式碼

```
char y = (char)0x1234;
```

指派值 0x34 給 `y`。

當 **`signed`** 變數轉換成，反之亦然 **`unsigned`** ，位模式則保持不變。 例如，將-2 （0xFE）轉換成 **`unsigned`** 值會產生254（也是0xFE）。

## <a name="see-also"></a>另請參閱

[陣列](../c-language/integers.md)
