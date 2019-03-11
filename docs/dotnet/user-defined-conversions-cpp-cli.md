---
title: 使用者定義轉換 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
ms.openlocfilehash: cd3b27e0667b5ab9707db4b2cce2d7eef4611219
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743179"
---
# <a name="user-defined-conversions-ccli"></a>使用者定義轉換 (C++/CLI)

當其中一個轉換中的型別參考或實值型別或參考類型的執行個體時，本節會討論使用者定義轉換 (UDC)。

## <a name="implicit-and-explicit-conversions"></a>隱含和明確轉換

使用者定義的轉換可以是隱含或明確。  UDC 應該隱含如果轉換不會導致資訊遺失。 否則不應定義明確的 UDC。

原生類別的建構函式可用來參考或實值類型轉換為原生類別。

如需有關轉換的詳細資訊，請參閱 < [Boxing](../windows/boxing-cpp-component-extensions.md)並[標準轉換](../cpp/standard-conversions.md)。

```
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

**輸出**

```Output
in N::N
in N::N
```

## <a name="convert-from-operators"></a>轉換來源運算子

轉換來源運算子會從其他類別的物件建立定義運算子之類別的物件。

標準 c + + 不支援轉換來源運算子;標準 c + + 會使用建構函式，針對此目的。 不過，使用 CLR 類型時，Visual c + + 提供語法支援呼叫轉換來源運算子。

為了與其他符合 CLS 相容語言交互操作，您可能想將特定類別的每個使用者定義一元 （unary） 建構函式包裝對應的轉換來源運算子。

轉換來源運算子：

- 應該定義為靜態函式。

- 可以是 （適用於不會遺失有效位數，例如簡短-int 的轉換） 明確或隱含時可能會遺失有效位數。

- 應該會傳回包含類別的物件。

- 必須有唯一的參數類型為"from"類型。

下列範例示範隱含和明確的 「 轉換來源 」、 使用者定義轉換 (UDC) 運算子。

```
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

**輸出**

```Output
in operator
in constructor
10
1
```

## <a name="convert-to-operators"></a>轉換目標運算子

轉換目標運算子將某個其他物件定義運算子之類別物件的轉換。 下列範例會示範隱含的轉換目標，使用者定義轉換運算子：

```
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

**輸出**

```Output
10
```

外顯使用者定義轉換目標轉換運算子是適用於可能會遺失資料，以某種方式的轉換。 要叫用明確的轉換目標運算子，就必須使用轉型。

```
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

**輸出**

```Output
10.3
10
```

## <a name="to-convert-generic-classes"></a>若要轉換泛型類別

您可以將泛型類別轉換成 t。

```
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

**輸出**

```Output
True
```

轉換建構函式會採用型別，並使用它來建立物件。  轉換建構函式呼叫; 直接初始化轉換 （cast） 不會叫用轉換建構函式。 根據預設，轉換建構函式是明確的 CLR 型別。

```
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

**輸出**

```Output
5
R
```

在此程式碼範例中，隱含的靜態轉換函式的作用與明確的轉換建構函式相同的工作。

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

**輸出**

```Output
13
12
500
2000
```

## <a name="see-also"></a>另請參閱

[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)
