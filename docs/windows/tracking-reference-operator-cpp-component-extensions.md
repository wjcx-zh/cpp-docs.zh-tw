---
title: "Tracking Reference Operator (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tracking references"
  - "% tracking reference [C++]"
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
caps.latest.revision: 31
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tracking Reference Operator (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「*追蹤參考*」\(Tracking Reference\) \(`%`\) 作用如同一般的 C\+\+ 參考 \(`&`\)，不過當物件指派給追蹤參考時，物件的參考計數會遞增。  
  
## 所有平台  
 追蹤參考有下列特性：  
  
-   將物件指派給追蹤參考會導致物件的參考計數遞增。  
  
-   原生參考 \(&\) 是當您取值 \* 時的結果，  追蹤參考 \(%\) 是當您取值 ^ 時的結果。  只要您有物件的 %，物件就會保持存留在記憶體中。  
  
-   點 \(`.`\) 成員存取運算子是用來存取物件的成員。  
  
-   追蹤參考對實值型別和控制代碼 \(例如 `String^`\) 是有效的。  
  
-   不可指派 null 或 `nullptr` 值給追蹤參考。  追蹤參考可視需求重新指派給另一個有效物件多次。  
  
-   追蹤參考不可做為一元取址運算子。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 追蹤參考的行為類似標準的 C\+\+ 參考，差異在於 % 是參考計數。  下列程式碼片段示範如何在 % 和 ^ 類型之間轉換：  
  
```  
Foo^ spFoo = ref new Foo();  
Foo% srFoo = *spFoo;  
Foo^ spFoo2 = %srFoo;  
```  
  
 下列範例顯示如何將 ^ 傳遞至採用 % 的函式。  
  
```  
  
ref class Foo sealed {};  
  
    // internal or private  
    void UseFooHelper(Foo% f)  
    {  
        auto x = %f;  
    }  
  
    // public method on ABI boundary  
    void UseFoo(Foo^ f)  
    {  
        if (f != nullptr) { UseFooHelper(*f); }  
    }  
  
```  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 在 C\+\+\/CLI 中，繫結至記憶體回收堆積上的 CLR 類型物件時，可使用控制代碼的追蹤參考。  
  
 在 CLR，當記憶體回收行程移動所參考的物件時，會自動更新追蹤參考變數的值。  
  
 只能在堆疊上宣告追蹤參考。  追蹤參考不可以是類別的成員。  
  
 在記憶體回收堆積上的物件不可能有原生 C\+\+ 參考。  
  
 如需 C\+\+\/CLI 追蹤參考的詳細資訊，請參閱：  
  
-   [如何：在 C\+\+\/CLI 中使用追蹤參考](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)  
  
-   [如何：使用追蹤參考和實值類型](../misc/how-to-use-tracking-references-and-value-types.md)  
  
-   [如何：使用追蹤參考和內部指標](../misc/how-to-use-tracking-references-and-interior-pointers.md)  
  
-   [如何：撰寫使用原生、值或參考參數的樣板函式](../misc/how-to-write-template-functions-that-take-native-value-or-reference-parameters.md)  
  
### 範例  
 **範例**  
  
 下列 C\+\+\/CLI 範例示範如何搭配使用追蹤參考與原生和 Managed 類型。  
  
```  
// tracking_reference_1.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   int i;  
};  
  
value struct MyStruct {  
   int k;  
};  
  
int main() {  
   MyClass ^ x = ref new MyClass;  
   MyClass ^% y = x;   // tracking reference handle to reference object   
  
   int %ti = x->i;   // tracking reference to member of reference type  
  
   int j = 0;  
   int %tj = j;   // tracking reference to object on the stack  
  
   int * pi = new int[2];  
   int % ti2 = pi[0];   // tracking reference to object on native heap  
  
   int *% tpi = pi;   // tracking reference to native pointer  
  
   MyStruct ^ x2 = ref new MyStruct;  
   MyStruct ^% y2 = x2;   // tracking reference to value object  
  
   MyStruct z;  
   int %tk = z.k;   // tracking reference to member of value type  
  
   delete[] pi;  
}  
  
```  
  
 **範例**  
  
 下列 C\+\+\/CLI 範例示範如何將追蹤參考繫結至陣列。  
  
```  
// tracking_reference_2.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   array<int> ^ a = ref new array< Int32 >(5);  
   a[0] = 21;  
   Console::WriteLine(a[0]);  
   array<int> ^% arr = a;  
   arr[0] = 222;  
   Console::WriteLine(a[0]);  
}  
```  
  
 **輸出**  
  
  **21**  
 **222**