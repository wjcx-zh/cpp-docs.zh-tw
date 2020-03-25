---
title: 編譯器警告 (層級 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 5970aa439a450bda4c1a2036da299d5c3cfbdb7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198896"
---
# <a name="compiler-warning-level-3-c4290"></a>編譯器警告 (層級 3) C4290

C++例外狀況規格會被忽略，但不會指出函式不 __declspec （nothrow）

函式會使用例外狀況規格來宣告， C++而視覺效果會接受但不會執行此功能。 在編譯期間忽略例外狀況規格的程式碼，可能需要重新編譯並連結，才能在支援例外狀況規格的未來版本中重複使用。

如需詳細資訊，請參閱[例外狀況規格（throw）](../../cpp/exception-specifications-throw-cpp.md) 。

您可以使用[warning](../../preprocessor/warning.md) pragma 來避免這個警告：

```cpp
#pragma warning( disable : 4290 )
```

下列程式碼範例會產生 C4290：

```cpp
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```
