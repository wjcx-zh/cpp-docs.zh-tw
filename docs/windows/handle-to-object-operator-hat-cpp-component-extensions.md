---
title: "物件控制代碼運算子 (^) （c + + 元件擴充功能） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e760181f48e4bfd197514b152701e94ac6e94a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="handle-to-object-operator---c-component-extensions"></a>物件控制代碼運算子 (^) (C++ 元件擴充功能)
*控制代碼宣告子*(`^`，唸成"hat")，修改型別[規範](../cpp/overview-of-declarators.md)來表示，在宣告的物件應該自動刪除當系統決定此物件是無法存取。  
  
## <a name="accessing-the-declared-object"></a>存取宣告的物件  
 以控制代碼宣告子宣告的變數作用如同物件指標。 然而，此變數指向整個物件，無法指向物件的成員，也不支援指標算術。 使用間接取值運算子 (`*`) 存取物件，使用箭號成員存取運算子 (`->`) 存取物件的成員。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 編譯器會使用 COM*參考計數*機制，以判斷物件不再使用且可以刪除。 究其原因是，從 Windows 執行階段介面衍生的物件實際上是 COM 物件。 當物件建立或複製時參考計數遞增，當物件設定為 null 或超出範圍時則遞減。 如果參考計數歸零，物件會自動並立即刪除。  
  
 控制代碼宣告子的優點是，在 COM 中，必須明確地管理物件的參考計數 (這個程序相當繁瑣且易錯)， 也就是，若要遞增和遞減參考計數，必須呼叫物件的 AddRef() 和 Release() 方法。 不過，如果以控制代碼宣告子宣告物件，Visual C++ 編譯器會產生自動調整參考計數的程式碼。  
  
 如需如何具現化物件的資訊，請參閱[ref 新](../windows/ref-new-gcnew-cpp-component-extensions.md)。  
  
## <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 系統會使用 CLR*記憶體回收行程*機制，以判斷物件不再使用且可以刪除。 Common Language Runtime 會維持用以配置物件的堆積，並使用您程式中的 Managed 參考 (變數)，指出物件在堆積上的位置。 當物件不再使用時，物件在堆積上佔用的記憶體會被釋放。 記憶體回收行程會定期壓縮堆積，以更有效地利用釋放的記憶體。 壓縮堆積可能會移動堆積上的物件，而使得 Managed 參考所參考的位置無效。 然而，記憶體回收行程知道所有 Managed 參考的位置，而且會自動更新以指出物件在堆積上目前的位置。  
  
 因為原生 C++ 指標 (`*`) 和參考 (`&`) 不是 Managed 參考，所以記憶體回收行程無法自動更新它們所指的位址。 若要解決這個問題，請使用控制代碼宣告子，指定記憶體回收行程知道且會自動更新的變數。  
  
 在 Visual C++ 2002 和 Visual C++ 2003 中，`__gc *` 是用來宣告在 Managed 堆積上的物件。  在新語法中，`^` 取代 `__gc *`。  
  
 如需詳細資訊，請參閱[How to： 在原生類型中宣告處理](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
### <a name="examples"></a>範例  
 **範例**  
  
 這個範例示範如何在 Managed 堆積上建立參考型別的執行個體。  這個範例也示範如何以一個控制代碼初始化另一個控制代碼，導致在 Managed、記憶體回收堆積上同一個物件有兩個參考。 請注意，指定[nullptr](../windows/nullptr-cpp-component-extensions.md)至一個控制代碼不會將標示為記憶體回收的物件。  
  
```  
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
  
 **輸出**  
  
```Output  
1  
2  
```  
  
 **範例**  
  
 下列範例示範如何在 Managed 堆積上宣告物件控制代碼，而物件的型別為 Boxed 實值型別。 這個範例也會示範如何從 Boxed 物件取得實值型別。  
  
```  
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
  
 **輸出**  
  
```Output  
Not a boxed int  
100  
```  
  
 **範例**  
  
 這個範例示範如何將使用 void* 指標指向任意物件的 C++ 常見慣用語，取代為可儲存任何參考類別控制代碼的 Object^。 這個範例也會示範所有型別 (例如陣列和委派) 都可以轉換為物件控制代碼。  
  
```  
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
  
 **輸出**  
  
```Output  
Type is System.Collections.ArrayList  
  
Type is System.Int32  
  
Type is MyDel  
```  
  
 **範例**  
  
 這個範例示範控制代碼可以是取值的，而且可透過已取值的控制代碼存取成員。  
  
```  
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
  
 **輸出**  
  
```Output  
Array value: 7  
  
Cannot access array element 11, size is 10  
```  
  
 **範例**  
  
 這個範例示範原生參考 (`&`) 無法繫結到 Managed 型別的 `int` 成員，因為 `int` 可能儲存在記憶體回收堆積中，而原生參考不會追蹤 Managed 堆積上的物件移動。 解決方法是使用區域變數，或將 `&` 變更為 `%`，使其成為追蹤參考。  
  
```  
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
 編譯器選項： **/clr**  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)   
 [追蹤參考運算子](../windows/tracking-reference-operator-cpp-component-extensions.md)