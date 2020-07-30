---
title: 編譯器警告 (層級 4) C4985
ms.date: 11/04/2016
f1_keywords:
- C4985
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 87537e960c858cc6741108cf191fbeb2a7a2a8d7
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390009"
---
# <a name="compiler-warning-level-4-c4985"></a>編譯器警告 (層級 4) C4985

> '*symbol-name*'：屬性不存在先前的宣告中。

目前方法宣告或定義的 Microsoft 原始程式碼註釋語言 (SAL) 註釋與先前宣告的註釋不同。 方法的定義和宣告中必須使用相同的 SAL 註釋。

SAL 提供一組註釋，可讓您用來描述某個函式如何使用其參數、建立與其相關的假設，以及使其完成的保證。 這些註釋會在 sal.h header 標頭檔中定義。

請注意，除非專案已指定旗標，否則 SAL 宏不會展開 [`/analyze`](../../build/reference/analyze-code-analysis.md) 。 當您指定時， **`/analyze`** 編譯器可以擲回 C4985，即使沒有出現警告或錯誤也一樣 **`/analyze`** 。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 對方法的定義及其所有宣告使用相同的 SAL 註釋。

## <a name="see-also"></a>另請參閱

[SAL 注釋](../../c-runtime-library/sal-annotations.md)
