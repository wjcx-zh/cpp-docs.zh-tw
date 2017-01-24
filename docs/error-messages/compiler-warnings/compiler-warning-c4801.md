---
title: "編譯器警告 C4801 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4801"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4801"
ms.assetid: 05b29dff-15ef-42ca-9712-dc993afc4fd6
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4801
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳址方式的傳回值無法驗證: 原因  
  
 您不能將追蹤參考存放於本機變數之中，然後以可驗證方式傳回。  
  
 參考只有在能夠由驗證器從建立追蹤到傳回點時，以及它是陣列元素或類別成員的參考時，才能以可驗證方式傳回。  
  
 如需詳細資訊，請參閱[Peverify.exe \(PEVerify Tool\)](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md)。  
  
 參考必須從建立到傳回都保持在堆疊上才可驗證。  
  
 C4801 一定視同一個錯誤。您可以使用 `#pragma warning` 或 **\/wd** 關閉這個警告。如需詳細資訊，請參閱 [warning](../../preprocessor/warning.md) 或 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won \(警告層級\)](../../build/reference/compiler-option-warning-level.md)。  
  
## 範例  
 如果驗證器看不到所用的位址，則將產生 C4801，因此它必須假設可能是無法驗證的參考。  下列範例會產生 C4801：  
  
```  
// C4801.cpp  
// compile with: /clr:safe /c  
int% f(int% p) {  
   return p;   // C4801  
}  
```  
  
## 範例  
 下列範例會產生 C4801：  
  
```  
// C4801_b.cpp  
// compile with: /clr:safe /c  
  
int% f(int i, array<int>^ ar) {  
   int x;  
   int% bri = x;   // cannot return a byref to a local.  
   if (i < ar->Length) {  
      bri = ar[i];   // this byref is ok.  
   }  
  
   return bri;   // C4801 not returned within the basic block  
}  
```  
  
## 範例  
 如果嘗試取值 \(Dereference\) 並傳回 try 區塊中的參考值，也會發生 C4801。  這樣會產生無法驗證的程式碼，因為 try 區塊的結尾已清除堆疊，並終結堆疊上的任何傳回值。  應該取值參考型別並指定給變數，以確保不會擲回例外狀況。  然後在函式結尾，再度取值參考型別，並將它傳回。  
  
 下列範例會產生 C4801：  
  
```  
// C4801_c.cpp  
// compile with: /clr:safe  
using namespace System;  
  
ref class StackEmptyException : public System::Exception {};  
ref class StackFullException : public System::Exception {};  
  
template <typename T>  
ref struct Stack {  
  
   Stack() {  
      topElem = -1;   // initialize stack  
      stackPtr = gcnew array<T>(10);  
   }  
  
   void push(const T%);  
   T% top();  
  
private:  
   int topElem;    
   array<T>^ stackPtr;    
};  
  
template <typename T>   
T% Stack<T>::top() {  
   try {  
      return stackPtr[topElem];   // C4801  
      // Try the following line instead.  
      // T% deadstore = stackPtr[topElem] ;  
   }  
  
   catch (System::IndexOutOfRangeException ^ e) {  
      throw gcnew StackEmptyException();  
   }  
  
   catch (System::Exception ^ e) {  
      throw;  
   }  
  
   return stackPtr[topElem] ;  
}  
  
int main() {  
   typedef Stack<Int32> IntStack;  
   IntStack ^ is = gcnew IntStack();  
  
   int i = 1;  
   while (1) {  
      try {  
         is->push(i++);  
      }  
      catch (System::Exception ^ e) {  
         break;  
      }  
      Console::Write("{0} ", is->top());  
   }  
}  
```