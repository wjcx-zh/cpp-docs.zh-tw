---
title: "參考類型的 C++ 堆疊語意 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "參考類型, 的 C++ 堆疊語意"
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 參考類型的 C++ 堆疊語意
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 `new` 運算子，在 Visual C\+\+ 2005 以前，參考型別的執行個體只能建立，會在記憶體回收堆積上的物件。  不過，您現在可以建立參考型別的執行個體使用您用來建立原生型別執行個體在堆疊上的語法相同。  因此，您不需要使用 [ref new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) 建立參考型別的物件。  然後，當物件超出範圍時，編譯器會呼叫物件的解構函式。  
  
## 備註  
 使用堆疊語意時，就會參考型別的執行個體，則編譯器會在內部建立在記憶體回收堆積的執行個體 \(使用 `gcnew`\)。  
  
 當函式的簽章或傳回型別是由值參考型別的執行個體，則函式會在中繼資料中標記為需要特殊處理 \(與 modreq\)。  這個特殊處理由 Visual C\+\+ 用戶端目前只提供;其他語言目前不支援使用參考型別建立搭配使用的消耗的函式或資料。  
  
 其中一個理由使用 `gcnew` \(動態配置\) 而不是堆疊語意為，但如果該型別沒有解構函式。  此外，除了 Visual C\+\+ 之外，如果您想要讓函式由語言使用參考型別會以函式簽章的堆疊語意是不可能的。  
  
 編譯器不會產生參考型別的複製建構函式。  因此，如果您在簽章使用由值參考型別的函式，您必須定義參考型別的複製建構函式。  參考型別的複製建構函式有下列形式的簽章: `R(R%){}`。  
  
 編譯器不會產生參考型別的預設指派運算子。  指派運算子可讓您建立物件使用堆疊語意並以使用堆疊語意建立的現有物件。  參考型別的指派運算子有下列形式的簽章: `void operator=( R% ){}`。  
  
 如果型別的解構函式版本重要資源和您為參考型別使用堆疊語意，您不需要明確呼叫解構函式 \(或呼叫 `delete`\)。  如需參考型別中可為解構函式的型別之詳細資訊，請參閱[Visual C\+\+ 中的解構函式和完成項](../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
 由編譯器產生的指派運算子會遵循通常 Standard C\+\+ 規則與下列動作:  
  
-   型別為控制代碼參考型別的任何非靜態資料成員是淺層複製 \(視為型別是指標\) 的非靜態資料成員。  
  
-   如果型別為實值型別的非靜態資料成員是淺層複製。  
  
-   型別是參考型別的執行個體的非靜態資料成員會叫用呼叫參考型別的複製建構函式。  
  
 編譯器也會提供 `%` 一元運算子轉換使用堆疊語意建立的參考型別的執行個體返回其基礎控制代碼的型別。  
  
 下列參考型別不能為與搭配使用的使用:  
  
-   [delegate](../windows/delegate-cpp-component-extensions.md)  
  
-   [Arrays](../windows/arrays-cpp-component-extensions.md)  
  
-   <xref:System.String>  
  
## 範例  
  
### 說明  
 下列程式碼範例示範如何宣告參考型別的執行個體搭配使用的，指派運算子和複製建構函式如何運作以及如何初始化使用堆疊語意建立的參考型別的追蹤參考。  
  
### 程式碼  
  
```  
// stack_semantics_for_reference_types.cpp  
// compile with: /clr  
ref class R {  
public:  
   int i;  
   R(){}  
  
   // assignment operator  
   void operator=(R% r) {  
      i = r.i;  
   }  
  
   // copy constructor  
   R(R% r) : i(r.i) {}  
};  
  
void Test(R r) {}   // requires copy constructor  
  
int main() {  
   R r1;  
   r1.i = 98;  
  
   R r2(r1);   // requires copy constructor  
   System::Console::WriteLine(r1.i);  
   System::Console::WriteLine(r2.i);  
  
   // use % unary operator to convert instance using stack semantics  
   // to its underlying handle  
   R ^ r3 = %r1;  
   System::Console::WriteLine(r3->i);  
  
   Test(r1);  
  
   R r4;  
   R r5;  
   r5.i = 13;  
   r4 = r5;   // requires a user-defined assignment operator  
   System::Console::WriteLine(r4.i);  
  
   // initialize tracking reference  
   R % r6 = r4;  
   System::Console::WriteLine(r6.i);  
}  
```  
  
### Output  
  
```  
98  
98  
98  
13  
13  
```  
  
## 請參閱  
 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)