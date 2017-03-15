---
title: "左值參考宣告子：&amp; | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 運算子, 參考運算子"
  - "參考運算子"
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 左值參考宣告子：&amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

保存物件的位址，但語法上的行為與物件相似。  
  
## 語法  
  
```  
  
type-id & cast-expression  
```  
  
## 備註  
 您可以將左值參考當做物件的另一個名稱。  左值參考宣告包含選擇性的指定名稱清單加上參考宣告符號。  參考必須經過初始化，而且不能變更。  
  
 只要物件的位址可以轉換為指定的指標類型，則該物件也可轉換為類似的參考類型。  例如，只要物件的位址可以轉換成 `char *` 類型，該物件也可轉換成 `char &` 類型。  
  
 請勿將參考宣告與[傳址運算子](../cpp/address-of-operator-amp.md)的使用混淆。  當 `&`*識別項* 接在類型 \(例如 `int` 或 `char`\) 之後時，*識別項* 會宣告為該類型的參考。  當 `&`*識別項* 未接在類型之後時，其用法即為傳址運算子的用法。  
  
## 範例  
 下列範例示範宣告 `Person` 物件和該物件之參考的參考宣告子。  因為 `rFriend` 是 `myFriend` 的參考，無論更新哪一個變數都會變更同一個物件。  
  
```  
// reference_declarator.cpp  
// compile with: /EHsc  
// Demonstrates the reference declarator.  
#include <iostream>  
using namespace std;  
  
struct Person  
{  
    char* Name;  
    short Age;  
};  
  
int main()  
{  
   // Declare a Person object.  
   Person myFriend;  
  
   // Declare a reference to the Person object.  
   Person& rFriend = myFriend;  
  
   // Set the fields of the Person object.  
   // Updating either variable changes the same object.  
   myFriend.Name = "Bill";  
   rFriend.Age = 40;  
  
   // Print the fields of the Person object to the console.  
   cout << rFriend.Name << " is " << myFriend.Age << endl;  
}  
```  
  
  **Bill 為 40**   
## 請參閱  
 [參考](../cpp/references-cpp.md)   
 [參考類型函式引數](../cpp/reference-type-function-arguments.md)   
 [參考類型函式傳回](../cpp/reference-type-function-returns.md)   
 [指標的參考](../cpp/references-to-pointers.md)