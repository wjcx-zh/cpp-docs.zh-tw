---
title: HOW TO：使用陣列，在 C + + /cli CLI
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++], single-dimension
ms.assetid: 301cfb3e-199f-42c8-8151-629dce9e87f3
ms.openlocfilehash: b0a13441bc3532884dbbd32f28d57c15e352c3ef
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414599"
---
# <a name="how-to-use-arrays-in-ccli"></a>HOW TO：使用陣列，在 C + + /cli CLI

本文說明如何使用陣列，在 C + + /cli CLI。

## <a name="single-dimension-arrays"></a>一維陣列

下列範例示範如何建立一維陣列的參考、 值和原生指標型別。 此外，它也會示範如何從函式會傳回一維陣列，以及如何將單一維度陣列做為引數傳遞至函式。

```cpp
// mcppv2_sdarrays.cpp
// compile with: /clr
using namespace System;

#define ARRAY_SIZE 2

value struct MyStruct {
   int m_i;
};

ref class MyClass {
public:
   int m_i;
};

struct MyNativeClass {
   int m_i;
};

// Returns a managed array of a reference type.
array<MyClass^>^ Test0() {
   int i;
   array< MyClass^ >^ local = gcnew array< MyClass^ >(ARRAY_SIZE);

   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      local[i] = gcnew MyClass;
      local[i] -> m_i = i;
   }
   return local;
}

// Returns a managed array of Int32.
array<Int32>^ Test1() {
   int i;
   array< Int32 >^ local = gcnew array< Int32 >(ARRAY_SIZE);

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      local[i] = i + 10;
   return local;
}

// Modifies an array.
void Test2(array< MyNativeClass * >^ local) {
   for (int i = 0 ; i < ARRAY_SIZE ; i++)
      local[i] -> m_i = local[i] -> m_i + 2;
}

int main() {
   int i;

   // Declares an array of user-defined reference types
   // and uses a function to initialize.
   array< MyClass^ >^ MyClass0;
   MyClass0 = Test0();

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyClass0[{0}] = {1}", i, MyClass0[i] -> m_i);
   Console::WriteLine();

   // Declares an array of value types and uses a function to initialize.
   array< Int32 >^ IntArray;
   IntArray = Test1();

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("IntArray[{0}] = {1}", i, IntArray[i]);
   Console::WriteLine();

   // Declares and initializes an array of user-defined
   // reference types.
   array< MyClass^ >^ MyClass1 = gcnew array< MyClass^ >(ARRAY_SIZE);
   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      MyClass1[i] = gcnew MyClass;
      MyClass1[i] -> m_i = i + 20;
   }

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyClass1[{0}] = {1}", i, MyClass1[i] -> m_i);
   Console::WriteLine();

   // Declares and initializes an array of pointers to a native type.
   array< MyNativeClass * >^ MyClass2 = gcnew array<
      MyNativeClass * >(ARRAY_SIZE);
   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      MyClass2[i] = new MyNativeClass();
      MyClass2[i] -> m_i = i + 30;
   }

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyClass2[{0}] = {1}", i, MyClass2[i]->m_i);
   Console::WriteLine();

   Test2(MyClass2);
   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyClass2[{0}] = {1}", i, MyClass2[i]->m_i);
   Console::WriteLine();

   delete[] MyClass2[0];
   delete[] MyClass2[1];

   // Declares and initializes an array of user-defined value types.
   array< MyStruct >^ MyStruct1 = gcnew array< MyStruct >(ARRAY_SIZE);
   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      MyStruct1[i] = MyStruct();
      MyStruct1[i].m_i = i + 40;
   }

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyStruct1[{0}] = {1}", i, MyStruct1[i].m_i);
}
```

```Output
MyClass0[0] = 0
MyClass0[1] = 1

IntArray[0] = 10
IntArray[1] = 11

MyClass1[0] = 20
MyClass1[1] = 21

MyClass2[0] = 30
MyClass2[1] = 31

MyClass2[0] = 32
MyClass2[1] = 33

MyStruct1[0] = 40
MyStruct1[1] = 41
```

下一個範例示範如何在一維 managed 陣列上執行彙總初始化。

