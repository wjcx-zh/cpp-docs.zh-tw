---
title: "函式樣板呼叫的多載解析 | Microsoft Docs"
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
  - "函式樣板多載解析"
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函式樣板呼叫的多載解析
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

函式樣板可以多載相同名稱的非樣板函式。  在這種情節中，函式呼叫會先使用樣板引數推算解析，以具現化具有唯一特製化的函式樣板。  如果樣板引數推算失敗，才會考慮使用其他函式多載解析呼叫。  這些其他多載也稱為候選集合，包括非樣板函式和其他具現化的函式樣板。  如果樣板引數推算成功，則會依照多載解析的規則將產生的函式與其他函式進行比較，以判斷最符合的項目。  如需詳細資訊，請參閱[多載](../misc/overloading-cpp.md)和[引數比對](../misc/argument-matching.md)。  
  
## 範例  
 如果非樣板函式是與樣板函式一樣理想的相符項目，則會選擇非樣板函式 \(除非明確指定樣板引數\)，如同下列範例中的呼叫 `f(1, 1)`。  
  
```  
// template_name_resolution9.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void f(int, int) { cout << "f(int, int)" << endl; }  
void f(char, char) { cout << "f(char, char)" << endl; }  
  
template <class T1, class T2>  
void f(T1, T2)  
{  
   cout << "void f(T1, T2)" << endl;  
};  
  
int main()  
{  
   f(1, 1);   // Equally good match; choose the nontemplate function.  
   f('a', 1); // Chooses the template function.  
   f<int, int>(2, 2);  // Template arguments explicitly specified.  
}  
```  
  
  **f\(int, int\)**  
**void f\(T1, T2\)**  
**void f\(T1, T2\)**   
## 範例  
 下一個範例將說明，如果非樣板函式需要轉換，則建議您使用完全相符的樣板函式。  
  
```  
// template_name_resolution10.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void f(int, int) { cout << "f(int, int)" << endl; }  
  
template <class T1, class T2>  
void f(T1, T2)  
{  
   cout << "void f(T1, T2)" << endl;  
};  
  
int main()  
{  
   long l = 0;  
   int i = 0;  
   // Call the template function f(long, int) because f(int, int)  
   // would require a conversion from long to int.  
   f(l, i);  
}  
```  
  
  **void f\(T1, T2\)**   
## 請參閱  
 [名稱解析](../cpp/templates-and-name-resolution.md)   
 [typename](../cpp/typename.md)   
 [樣板引數推斷](../Topic/Template%20Argument%20Deduction.md)