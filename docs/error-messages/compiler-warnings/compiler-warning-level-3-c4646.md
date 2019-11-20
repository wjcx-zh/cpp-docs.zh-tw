---
title: 編譯器警告 (層級 3) C4646
ms.date: 11/04/2016
f1_keywords:
- C4646
helpviewer_keywords:
- C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
ms.openlocfilehash: 2f156bfbe92fbfb3437a7f0b9ac77a91976c2b1c
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189387"
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