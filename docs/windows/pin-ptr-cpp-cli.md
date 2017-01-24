---
title: "pin_ptr (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "pin_ptr_cpp"
  - "stdcli::language::pin_ptr"
  - "pin_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pinning pointers"
  - "pin_ptr keyword [C++]"
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
caps.latest.revision: 28
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# pin_ptr (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宣告*Pin 指標*，只使用與 Common Language Runtime。  
  
## 所有執行階段  
 \(這個語言功能沒有適用於所有執行階段的備註\)。  
  
## Windows Runtime \- Windows 執行階段  
 \(這個語言功能在 Windows 執行階段不支援\)  
  
## Common Language Runtime  
 *Pin 指標*是防止物件會繼續執行記憶體回收的堆積的內部指標。  即 Common Language Runtime 不會變更 Pin 指標的值。  利用這種方式將 Managed 類別的位址傳遞至 Unmanaged 函式是必須的，所以位址不會在解析 Unmanaged 函式呼叫時意外變更。  
  
### 語法  
  
```cpp  
[cli::]pin_ptr<cv_qualifier type> var = &initializer;  
```  
  
### 參數  
 *cv\_qualifier*  
 `const` 或 `volatile` 限定詞。  根據預設， Pin 指標是 `volatile`。  它是重複，但不是錯誤宣告 Pin 指標 `volatile`。  
  
 *type*  
 `initializer` 的型別。  
  
 *var*  
 `pin_ptr`變數的名稱。  
  
 *initializer*  
 參考型別，項目的 Managed 陣列，或任何其他的成員可以指派到原生指標的物件。  
  
### 備註  
 `pin_ptr` 表示原生指標功能的超集。  因此，可以指派至原生指標的任何物件也可以指派至 `pin_ptr`。  內部指標被允許執行同一組作業與原生指標，包括比較和指標算術。  
  
 在 Common Language Runtime 不會在記憶體回收期間的情況下，將它移至 Managed 類別的物件或子物件可停駐。  對這個用途是將指標傳遞給 Managed 資料做為 Unmanaged 函式呼叫的實質參數。  在集合週期，執行階段會檢查建立的中繼資料所指向的 Pin 指標，並不會移動項目。  
  
 固定物件也修正其值欄位；即原始或實值型別欄位。  然而，追蹤宣告的欄位控制代碼 \(`%`\) 沒有內建。  
  
 固定在 Managed 物件定義的子物件具有固定整個物件的效果。  
  
 如果 Pin 指標重新指派給對新值，前一個執行個體指向不再視為固定。  
  
 物件只有在為 `pin_ptr` 時固定。  物件不再固定，當它 Pin 指標超出範圍時，或設定為 [nullptr](../windows/nullptr-cpp-component-extensions.md)。  在 `pin_ptr` 超出範圍之後， Pin 物件可在堆積由記憶體回收行程移動。  仍然指向物件的任何原生指標不會更新和取值其中一個可能引發無法復原的例外狀況。  
  
 如果物件的 Pin 指標點 \(所有內建的指標超出的範圍，重新指派給其他物件的點或者是指定 [nullptr](../windows/nullptr-cpp-component-extensions.md)\)，物件不保證不固定。  
  
 Pin 指標可以指向 Managed 型別的控制代碼取值、實值型別或 Boxed 型別控制代碼，成員或 Managed 陣列的元素。  它無法指向參考型別。  
  
 取得指向原生物件 `pin_ptr` 的位址會產生未定義的行為。  
  
 Pin 指標只能宣告在堆疊上的非靜態區域變數。  
  
 Pin 指標無法使用如下:  
  
-   函式參數  
  
-   函式的傳回型別。  
  
-   類別的成員  
  
-   轉換的目標類型。  
  
 `pin_ptr`在`cli`命名空間中。  如需詳細資訊，請參閱[Platform, default, and cli Namespaces](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。  
  
 如需內部指標的詳細資訊，請參閱[interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)。  
  
 如需 Pin 指標的詳細資訊，請參閱[How to: Pin Pointers and Arrays](../windows/how-to-pin-pointers-and-arrays.md) 和[How to: Declare Pinning Pointers and Value Types](../windows/how-to-declare-pinning-pointers-and-value-types.md)。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列範例會使用 `pin_ptr` 限制陣列的第一個項目的位置。  
  
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
  
 **Output**  
  
  **45** **範例**  
  
 下列範例顯示內部指標可以轉換為 Pin 指標，且傳址運算子 \(`&`\) 的傳回型別是內部指標，當運算元在 Managed 堆積上。  
  
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
  
 **Output**  
  
 **1** **範例**  
  
 下列範例中，示範了 Pin 指標可以轉換成其他型別。  
  
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
   pin_ptr< int > pt = &mt->i;  
   *pt = 8;  
   Console::WriteLine(mt->i);  
  
   char *pc = ( char* ) pt;  
   *pc = 255;  
   Console::WriteLine(mt->i);  
}  
```  
  
 **Output**  
  
 **8**   
**255**