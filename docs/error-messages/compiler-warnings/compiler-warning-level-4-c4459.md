---
title: 編譯器警告 （層級 4） C4459 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4459
dev_langs:
- C++
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0fc86be746bafdf4987a7492c59d9686535cef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040891"
---
# <a name="compiler-warning-level-4-c4459"></a>編譯器警告 （層級 4） C4459

> 宣告的 '*識別碼*' 會隱藏全域宣告

Deklarace*識別碼*本機範圍內隱藏相同名稱的宣告*識別項*在全域範圍中。 這項警告可讓您知道的參考*識別碼*在這個範圍中解析的區域宣告的版本，而非全域版本，這可能會或可能不到您的意圖。 一般而言，我們建議您盡量減少工程最好使用全域變數。 全域命名空間的干擾降到最低，我們建議使用的具名命名空間的全域變數。

這項警告是 Visual Studio 2015 的 Visual c + + 編譯器版本 18.00 的新功能。 若要隱藏警告的編譯器或更新版本移轉您的程式碼時，該版本中，使用[/wv:18](../../build/reference/compiler-option-warning-level.md)編譯器選項。

## <a name="example"></a>範例

下列範例會產生 C4459:

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

若要修正此問題的一個方式是建立您的全域變數的命名空間，但不使用`using`該命名空間帶入範圍，因此所有參考都必須都使用明確的指示詞完整名稱：

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
