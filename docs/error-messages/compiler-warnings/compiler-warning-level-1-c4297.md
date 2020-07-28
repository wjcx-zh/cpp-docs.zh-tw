---
title: 編譯器警告 (層級 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 53c9a3c311f0136136c1c57438860edcc0766e0f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220063"
---
# <a name="compiler-warning-level-1-c4297"></a>編譯器警告 (層級 1) C4297

'function' : 函式預設並不會擲回例外狀況，但卻擲回例外狀況

函式宣告包含（可能是隱含的） **`noexcept`** 規範、空的 **`throw`** 例外狀況規範或[__declspec （nothrow）](../../cpp/nothrow-cpp.md)屬性，而且定義包含一個或多個[throw](../../cpp/try-throw-and-catch-statements-cpp.md)語句。 若要解決 C4297，請勿嘗試在宣告 `__declspec(nothrow)`、`noexcept(true)` 或 `throw()` 的函式中擲回例外狀況。 或者，移除 **`noexcept`** 、 `throw()` 或 `__declspec(nothrow)` 規格。

根據預設，編譯器會為使用者定義的解構函式和取消配置函式和編譯器所產生的特殊成員函式產生隱含 `noexcept(true)` 規範。 這會符合 ISO C++11 標準。 若要防止產生隱含的 noexcept 規範，並將編譯器還原為 Visual Studio 2013 的非標準行為，請使用 **/zc： implicitNoexcept-** 編譯器選項。 如需詳細資訊，請參閱[/zc： implicitNoexcept （隱含的例外](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md)狀況規範）。

如需例外狀況規格的詳細資訊，請參閱[例外狀況規格（throw）](../../cpp/exception-specifications-throw-cpp.md)。 另請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md) ，以取得如何在編譯時期修改例外狀況處理行為的相關資訊。

標記為 extern "C" 的 __declspec （[dllexport](../../cpp/dllexport-dllimport.md)）函式也會產生這個警告，即使它們是 c + + 函式也一樣。

下列範例會產生 C4297：

```cpp
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```
