---
title: 呼叫慣例
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: d351ae064b8c9bdd0599a1d6981166371a62af58
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216605"
---
# <a name="calling-conventions"></a>呼叫慣例

Visual C/C++ 編譯器提供數個用於呼叫內部和外部函式的不同慣例。 了解這些不同的方法可協助您偵錯程式，並將您的程式碼與組合語言常式連結。

與此主旨有關的主題將說明呼叫慣例之間的差異、引數傳遞方式，以及函式傳回值的方式。 並且也會探討 naked 函式呼叫，這是一個讓您自行撰寫初構和終解程式碼的進階功能。

如需 x64 處理器呼叫慣例的詳細資訊，請參閱[呼叫慣例](../build/x64-calling-convention.md)。

## <a name="topics-in-this-section"></a>本節主題：

- [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)（ **`__cdecl`** 、 **`__stdcall`** 、 **`__fastcall`** 和其他）

- [呼叫範例：函式原型和呼叫](../cpp/calling-example-function-prototype-and-call.md)

- [使用 naked 函式呼叫撰寫自訂初構/終解程式碼](../cpp/naked-function-calls.md)

- [浮點副處理器和呼叫慣例](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [淘汰呼叫慣例](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>另請參閱

[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)
