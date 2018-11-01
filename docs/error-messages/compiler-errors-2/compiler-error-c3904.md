---
title: 編譯器錯誤 C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: 8c7f4a2861825a35d676328b5e283a5e4087d85b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519778"
---
# <a name="compiler-error-c3904"></a>編譯器錯誤 C3904

'property_accessor': 必須指定數字的參數

檢查中的參數數目您`get`和`set`針對維度屬性的方法。

- 參數數目`get`方法必須等於屬性的維度數目，或為零的非索引屬性。

- 參數數目`set`方法必須是其中一個屬性的維度數目範圍內。

如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3904。

```
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

## <a name="example"></a>範例

下列範例會產生 C3904。

```
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