```cpp
// mcppv2_sdarrays_aggregate_init.cpp
// compile with: /clr
using namespace System;

ref class G {
public:
   G(int i) {}
};

value class V {
public:
   V(int i) {}
};

class N {
public:
   N(int i) {}
};

int main() {
   // Aggregate initialize a single-dimension managed array.
   array<String^>^ gc1 = gcnew array<String^>{"one", "two", "three"};
   array<String^>^ gc2 = {"one", "two", "three"};

   array<G^>^ gc3 = gcnew array<G^>{gcnew G(0), gcnew G(1), gcnew G(2)};
   array<G^>^ gc4 = {gcnew G(0), gcnew G(1), gcnew G(2)};

   array<Int32>^ value1 = gcnew array<Int32>{0, 1, 2};
   array<Int32>^ value2 = {0, 1, 2};

   array<V>^ value3 = gcnew array<V>{V(0), V(1), V(2)};
   array<V>^ value4 = {V(0), V(1), V(2)};

   array<N*>^ native1 = gcnew array<N*>{new N(0), new N(1), new N(2)};
   array<N*>^ native2 = {new N(0), new N(1), new N(2)};
}
```

```Output
MyClass0[0, 0] = 0
MyClass0[0, 1] = 0
MyClass0[1, 0] = 1
MyClass0[1, 1] = 1

IntArray[0, 0] = 10
IntArray[0, 1] = 10
IntArray[1, 0] = 11
IntArray[1, 1] = 11
```

此範例示範如何在多維度的 managed 陣列上執行彙總初始設定：

```cpp
// mcppv2_mdarrays_aggregate_initialization.cpp
// compile with: /clr
using namespace System;

ref class G {
public:
   G(int i) {}
};

value class V {
public:
   V(int i) {}
};

class N {
public:
   N(int i) {}
};

int main() {
   // Aggregate initialize a multidimension managed array.
   array<String^, 2>^ gc1 = gcnew array<String^, 2>{ {"one", "two"},
       {"three", "four"} };
   array<String^, 2>^ gc2 = { {"one", "two"}, {"three", "four"} };

   array<G^, 2>^ gc3 = gcnew array<G^, 2>{ {gcnew G(0), gcnew G(1)},
       {gcnew G(2), gcnew G(3)} };
   array<G^, 2>^ gc4 = { {gcnew G(0), gcnew G(1)}, {gcnew G(2), gcnew G(3)} };

   array<Int32, 2>^ value1 = gcnew array<Int32, 2>{ {0, 1}, {2, 3} };
   array<Int32, 2>^ value2 = { {0, 1}, {2, 3} };

   array<V, 2>^ value3 = gcnew array<V, 2>{ {V(0), V(1)}, {V(2), V(3)} };
   array<V, 2>^ value4 = { {V(0), V(1)}, {V(2), V(3)} };

   array<N*, 2>^ native1 = gcnew array<N*, 2>{ {new N(0), new N(1)},
      {new N(2), new N(3)} };
   array<N*, 2>^ native2 = { {new N(0), new N(1)}, {new N(2), new N(3)} };
}
```

## <a name="jagged-arrays"></a>不規則陣列

本節說明如何建立 managed 陣列的參考、 值和原生指標類型的一維陣列。 此外，它也會示範如何從函式中傳回 managed 陣列的一維陣列，以及如何將單一維度陣列做為引數傳遞至函式。

```cpp
// mcppv2_array_of_arrays.cpp
// compile with: /clr
using namespace System;

#define ARRAY_SIZE 2

value struct MyStruct {
   int m_i;
};

ref class MyClass {
public:
   int m_i;
};

// Returns an array of managed arrays of a reference type.
array<array<MyClass^>^>^ Test0() {
   int size_of_array = 4;
   array<array<MyClass^>^>^ local = gcnew
      array<array<MyClass^>^>(ARRAY_SIZE);

   for (int i = 0 ; i < ARRAY_SIZE ; i++, size_of_array += 4) {
      local[i] = gcnew array<MyClass^>(size_of_array);
      for (int k = 0; k < size_of_array ; k++) {
         local[i][k] = gcnew MyClass;
         local[i][k] -> m_i = i;
      }
   }

   return local;
}

// Returns a managed array of Int32.
array<array<Int32>^>^ Test1() {
   int i;
   array<array<Int32>^>^ local = gcnew array<array< Int32 >^>(ARRAY_SIZE);

   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      local[i] = gcnew array< Int32 >(ARRAY_SIZE);
         for ( int j = 0 ; j < ARRAY_SIZE ; j++ )
            local[i][j] = i + 10;
   }
   return local;
}

int main() {
   int i, j;

   // Declares an array of user-defined reference types
   // and uses a function to initialize.
   array< array< MyClass^ >^ >^ MyClass0;
   MyClass0 = Test0();

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      for ( j = 0 ; j < ARRAY_SIZE ; j++ )
         Console::WriteLine("MyClass0[{0}] = {1}", i, MyClass0[i][j] -> m_i);
   Console::WriteLine();

   // Declares an array of value types and uses a function to initialize.
   array< array< Int32 >^ >^ IntArray;
   IntArray = Test1();

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      for (j = 0 ; j < ARRAY_SIZE ; j++)
      Console::WriteLine("IntArray[{0}] = {1}", i, IntArray[i][j]);
   Console::WriteLine();

   // Declares and initializes an array of user-defined value types.
   array< MyStruct >^ MyStruct1 = gcnew array< MyStruct >(ARRAY_SIZE);
   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      MyStruct1[i] = MyStruct();
      MyStruct1[i].m_i = i + 40;
   }

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine(MyStruct1[i].m_i);
}
```

