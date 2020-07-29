---
title: C 大小的整數類型
ms.date: 07/22/2020
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: 7f785efb2fc93d2ec57783dd20a43642c87e4a4c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226499"
---
# <a name="c-sized-integer-types"></a>C 大小的整數類型

**Microsoft 特定的**

Microsoft C 的功能支援可調整大小的整數類型。 您可以使用 `__intN` 類型規範（其中 *`N`* 是整數變數的大小，以位為單位）來宣告8、16、32或64位的整數變數。 *n* 的值可以是 8、16、32 或 64。 下列範例宣告了四種可調整大小整數類型的變數：

```C
__int8  nSmall;     // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

前三個大小的整數類型是具有相同大小之 ANSI 類型的同義字。 它們適用于撰寫可在多個平臺上有相同行為的可移植程式碼。 **`__int8`** 資料類型與類型同義，是與類型同義、與類型同義， **`char`** **`__int16`** 而且與 **`short`** **`__int32`** **`int`** **`__int64`** 類型同義 **`long long`** 。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[基本類型的儲存](../c-language/storage-of-basic-types.md)
