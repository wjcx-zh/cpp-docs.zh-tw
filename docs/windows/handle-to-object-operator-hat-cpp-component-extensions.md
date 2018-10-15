---
title: 物件控制代碼運算子 (^) (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d7fb74dcff370b314df5da5428ba3e406023acbe
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327969"
---
# <a name="handle-to-object-operator---ccli-and-ccx"></a>物件控制代碼運算子 (^) (C + + /cli 和 C + + /CX)

*控制代碼宣告子*(`^`，唸成"hat")，修改型別[規範](../cpp/overview-of-declarators.md)來表示，宣告的物件時，應會自動刪除系統判斷此物件是無法再存取。

## <a name="accessing-the-declared-object"></a>存取宣告的物件

以控制代碼宣告子宣告的變數作用如同物件指標。 然而，此變數指向整個物件，無法指向物件的成員，也不支援指標算術。 使用間接取值運算子 (`*`) 存取物件，使用箭號成員存取運算子 (`->`) 存取物件的成員。

## <a name="windows-runtime"></a>Windows 執行階段

編譯器會使用 COM*參考計數*機制來判斷是否物件已不再使用，且可以刪除。 究其原因是，從 Windows 執行階段介面衍生的物件實際上是 COM 物件。 當物件建立或複製時參考計數遞增，當物件設定為 null 或超出範圍時則遞減。 如果參考計數歸零，物件會自動並立即刪除。

控制代碼宣告子的優點是，在 COM 中，必須明確地管理物件的參考計數 (這個程序相當繁瑣且易錯)， 也就是，若要遞增和遞減參考計數，必須呼叫物件的 AddRef() 和 Release() 方法。 不過，如果您宣告物件控制代碼宣告子使用時，編譯器會產生自動調整參考計數的程式碼。

如需如何具現化物件的資訊，請參閱[ref 新](../windows/ref-new-gcnew-cpp-component-extensions.md)。

## <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

系統會使用 CLR*記憶體回收行程*機制來判斷是否物件已不再使用，且可以刪除。 Common Language Runtime 會維持用以配置物件的堆積，並使用您程式中的 Managed 參考 (變數)，指出物件在堆積上的位置。 當物件不再使用時，物件在堆積上佔用的記憶體會被釋放。 記憶體回收行程會定期壓縮堆積，以更有效地利用釋放的記憶體。 壓縮堆積可能會移動堆積上的物件，而使得 Managed 參考所參考的位置無效。 然而，記憶體回收行程知道所有 Managed 參考的位置，而且會自動更新以指出物件在堆積上目前的位置。

因為原生 C++ 指標 (`*`) 和參考 (`&`) 不是 Managed 參考，所以記憶體回收行程無法自動更新它們所指的位址。 若要解決這個問題，請使用控制代碼宣告子，指定記憶體回收行程知道且會自動更新的變數。

如需詳細資訊，請參閱 <<c0> [ 如何： 以原生類型宣告處理](../dotnet/how-to-declare-handles-in-native-types.md)。

### <a name="examples"></a>範例

這個範例示範如何在 Managed 堆積上建立參考型別的執行個體。  這個範例也示範如何以一個控制代碼初始化另一個控制代碼，導致在 Managed、記憶體回收堆積上同一個物件有兩個參考。 請注意，指派[nullptr](../windows/nullptr-cpp-component-extensions.md)給一個控制代碼不會標記為記憶體回收的物件。

```cpp
// mcppv2_handle.cpp
// compile with: /clr
ref class MyClass {
public:
   MyClass() : i(){}
   int i;
   void Test() {
      i++;
      System::Console::WriteLine(i);
   }
};

int main() {
   MyClass ^ p_MyClass = gcnew MyClass;
   p_MyClass->Test();

   MyClass ^ p_MyClass2;
   p_MyClass2 = p_MyClass;

   p_MyClass = nullptr;
   p_MyClass2->Test();
}
```

```Output
1
2
```

下列範例示範如何在 Managed 堆積上宣告物件控制代碼，而物件的型別為 Boxed 實值型別。 這個範例也會示範如何從 Boxed 物件取得實值型別。

```cpp
// mcppv2_handle_2.cpp
// compile with: /clr
using namespace System;

void Test(Object^ o) {
   Int32^ i = dynamic_cast<Int32^>(o);

   if(i)  
      Console::WriteLine(i);
   else
      Console::WriteLine("Not a boxed int");
}

int main() {
   String^ str = "test";
   Test(str);

   int n = 100;
   Test(n);
}
```

```Output
Not a boxed int
100
```

這個範例示範使用通用的 c + + 慣用語`void*`指標指向任意物件會取代`Object^`，其中可包含任何參考類別的控制代碼。 這個範例也會示範所有型別 (例如陣列和委派) 都可以轉換為物件控制代碼。

```cpp
// mcppv2_handle_3.cpp
// compile with: /clr
using namespace System;
using namespace System::Collections;
public delegate void MyDel();
ref class MyClass {
public:
   void Test() {}
};

void Test(Object ^ x) {
   Console::WriteLine("Type is {0}", x->GetType());
}

int main() {
   // handle to Object can hold any ref type
   Object ^ h_MyClass = gcnew MyClass;

   ArrayList ^ arr = gcnew ArrayList();
   arr->Add(gcnew MyClass);

   h_MyClass = dynamic_cast<MyClass ^>(arr[0]);
   Test(arr);

   Int32 ^ bi = 1;
   Test(bi);

   MyClass ^ h_MyClass2 = gcnew MyClass;

   MyDel^ DelInst = gcnew MyDel(h_MyClass2, &MyClass::Test);
   Test(DelInst);
}
```

```Output
Type is System.Collections.ArrayList

Type is System.Int32

Type is MyDel
```

這個範例示範控制代碼可以是取值的，而且可透過已取值的控制代碼存取成員。

```cpp
// mcppv2_handle_4.cpp
// compile with: /clr
using namespace System;
value struct DataCollection {
private:
   int Size;
   array<String^>^ x;

public:
   DataCollection(int i) : Size(i) {
      x = gcnew array<String^>(Size);
      for (int i = 0 ; i < Size ; i++)  
         x[i] = i.ToString();
   }

   void f(int Item) {
      if (Item >= Size)  
      {
         System::Console::WriteLine("Cannot access array element {0}, size is {1}", Item, Size);
         return;
      }
      else
         System::Console::WriteLine("Array value: {0}", x[Item]);
   }
};

void f(DataCollection y, int Item) {
   y.f(Item);
}

int main() {
   DataCollection ^ a = gcnew DataCollection(10);
   f(*a, 7);   // dereference a handle, return handle's object
   (*a).f(11);   // access member via dereferenced handle
}
```

```Output
Array value: 7

Cannot access array element 11, size is 10
```

這個範例示範原生參考 (`&`) 無法繫結至**int**的 managed 類型的成員作為**int**可能儲存在記憶體回收堆積，並不會追蹤原生參考managed 堆積中的物件移動。 解決方法是使用區域變數，或將 `&` 變更為 `%`，使其成為追蹤參考。

```cpp
// mcppv2_handle_5.cpp
// compile with: /clr
ref struct A {
   void Test(unsigned int &){}
   void Test2(unsigned int %){}
   unsigned int i;
};

int main() {
   A a;
   a.i = 9;
   a.Test(a.i);   // C2664
   a.Test2(a.i);   // OK

   unsigned int j = 0;
   a.Test(j);   // OK
}
```

### <a name="requirements"></a>需求

編譯器選項：`/clr`

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)<br/>
[追蹤參考運算子](../windows/tracking-reference-operator-cpp-component-extensions.md)