```Output
MyClass0[0] = 0
MyClass0[0] = 0
MyClass0[1] = 1
MyClass0[1] = 1

IntArray[0] = 10
IntArray[0] = 10
IntArray[1] = 11
IntArray[1] = 11

40
41
```

下列範例示範如何執行彙總初始化不規則陣列。

```cpp
// mcppv2_array_of_arrays_aggregate_init.cpp
// compile with: /clr
using namespace System;
#define ARRAY_SIZE 2
int size_of_array = 4;
int count = 0;

ref class MyClass {
public:
   int m_i;
};

struct MyNativeClass {
   int m_i;
};

int main() {
   // Declares an array of user-defined reference types
   // and performs an aggregate initialization.
   array< array< MyClass^ >^ >^ MyClass0 = gcnew array<array<MyClass^>^> {
      gcnew array<MyClass^>{ gcnew MyClass(), gcnew MyClass() },
      gcnew array<MyClass^>{ gcnew MyClass(), gcnew MyClass() }
   };

   for ( int i = 0 ; i < ARRAY_SIZE ; i++, size_of_array += 4 )
      for ( int k = 0 ; k < ARRAY_SIZE ; k++ )
         MyClass0[i][k] -> m_i = i;

   for ( int i = 0 ; i < ARRAY_SIZE ; i++ )
      for ( int j = 0 ; j < ARRAY_SIZE ; j++ )
         Console::WriteLine("MyClass0[{0}] = {1}", i, MyClass0[i][j] -> m_i);
   Console::WriteLine();

   // Declares an array of value types and performs an aggregate initialization.
   array< array< Int32 >^ >^ IntArray = gcnew array<array< Int32 >^> {
      gcnew array<Int32>{1,2},
      gcnew array<Int32>{3,4,5}
   };

   for each ( array<int>^ outer in IntArray ) {
      Console::Write("[");

      for each( int i in outer )
         Console::Write(" {0}", i);

      Console::Write(" ]");
      Console::WriteLine();
   }
   Console::WriteLine();

   // Declares and initializes an array of pointers to a native type.
   array<array< MyNativeClass * >^ > ^ MyClass2 =
      gcnew array<array< MyNativeClass * > ^> {
         gcnew array<MyNativeClass *>{ new MyNativeClass(), new MyNativeClass() },
         gcnew array<MyNativeClass *>{ new MyNativeClass(), new MyNativeClass(), new MyNativeClass() }
      };

   for each ( array<MyNativeClass *> ^ outer in MyClass2 )
      for each( MyNativeClass* i in outer )
         i->m_i = count++;

   for each ( array<MyNativeClass *> ^ outer in MyClass2 ) {
      Console::Write("[");
      for each( MyNativeClass* i in outer )
         Console::Write(" {0}", i->m_i);
      Console::Write(" ]");
      Console::WriteLine();
   }
   Console::WriteLine();

   // Declares and initializes an array of two-dimensional arrays of strings.
   array<array<String ^,2> ^> ^gc3 = gcnew array<array<String ^,2> ^>{
      gcnew array<String ^>{ {"a","b"}, {"c", "d"}, {"e","f"} },
      gcnew array<String ^>{ {"g", "h"} }
   };

   for each ( array<String^, 2> ^ outer in gc3 ){
      Console::Write("[");
      for each( String ^ i in outer )
         Console::Write(" {0}", i);
      Console::Write(" ]");
      Console::WriteLine();
   }
}
```

```Output
MyClass0[0] = 0
MyClass0[0] = 0
MyClass0[1] = 1
MyClass0[1] = 1

[ 1 2 ]
[ 3 4 5 ]

[ 0 1 ]
[ 2 3 4 ]

[ a b c d e f ]
[ g h ]
```

## <a name="managed-arrays-as-template-type-parameters"></a>Managed 陣列當做樣板類型參數

此範例示範如何使用 managed 的陣列做為範本的參數：

```cpp
// mcppv2_template_type_params.cpp
// compile with: /clr
using namespace System;
template <class T>
class TA {
public:
   array<array<T>^>^ f() {
      array<array<T>^>^ larr = gcnew array<array<T>^>(10);
      return larr;
   }
};

int main() {
   int retval = 0;
   TA<array<array<Int32>^>^>* ta1 = new TA<array<array<Int32>^>^>();
   array<array<array<array<Int32>^>^>^>^ larr = ta1->f();
   retval += larr->Length - 10;
   Console::WriteLine("Return Code: {0}", retval);
}
```

