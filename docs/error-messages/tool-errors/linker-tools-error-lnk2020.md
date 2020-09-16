---
title: 連結器工具錯誤 LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 6fd4859e4f8cad657de57e8039bd647e5e2b99a9
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684634"
---
# <a name="linker-tools-error-lnk2020"></a>連結器工具錯誤 LNK2020

未解析的權杖 ' token '

類似于未定義的外部錯誤，不同之處在于參考是經由中繼資料。 在中繼資料中，必須定義所有的函式和資料。

解決方式：

- 定義遺失的函數或資料，或

- 包含已定義遺失的函式或資料的物件檔案或程式庫。

## <a name="examples"></a>範例

下列範例會產生 LNK2020。

```cpp
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

如果您建立受管理範本類型的變數，但也未具現化類型，也會發生 LNK2020。

下列範例會產生 LNK2020。

```cpp
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```
