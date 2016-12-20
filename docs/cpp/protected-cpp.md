---
title: "protected (C++) | Microsoft Docs"
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
  - "protected"
  - "protected_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "protected 關鍵字 [C++]"
  - "protected 關鍵字 [C++], 成員存取"
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# protected (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## 備註  
 `protected` 關鍵字會指定 *member\-list* 中，到下一個存取指定名稱 \(**public** 或 `private`\) 或類別定義結束之前的類別成員存取。  宣告為 `protected` 的類別成員只能用於下列各項：  
  
-   原本宣告這些成員之類別的成員函式。  
  
-   原本宣告這些成員之類別的 Friend。  
  
-   從原本宣告這些成員的類別中所衍生，具有 public 或 protected 存取權限的類別。  
  
-   直接以 private 方式衍生的類別，這些類別也具有對 protected 成員的 private 存取權限。  
  
 `protected` 關鍵字加在基底類別的名稱前面時，會將基底類別的 public 和 protected 成員指定為其衍生類別的 protected 成員。  
  
 Protected 成員不像 `private` 成員一樣為私用，只有其宣告所在類別中的成員才能存取，而且也不像 **public** 成員一樣為公用，可在所有函式中存取。  
  
 同時宣告為 **static** 的 protected 成員可供衍生類別的任何 friend 或成員函式存取。  未宣告為 **static** 的 protected 成員，只能透過衍生類別的指標、參考或物件供 friend 和成員函式在衍生類別中存取。  
  
 如需相關資訊，請參閱 [friend](../cpp/friend-cpp.md)、[public](../cpp/public-cpp.md)、[private](../cpp/private-cpp.md) 和[控制對類別成員的存取](../misc/controlling-access-to-class-members.md)中的成員存取表。  
  
## \/clr 專屬資訊  
 在 CLR 類型中，C\+\+ 存取指定名稱關鍵字 \(**public**、`private` 和 `protected`\) 可能會影響類型和方法在組件方面的可視性。  如需詳細資訊，請參閱[類型和成員可視性](../misc/type-and-member-visibility.md)。  
  
> [!NOTE]
>  以 [\/LN](../build/reference/ln-create-msil-module.md) 編譯的檔案不受這個行為影響。  在這種情況下，所有 Managed 類別 \(public 或 private\) 都會是可見。  
  
## \/clr 專屬資訊結束  
  
## 範例  
  
```  
// keyword_protected.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class X {  
public:  
   void setProtMemb( int i ) { m_protMemb = i; }  
   void Display() { cout << m_protMemb << endl; }  
protected:  
   int  m_protMemb;  
   void Protfunc() { cout << "\nAccess allowed\n"; }  
} x;  
  
class Y : public X {  
public:  
   void useProtfunc() { Protfunc(); }  
} y;  
  
int main() {  
   // x.m_protMemb;         error, m_protMemb is protected  
   x.setProtMemb( 0 );   // OK, uses public access function  
   x.Display();  
   y.setProtMemb( 5 );   // OK, uses public access function  
   y.Display();  
   // x.Protfunc();         error, Protfunc() is protected  
   y.useProtfunc();      // OK, uses public access function  
                        // in derived class  
}  
```  
  
## 請參閱  
 [控制對類別成員的存取](../misc/controlling-access-to-class-members.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)