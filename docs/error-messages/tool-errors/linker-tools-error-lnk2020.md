---
title: 連結器工具錯誤 LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 7290a90dfd92d84c4632e7f9dd38d36eccd4ac27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386326"
---
# <a name="linker-tools-error-lnk2020"></a>連結器工具錯誤 LNK2020

無法解析的語彙基元 'token'

類似於發生未定義的外部錯誤，不同之處在於會透過中繼資料的參考。 在中繼資料，就必須定義所有函式和資料。

若要解決：

- 定義遺漏的函式或資料，或

- 包含的物件檔案或遺漏的函式或資料已定義所在的程式庫。

## <a name="example"></a>範例

下列範例會產生 LNK2020。

```
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

如果您建立 managed 的範本類型的變數，但請勿也產生型別，也會發生 LNK2020。

下列範例會產生 LNK2020。

```
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