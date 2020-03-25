---
title: 編譯器警告 (層級 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 54baf35eaeb5ef2c8add024f25c059480d60617b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186553"
---
# <a name="compiler-warning-level-1-c4508"></a>編譯器警告 (層級 1) C4508

' function '：函數應該傳回值;假設為 ' void ' 傳回類型

函數未指定傳回類型。 在此情況下，C4430 應該也會引發，而編譯器會執行 C4430 所報告的修正（預設值為 int）。

若要解決這個警告，請明確宣告函式的傳回型別。

下列範例會產生 C4508：

```cpp
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```
