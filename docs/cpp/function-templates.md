---
title: "函式樣板 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式樣板"
  - "函式樣板, 關於函式樣板"
  - "範本, 函式"
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函式樣板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別樣板會根據在具現化時傳遞至類別的類型引數，定義一系列相關的類別。  函式樣板與類別樣板類似，但其定義一系列的函式。  使用函式樣板時，您可以指定一組根據相同的程式碼，但在不同類型或類別上運作的函式。  下列函式樣板會交換兩個項目：  
  
```  
// function_templates1.cpp  
template< class T > void MySwap( T& a, T& b ) {  
   T c(a);   
   a = b;   
   b = c;  
}  
int main() {  
}  
```  
  
 此程式碼會定義一系列交換引數值的函式。  從這個樣板中，您可以產生交換 `int` 和 **long** 類型以及使用者定義類型的函式。  如果已正確定義類別的複製建構函式和指派運算子，則 `MySwap` 甚至會交換類別。  
  
 此外，因為編譯器會在編譯時期得知 `a` 和 `b` 參數的類型，因此函式樣板將不會讓您交換不同類型的物件。  
  
 雖然使用 void 指標可讓這個函式由非樣板化的函式執行，但樣板版本仍是 typesafe。  請考慮下列呼叫：  
  
```  
int j = 10;  
int k = 18;  
CString Hello = "Hello, Windows!";  
MySwap( j, k );          //OK  
MySwap( j, Hello );      //error  
```  
  
 因為編譯器無法產生具有不同類型之參數的 `MySwap` 函式，因此第二個 `MySwap` 呼叫會觸發編譯時期錯誤。  如果使用了 void 指標，則會正確編譯兩個函式呼叫，不過，函式在執行階段將無法正常運作。  
  
 您可以明確指定函式樣板的樣板引數。  例如：  
  
```  
// function_templates2.cpp  
template<class T> void f(T) {}  
int main(int j) {  
   f<char>(j);   // Generate the specialization f(char).  
   // If not explicitly specified, f(int) would be deduced.  
}  
```  
  
 明確指定樣板引數時，一般會完成隱含轉換，以便將函式引數轉換為對應函式樣板參數的類型。  在上述範例中，編譯器會將 \(`char j`\) 轉換為 `int` 類型。  
  
## 請參閱  
 [樣板](../cpp/templates-cpp.md)   
 [函式樣板具現化](../cpp/function-template-instantiation.md)   
 [明確初始化](../cpp/explicit-instantiation.md)   
 [函式樣板的明確特製化](../cpp/explicit-specialization-of-function-templates.md)