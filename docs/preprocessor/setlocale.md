---
title: setlocale pragma
ms.date: 08/29/2019
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: 9603c132610e0cfb1e8f955be48271870527105b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219374"
---
# <a name="setlocale-pragma"></a>setlocale pragma

定義轉譯寬字元常數和字串常值時所使用*的地區設定、國家*/地區、區域和語言。

## <a name="syntax"></a>語法

> **#pragma setlocale （"** [*地區設定-字串*] **"）**

## <a name="remarks"></a>備註

因為將多位元組字元轉換為寬字元的演算法可能會因地區設定而異，或編譯可能會發生在不同的地區設定，而這是可執行檔將會在其中執行的位置，所以這個 pragma 提供了一種方法，可在編譯時期指定目標地區設定。 它保證寬字元字串會以正確的格式儲存。

預設的*地區設定字串*為 ""。

"C" 地區設定會將字串中的每個字元對應到其值做為 **`wchar_t`** 。 的其他有效值 `setlocale` 是在[語言字串](../c-runtime-library/language-strings.md)清單中找到的專案。 例如，您可以指定：

```cpp
#pragma setlocale("dutch")
```

指定語言字串的能力取決於電腦上的字碼頁和語言識別項支援。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞與 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
