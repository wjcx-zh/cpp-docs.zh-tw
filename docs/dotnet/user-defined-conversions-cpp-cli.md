---
title: 使用者定義轉換 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
ms.openlocfilehash: bb7a30382bc586f4d324d47ef6e6757fac83f5ae
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988385"
---
# <a name="user-defined-conversions-ccli"></a>使用者定義轉換 (C++/CLI)

當轉換中的其中一個類型是實數值型別或參考型別的參考或實例時，本節將討論使用者定義的轉換（UDC）。

## <a name="implicit-and-explicit-conversions"></a>隱含和明確轉換

使用者定義的轉換可以是隱含或明確的。  如果轉換不會導致資訊遺失，則 UDC 應該是隱含的。 否則，應該定義明確的 UDC。

原生類別的函式可以用來將參考或實值型別轉換成原生類別。

如需轉換的詳細資訊，請參閱[裝箱](../extensions/boxing-cpp-component-extensions.md)和[標準轉換](../cpp/standard-conversions.md)。

```cpp
// mcpp_User_Defined_Conversions.cpp
// compile with: /clr
#include "stdio.h"
ref class R;
class N;

value class V {
   static operator V(R^) {
      return V();
   }
};

ref class R {
public:
   static operator N(R^);
   static operator V(R^) {
      System::Console::WriteLine("in R::operator N");
      return V();
   }
};

class N {
public:
   N(R^) {
      printf("in N::N\n");
   }
};

R::operator N(R^) {
   System::Console::WriteLine("in R::operator N");
   return N(nullptr);
}

int main() {
   // Direct initialization:
   R ^r2;
   N n2(r2);   // direct initialization, calls constructor
   static_cast<N>(r2);   // also direct initialization

   R ^r3;
   // ambiguous V::operator V(R^) and R::operator V(R^)
   // static_cast<V>(r3);
}
```

**Output**

```Output
in N::N
in N::N
```

## <a name="convert-from-operators"></a>轉換來源運算子

Convert-from 運算子會建立類別的物件，其中運算子是從其他類別的物件所定義。

標準C++不支援 convert from 運算子;標準C++針對此用途使用了函數。 不過，使用 CLR 型別時， C++視覺效果會提供呼叫 convert from 運算子的語法支援。

若要與其他符合 CLS 標準的語言互通，您可能想要使用對應的 convert from 運算子，來包裝指定類別的每個使用者定義一元函式。

從運算子轉換：

- 應定義為靜態函式。

- 當可能會遺失有效位數時，可以是隱含的（適用于不會遺失有效位數的轉換，例如 short to int）或 explicit。

- 應傳回包含類別的物件。

- 應將 "from" 類型當做唯一的參數類型。

下列範例顯示隱含和明確的「轉換自」、使用者定義的轉換（UDC）運算子。

```cpp
// clr_udc_convert_from.cpp
// compile with: /clr
value struct MyDouble {
   double d;

   MyDouble(int i) {
      d = static_cast<double>(i);
      System::Console::WriteLine("in constructor");
   }

   // Wrap the constructor with a convert-from operator.
   // implicit UDC because conversion cannot lose precision
   static operator MyDouble (int i) {
      System::Console::WriteLine("in operator");
      // call the constructor
      MyDouble d(i);
      return d;
   }

   // an explicit user-defined conversion operator
   static explicit operator signed short int (MyDouble) {
      return 1;
   }
};

int main() {
   int i = 10;
   MyDouble md = i;
   System::Console::WriteLine(md.d);

   // using explicit user-defined conversion operator requires a cast
   unsigned short int j = static_cast<unsigned short int>(md);
   System::Console::WriteLine(j);
}
```

**Output**

```Output
in operator
in constructor
10
1
```

## <a name="convert-to-operators"></a>轉換成運算子

轉換成運算子會將定義運算子的類別之物件轉換為其他物件。 下列範例顯示隱含的轉換成使用者定義的轉換運算子：

```cpp
// clr_udc_convert_to.cpp
// compile with: /clr
using namespace System;
value struct MyInt {
   Int32 i;

   // convert MyInt to String^
   static operator String^ ( MyInt val ) {
      return val.i.ToString();
   }

   MyInt(int _i) : i(_i) {}
};

int main() {
   MyInt mi(10);
   String ^s = mi;
   Console::WriteLine(s);
}
```

**Output**

```Output
10
```

明確使用者定義的轉換轉換運算子適用于可能會以某種方式遺失資料的轉換。 若要叫用明確的轉換成運算子，則必須使用 cast。

```cpp
// clr_udc_convert_to_2.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   d.d = 10.3;
   System::Console::WriteLine(d.d);
   int i = 0;
   i = static_cast<int>(d);
   System::Console::WriteLine(i);
}
```

**Output**

```Output
10.3
10
```

## <a name="to-convert-generic-classes"></a>轉換泛型類別

您可以將泛型類別轉換成 T。

```cpp
// clr_udc_generics.cpp
// compile with: /clr
generic<class T>
public value struct V {
   T mem;
   static operator T(V v) {
      return v.mem;
   }

   void f(T t) {
      mem = t;
   }
};

int main() {
   V<int> v;
   v.f(42);
   int i = v;
   i += v;
   System::Console::WriteLine(i == (42 * 2) );
}
```

**Output**

```Output
True
```

轉換的函式會採用類型，並使用它來建立物件。  轉換的函式只會使用直接初始化來呼叫;轉換不會叫用轉換的函式。 根據預設，轉換為 CLR 類型的函式是明確的。

```cpp
// clr_udc_converting_constructors.cpp
// compile with: /clr
public ref struct R {
   int m;
   char c;

   R(int i) : m(i) { }
   R(char j) : c(j) { }
};

public value struct V {
   R^ ptr;
   int m;

   V(R^ r) : ptr(r) { }
   V(int i) : m(i) { }
};

int main() {
   R^ r = gcnew R(5);

   System::Console::WriteLine( V(5).m);
   System::Console::WriteLine( V(r).ptr);
}
```

**Output**

```Output
5
R
```

在此程式碼範例中，隱含靜態轉換函式的作用與明確轉換的程式相同。

```
public value struct V {
   int m;
   V(int i) : m(i) {}
   static operator V(int i) {
      V v(i*100);
      return v;
   }
};

public ref struct R {
   int m;
   R(int i) : m(i) {}
   static operator R^(int i) {
      return gcnew R(i*100);
   }
};

int main() {
   V v(13);   // explicit
   R^ r = gcnew R(12);   // explicit

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);

   // explicit ctor can't be called here: not ambiguous
   v = 5;
   r = 20;

   System::Console::WriteLine(v.m);
   System::Console::WriteLine(r->m);
}
```

**Output**

```Output
13
12
500
2000
```

## <a name="see-also"></a>請參閱

[類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)
