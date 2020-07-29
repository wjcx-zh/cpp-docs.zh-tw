---
title: inline_depth pragma
ms.date: 08/29/2019
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: 73540ec19c4ecc18a740dace0d23a37ad43182c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219413"
---
# <a name="inline_depth-pragma"></a>inline_depth pragma

指定內嵌啟發式搜尋深度。 呼叫圖表中的深度函數若大於指定的值，則不會內嵌。

## <a name="syntax"></a>語法

> **#pragma inline_depth （** [ *n* ] **）**

## <a name="remarks"></a>備註

此 pragma 會控制標記為[內嵌](../cpp/inline-functions-cpp.md)和[__inline](../cpp/inline-functions-cpp.md)之函式的內嵌，或在選項下自動內嵌 `/Ob` 。

*n*可以是介於0到255之間的值，其中255表示呼叫圖形中的深度不受限制。 值為0會禁止內嵌展開。 若未指定*n* ，則會使用預設值254。

**Inline_depth** pragma 控制一系列函式呼叫可以展開的次數。 例如，假設內嵌深度為4。 如果呼叫 B，然後 B 呼叫 C，則所有三個呼叫都會以內嵌方式展開。 不過，如果最接近的內嵌深度展開為2，則只會展開 A 和 B，而 C 會維持為函式呼叫。

若要使用這個 pragma，您必須將 `/Ob` 編譯器選項設定為1或更高。 使用這個 pragma 設定的深度會在 pragma 之後的第一次函式呼叫生效。

內嵌深度可以在展開期間減少，但不會增加。 如果內嵌深度為6，而且在展開期間，預處理器遇到值為8的**inline_depth** pragma，則深度會維持為6。

**Inline_depth** pragma 不會影響以標記的函式 **`__forceinline`** 。

> [!NOTE]
> 遞迴函式可透過內嵌於最大 16 個呼叫深度的方式替代。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_recursion](../preprocessor/inline-recursion.md)
