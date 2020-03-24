---
title: 編譯器錯誤 C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 2aa922ebeadb374a7eac73a0f452376472b00984
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206024"
---
# <a name="compiler-error-c2383"></a>編譯器錯誤 C2383

'*symbol*'：此符號上不允許使用預設引數

編譯器C++在函式的指標上不允許預設引數。

這段程式碼已由 Microsoft C++編譯器在 Visual Studio 2005 之前的版本中接受，但現在會提供錯誤。 對於在所有版本的 Visual C++中都適用的程式碼，請勿將預設值指派給函式的指標引數。

## <a name="example"></a>範例

下列範例會產生 C2383，並顯示可能的解決方案：

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
