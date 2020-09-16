---
title: 編譯器錯誤 C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: b2c5737a4442761cbaa84b532907e579eddb423d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686061"
---
# <a name="compiler-error-c3904"></a>編譯器錯誤 C3904

' property_accessor '：必須指定數位參數 (s) 

`get`針對屬性維度檢查和方法中的參數數目 `set` 。

- 方法的參數數目 `get` 必須等於屬性的維度數目，或為非索引屬性的值為零。

- 方法的參數數目 `set` 必須比屬性的維度數目還要多。

如需詳細資訊，請參閱 [property](../../extensions/property-cpp-component-extensions.md)。

## <a name="examples"></a>範例

下列範例會產生 C3904。

```cpp
// C3904.cpp
// compile with: /clr /c
ref class X {
   property int P {
      // set
      void set();   // C3904
      // try the following line instead
      // void set(int);

      // get
      int get(int, int);   // C3904
      // try the following line instead
      // int get();
   };
};
```

下列範例會產生 C3904。

```cpp
// C3904b.cpp
// compile with: /clr /c
ref struct X {
   property int Q[double, double, float, float, void*, int] {
      // set
      void set(double, void*);   // C3904
      // try the following line instead
      // void set(double, double, float, float, void*, int, int);

      // get
      int get();   // C3904
      // try the following line instead
      // int get(double, double, float, float, void*, int);
   }
};
```
