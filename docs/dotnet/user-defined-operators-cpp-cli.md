---
title: "使用者定義的運算子 (C++/CLI) | Microsoft Docs"
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
  - "/clr 底下的使用者定義運算子"
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用者定義的運算子 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Managed 型別的使用者定義的運算子允許為靜態成員或是執行個體成員，或在全域範圍。  不過，只有靜態運算子是在以 Visual C\+\+ 之外的語言撰寫的用戶端之中繼資料是可取得的。  
  
 在參考型別中，其中一個靜態的使用者定義運算子的參數必須是下列其中一個：  
  
-   對封入型別的執行個體之控制代碼 \(`type` ^\)。  
  
-   對封入型別執行個體的控制代碼之參考型別 \(Reference Type\) 的間接取值 \(`type`^& 或 type^%\)。  
  
 在實值型別中，其中一個靜態的使用者定義運算子的參數必須是下列其中一個：  
  
-   與封入值型別相同。  
  
-   對封入型別的指標型別間接取值 \(`type`^\)。  
  
-   對封入型別的參考型別 \(Reference Type\) 之間接取值 \(`type`% 或 `type`&\)。  
  
-   對控制代碼的參考型別 \(Reference Type\) 之間接取值 \(`type`^% 或 `type`^&\)。  
  
 您可以定義下列運算子：  
  
|運算子|一元\/二元表單?|  
|---------|---------------|  
|\!|一元|  
|\!\=|Binary|  
|%|Binary|  
|&|一元和二元|  
|&&|Binary|  
|\*|一元和二元|  
|\+|一元和二元|  
|\+\+|一元|  
|,|Binary|  
|\-|一元和二元|  
|\-\-|一元|  
|\-\>|一元|  
|\/|Binary|  
|\<|Binary|  
|\<\<|Binary|  
|\<\=|Binary|  
|\=|Binary|  
|\=\=|Binary|  
|\>|Binary|  
|\>\=|Binary|  
|\>\>|Binary|  
|^|Binary|  
|false|一元|  
|true|一元|  
|&#124;|Binary|  
|&#124;&#124;|Binary|  
|~|一元|  
  
## 範例  
  
```  
// mcppv2_user-defined_operators.cpp  
// compile with: /clr  
using namespace System;  
public ref struct X {  
   X(int i) : m_i(i) {}  
   X() {}  
  
   int m_i;  
  
   // static, binary, user-defined operator  
   static X ^ operator + (X^ me, int i) {  
      return (gcnew X(me -> m_i + i));  
   }  
  
   // instance, binary, user-defined operator  
   X^ operator -( int i ) {  
      return gcnew X(this->m_i - i);  
   }  
  
   // instance, unary, user-defined pre-increment operator  
   X^ operator ++() {  
      return gcnew X(this->m_i++);  
   }  
  
   // instance, unary, user-defined post-increment operator  
   X^ operator ++(int i) {  
      return gcnew X(this->m_i++);  
   }  
  
   // static, unary user-defined pre- and post-increment operator  
   static X^ operator-- (X^ me) {  
      return (gcnew X(me -> m_i - 1));  
   }  
};  
  
int main() {  
   X ^hX = gcnew X(-5);  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX + 1;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX - (-1);  
   System::Console::WriteLine(hX -> m_i);  
  
   ++hX;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX++;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX--;  
   System::Console::WriteLine(hX -> m_i);  
  
   --hX;  
   System::Console::WriteLine(hX -> m_i);  
}  
```  
  
  **\-5**  
**\-4**  
**\-3**  
**\-2**  
**\-1**  
**\-2**  
**\-3**   
## 範例  
 下列範例將示範運算子複合，當您使用 **\/clr** 編譯時才可使用。  如果沒有定義二元運算子的工作表單，運算子複合會建立它，其中指派運算子左方會有一個 CLR 型別。  
  
```  
// mcppv2_user-defined_operators_2.cpp  
// compile with: /clr  
ref struct A {  
   A(int n) : m_n(n) {};  
   static A^ operator + (A^ r1, A^ r2) {  
      return gcnew A( r1->m_n + r2->m_n);  
   };  
   int m_n;  
};  
  
int main() {  
   A^ a1 = gcnew A(10);  
   A^ a2 = gcnew A(20);  
  
   a1 += a2;   // a1 = a1 + a2   += not defined in source  
   System::Console::WriteLine(a1->m_n);  
}  
```  
  
  **30**   
## 請參閱  
 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)