---
title: 編譯器警告（層級4） C4459
ms.date: 11/04/2016
f1_keywords:
- C4459
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
ms.openlocfilehash: d6d0a802f9f628145fbc5910aca805a5b01b94d2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214369"
---
# <a name="compiler-warning-level-4-c4459"></a>編譯器警告（層級4） C4459

> '*identifier*' 的宣告會隱藏全域宣告

本機範圍中的*識別碼*宣告會隱藏全域範圍中具有相同名稱之*識別碼*的宣告。 此警告可讓您知道，此範圍內的*識別碼*參考會解析為本機宣告的版本，而不是全域版本，而不一定是您的意圖。 一般來說，我們建議您將全域變數的使用降到最低，以做為良好的工程實務。 若要將全域命名空間的污染降到最低，我們建議針對全域變數使用名為的命名空間。

這是 Microsoft c + + 編譯器18.00 版中 Visual Studio 2015 的新警告。 若要在遷移程式碼時隱藏該編譯器或更新版本的警告，請使用[/Wv： 18](../../build/reference/compiler-option-warning-level.md)編譯器選項。

## <a name="example"></a>範例

下列範例會產生 C4459：

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

修正此問題的方法之一，是為您的全域建立命名空間，但不使用 **`using`** 指示詞將該命名空間帶入範圍中，因此所有參考都必須使用明確的限定名稱：

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
