---
title: 編譯器錯誤 C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: 30f472aa7a9475a19eea0e92fe5c2ea0d54e382b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442844"
---
# <a name="compiler-error-c2002"></a>編譯器錯誤 C2002

無效的寬字元常數

多位元組字元常數不正確。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 寬字元常數會包含比預期更多的位元組。

1. 不包含標準標頭檔 STDDEF.h。

1. 無法使用一般的字串常值串連的寬字元。

1. 寬字元常數前面必須有字元 'L':

    ```
    L'mbconst'
    ```

1. Microsoft c + + 前置處理器指示詞的文字引數必須是 ASCII。 比方說，指示詞， `#pragma message(L"string")`，不正確。