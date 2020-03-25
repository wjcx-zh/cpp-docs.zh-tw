---
title: 編譯器錯誤 C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: c37a9b94be837248c8025a4fc069d8a242128542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208243"
---
# <a name="compiler-error-c2002"></a>編譯器錯誤 C2002

寬字元常數無效

多位元組字元常數無效。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 寬字元常數包含比預期還要多的位元組。

1. 不包含標準標頭 STDDEF.H。

1. 寬字元無法與一般字串常值串連。

1. 寬字元常數前面必須加上字元 ' L '：

    ```
    L'mbconst'
    ```

1. 若為C++Microsoft，預處理器指示詞的文字引數必須是 ASCII。 例如，指示詞 `#pragma message(L"string")`無效。