```Output
Return Code: 0
```

## <a name="typedefs-for-managed-arrays"></a>managed 陣列的 typedef

此範例示範如何讓 managed 陣列的 typedef:

```cpp
// mcppv2_typedef_arrays.cpp
// compile with: /clr
using namespace System;
ref class G {};

typedef array<array<G^>^> jagged_array;

int main() {
   jagged_array ^ MyArr = gcnew jagged_array (10);
}
```

## <a name="sorting-arrays"></a>排序陣列

不同於標準 c + + 陣列，managed 的陣列隱含衍生自其繼承的通用行為陣列基底類別。 例如，`Sort`方法，可用來排序任何陣列中的項目。

對於包含基本的內建類型的陣列，您可以呼叫`Sort`方法。 您可以覆寫的排序準則，這動作需要時您想要排序陣列的複雜型別。 在此情況下，陣列項目類型必須實作<xref:System.IComparable.CompareTo%2A>方法。

```cpp
// array_sort.cpp
// compile with: /clr
using namespace System;

int main() {
   array<int>^ a = { 5, 4, 1, 3, 2 };
   Array::Sort( a );
   for (int i=0; i < a->Length; i++)
      Console::Write("{0} ", a[i] );
}
```

## <a name="sorting-arrays-by-using-custom-criteria"></a>藉由使用自訂準則排序陣列

若要排序陣列，其中包含基本的內建類型，只要呼叫`Array::Sort`方法。 不過，以排序陣列，包含複雜型別，或若要覆寫預設的排序準則，覆寫<xref:System.IComparable.CompareTo%2A>方法。

在下列範例中，結構名為`Element`衍生自<xref:System.IComparable>，並提供寫入<xref:System.IComparable.CompareTo%2A>兩個整數的平均值做為排序準則的方法。

```cpp
using namespace System;

value struct Element : public IComparable {
   int v1, v2;

   virtual int CompareTo(Object^ obj) {
      Element^ o = dynamic_cast<Element^>(obj);
      if (o) {
         int thisAverage = (v1 + v2) / 2;
         int thatAverage = (o->v1 + o->v2) / 2;
         if (thisAverage < thatAverage)
            return -1;
         else if (thisAverage > thatAverage)
            return 1;
         return 0;
         }
      else
         throw gcnew ArgumentException
      ("Object must be of type 'Element'");
   }
};

int main() {
   array<Element>^ a = gcnew array<Element>(10);
   Random^ r = gcnew Random;

   for (int i=0; i < a->Length; i++) {
      a[i].v1 = r->Next() % 100;
      a[i].v2 = r->Next() % 100;
   }

   Array::Sort( a );
   for (int i=0; i < a->Length; i++) {
      int v1 = a[i].v1;
      int v2 = a[i].v2;
      int v = (v1 + v2) / 2;
      Console::WriteLine("{0}  (({1}+{2})/2) ", v, v1, v2);
   }
}
```

## <a name="array-covariance"></a>陣列共變數

指定參考類別 D 具有直接或間接基底類別 B，D 型別的陣列可以指派給陣列變數的型別 b。

```cpp
// clr_array_covariance.cpp
// compile with: /clr
using namespace System;

int main() {
   // String derives from Object.
   array<Object^>^ oa = gcnew array<String^>(20);
}
```

指派給陣列項目應該與指派相容具有動態類型的陣列。 指派至具有不相容的類型的陣列項目會導致`System::ArrayTypeMismatchException`擲回。

陣列共變數不適用於實值類別類型的陣列。 例如，無法轉換的 Int32 陣列物件 ^ 陣列，甚至不是藉由使用 boxing。

```cpp
// clr_array_covariance2.cpp
// compile with: /clr
using namespace System;

ref struct Base { int i; };
ref struct Derived  : Base {};
ref struct Derived2 : Base {};
ref struct Derived3 : Derived {};
ref struct Other { short s; };

int main() {
   // Derived* d[] = new Derived*[100];
   array<Derived^> ^ d = gcnew array<Derived^>(100);

   // ok by array covariance
   array<Base ^> ^  b = d;

   // invalid
   // b[0] = new Other;

   // error (runtime exception)
   // b[1] = gcnew Derived2;

   // error (runtime exception),
   // must be "at least" a Derived.
   // b[0] = gcnew Base;

   b[1] = gcnew Derived;
   b[0] = gcnew Derived3;
}
```

## <a name="see-also"></a>另請參閱

[陣列](../windows/arrays-cpp-component-extensions.md)