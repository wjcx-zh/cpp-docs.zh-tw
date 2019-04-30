---
title: 編譯器錯誤 C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 06d4c19208bd242169e1cd07a71e8a568f46f7b1
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344809"
---
# <a name="compiler-error-c2383"></a>編譯器錯誤 C2383

'*符號*': 預設引數不允許在這個符號

C++編譯器不允許預設引數，函式的指標。

視覺效果已接受此程式碼C++在 Visual Studio 2005 之前的版本的編譯器，但現在會產生錯誤。 適用於視覺效果的所有版本的程式碼的C++，不要將預設值指派給函式指標引數。

## <a name="example"></a>範例

下列範例會產生 C2383，，並顯示可能的解決方案：

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```