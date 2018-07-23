---
title: pin_ptr (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
dev_langs:
- C++
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: afc99a352e0bde7918cab460293ff23061377551
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880162"
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)
宣告*pin 指標*，這僅適用於 common language runtime。  
  
## <a name="all-runtimes"></a>所有執行階段  
 (這個語言功能沒有適用所有執行階段的備註。)  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 （這個語言功能不支援在 Windows 執行階段）。  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 A *pin 指標*可防止物件的內部指標指向記憶體回收堆積上移動。 也就是通用語言執行平台不會變更 pin 指標的值。 這是必要的當您將傳遞 managed 類別的位址至 unmanaged 函式，以便位址不會變更非預期地在解析 unmanaged 函式呼叫的期間。  
  
### <a name="syntax"></a>語法  
  
```cpp  
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;  
```  
  
### <a name="parameters"></a>參數  
 *cv_qualifier*  
 `const` 或`volatile`限定詞。 根據預設，pin 指標是`volatile`。 它是重複，但不是錯誤來宣告 pin 指標`volatile`。  
  
 *type*  
 `initializer` 的類型。  
  
 *var*  
 `pin_ptr` 變數的名稱。  
  
 *initializer*  
 參考類型的成員，Managed 陣列的元素，或是其他任何可以指派至原生指標的物件。  
  
### <a name="remarks"></a>備註  
 A`pin_ptr`代表功能的原生指標的超集。 因此，任何可以指派給原生指標的項目也可指派給`pin_ptr`。 內部指標可以執行與原生指標相同的一組作業，包括比較和指標算術。  
  
 物件或子物件的 managed 類別可以釘選，在此情況下 common language runtime 不會移動它在記憶體回收期間。 這主要用途是要當做 unmanaged 函式呼叫的實質參數，傳遞至 managed 資料的指標。 在集合的週期中，執行階段會檢查為 pin 指標建立的中繼資料，並不會移動它所指向的項目。  
  
 固定物件也釘選它值的欄位。也就是基本類型的欄位或值類型。 不過，將欄位宣告藉由追蹤控制代碼 (`%`) 不會固定。  
  
 釘選受管理物件中定義的子物件的效果釘選整個物件。  
  
 如果 pin 指標會指派以指向新的值，指向上一個執行個體已不再視為固定。  
  
 已釘選物件時，才`pin_ptr`指向它。 其 pin 指標超出範圍，或設為當物件不再固定[nullptr](../windows/nullptr-cpp-component-extensions.md)。 之後`pin_ptr`超出範圍，已釘選的物件可以藉由記憶體回收行程移動堆積中。 仍然指向該物件任何原生指標將不會更新，並取消參考其中一個可能會引發例外狀況無法復原。  
  
 如果沒有 pin 指標指向的物件 (所有 pin 指標超出範圍，已重新指派至指向其他物件，或已指派[nullptr](../windows/nullptr-cpp-component-extensions.md))，不保證物件固定。  
  
 Pin 指標可以指向參考控制代碼、 實值型別或 boxed 的類型控制代碼、 managed 型別的成員或 managed 陣列的項目。 它無法指向參考類型。  
  
 位址`pin_ptr`指向原生的物件會導致未定義的行為。  
  
 Pin 指標在堆疊上只能宣告為非靜態區域變數。  
  
 Pin 指標不能當做：  
  
-   函式參數  
  
-   函式的傳回型別  
  
-   類別成員  
  
-   轉換目標類型。  
  
 `pin_ptr` 處於`cli`命名空間。 如需詳細資訊，請參閱[平台、 default 和 cli 命名空間](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
 如需內部指標的詳細資訊，請參閱[interior_ptr (C + + /CLI)](../windows/interior-ptr-cpp-cli.md)。  
  
 如需 pin 指標的詳細資訊，請參閱[How to: Pin 指標和陣列](../windows/how-to-pin-pointers-and-arrays.md)和[如何： 宣告固定指標和實值類型](../windows/how-to-declare-pinning-pointers-and-value-types.md)。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 下列範例會使用`pin_ptr`限制陣列的第一個元素的位置。  
  
```  
// pin_ptr_1.cpp  
// compile with: /clr   
using namespace System;  
#define SIZE 10  
  
#pragma unmanaged  
// native function that initializes an array  
void native_function(int* p) {  
   for(int i = 0 ; i < 10 ; i++)  
    p[i] = i;  
}  
#pragma managed  
  
public ref class A {  
private:  
   array<int>^ arr;   // CLR integer array  
  
public:  
   A() {  
      arr = gcnew array<int>(SIZE);  
   }  
  
   void load() {  
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr  
   int* np = p;   // pointer to the first element in arr  
   native_function(np);   // pass pointer to native function  
   }  
  
   int sum() {  
      int total = 0;  
      for (int i = 0 ; i < SIZE ; i++)  
         total += arr[i];  
      return total;  
   }  
};  
  
int main() {  
   A^ a = gcnew A;  
   a->load();   // initialize managed array using the native function  
   Console::WriteLine(a->sum());  
}  
```  
  
 **輸出**  
  
```Output  
45  
```  
  
 **範例**  
  
 下列範例顯示的內部指標可以轉換成 pin 指標，和傳址運算子的傳回類型 (`&`) 是內部指標，如果運算元為 managed 堆積上。  
  
```  
// pin_ptr_2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   G() : i(1) {}  
   int i;  
};  
  
ref struct H {  
   H() : j(2) {}  
   int j;  
};  
  
int main() {  
   G ^ g = gcnew G;   // g is a whole reference object pointer  
   H ^ h = gcnew H;  
  
   interior_ptr<int> l = &(g->i);   // l is interior pointer  
  
   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer  
  
   k = l;   // ok  
   Console::WriteLine(*k);  
};  
```  
  
 **輸出**  
  
```Output  
1  
```  
  
 **範例**  
  
 下列範例顯示的 pin 指標可以轉換成其他類型。  
  
```  
// pin_ptr_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class ManagedType {  
public:  
   int i;  
};  
  
int main() {  
   ManagedType ^mt = gcnew ManagedType;  
   pin_ptr<int> pt = &mt->i;  
   *pt = 8;  
   Console::WriteLine(mt->i);  
  
   char *pc = ( char* ) pt;  
   *pc = 255;  
   Console::WriteLine(mt->i);  
}  
```  
  
 **輸出**  
  
```Output  
8  
255  
```