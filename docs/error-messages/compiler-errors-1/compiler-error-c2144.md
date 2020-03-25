---
title: 編譯器錯誤 C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: b917c0a2c15aeb70222c948bce9a6fb275c91068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207242"
---
# <a name="compiler-error-c2144"></a>編譯器錯誤 C2144

> 語法錯誤： '*type*' 之前應加上 '*token*'

編譯器必須要有*token* ，並改為找到*類型*。

這個錯誤可能是因為遺漏右大括弧、右括弧或分號所造成。

嘗試從包含空白字元的 CLR 關鍵字建立宏時，也可能會發生 C2144。

如果您嘗試執行類型轉送，也可能會看到 C2144。 如需詳細資訊，請參閱[類型轉送（C++/cli）](../../extensions/type-forwarding-cpp-cli.md) 。

## <a name="examples"></a>範例

下列範例會產生 C2144，並顯示可修正此問題的方法：

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

下列範例會產生 C2144，並顯示可修正此問題的方法：

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```
