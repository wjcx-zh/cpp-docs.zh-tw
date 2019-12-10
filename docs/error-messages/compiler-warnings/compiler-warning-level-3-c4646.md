---
title: 編譯器警告 (層級 3) C4646
ms.date: 11/04/2016
f1_keywords:
- C4646
helpviewer_keywords:
- C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
ms.openlocfilehash: a5f78a978baa1c5b4c7854692d7b8b6ff294f3a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991730"
---
# <a name="compiler-warning-level-3-c4646"></a>編譯器警告 (層級 3) C4646

使用 __declspec(noreturn) 宣告的函式有非 void 的傳回類型

標記為 [noreturn](../../cpp/noreturn.md) `__declspec` 修飾詞的函式應該有 [void](../../cpp/void-cpp.md) 傳回類型。

下列範例會產生 C4646：

```cpp
// C4646.cpp
// compile with: /W3 /WX
int __declspec(noreturn) TestFunction()
{   // C4646  make return type void
}
```
