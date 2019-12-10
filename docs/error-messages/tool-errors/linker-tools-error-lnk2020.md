---
title: 連結器工具錯誤 LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 9c6be2548e277af08f1069a70b26cd761db835bc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988770"
---
# <a name="linker-tools-error-lnk2020"></a>連結器工具錯誤 LNK2020

無法解析的標記 ' token '

類似于未定義的外部錯誤，不同之處在于參考是透過中繼資料。 在中繼資料中，必須定義所有函數和資料。

解決方式：

- 定義遺失的函數或資料，或

- 包含已定義遺失函數或資料的物件檔案或程式庫。

## <a name="example"></a>範例

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

## <a name="example"></a>範例

如果您建立 managed 範本類型的變數，但也不具現化類型，也會發生 LNK2020。

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
