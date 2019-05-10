---
title: 編譯器錯誤 C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: e9c1774fe7cd4a6883aa79f384cc64521a57ed17
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448014"
---
# <a name="compiler-error-c2383"></a>編譯器錯誤 C2383

'*符號*': 預設引數不允許在這個符號

C++編譯器不允許預設引數，函式的指標。

此程式碼已接受 MicrosoftC++在 Visual Studio 2005 之前的版本的編譯器，但現在會產生錯誤。 適用於視覺效果的所有版本的程式碼的C++，不要將預設值指派給函式指標引數。

## <a name="example"></a>範例

下列範例會產生 C2383，，並顯示可能的解決方案：

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```