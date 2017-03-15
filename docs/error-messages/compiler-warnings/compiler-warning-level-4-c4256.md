---
title: "編譯器警告 (層級 4) C4256 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4256"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4256"
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 4) C4256
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 具有虛擬基底類別的建構函式有 '...'; 呼叫可能與舊版的 Visual C\+\+ 不相容  
  
 可能不相容。  
  
 請試想下列程式碼範例。  如果建構函式 S2::S2 \(int i, …\)的定義中使用 Visual C\+\+ 編譯器版本在 7 版之前所編譯，不過下列範例使用目前的版本來編譯，因為特殊大小寫呼叫慣例變更，對建構函式的呼叫 S3 會無法正確運作。  如果兩個都是以 Visual C\+\+ 6.0 編譯的，呼叫也不會正常運作，除非沒有參數傳入省略。  
  
 若要修正這項警告，  
  
1.  不要在建構函式中使用省略。  
  
2.  確定專案中所有的元件都是以目前版本 \(包括任何可能定義或參考此類別的程式庫\) 建置的，然後用 [warning](../../preprocessor/warning.md) Pragma 關閉警告。  
  
 下列範例會產生 C4256：  
  
```  
// C4256.cpp  
// compile with: /W4  
// #pragma warning(disable : 4256)  
struct S1  
{  
};  
  
struct S2: virtual public S1  
{  
   S2( int i, ... )    // C4256  
   {  
      i = 0;  
   }  
   /*  
   // try the following line instead  
   S2( int i)  
   {  
      i = 0;  
   }  
   */  
};  
  
void func1()  
{  
   S2 S3( 2, 1, 2 );   // C4256  
   // try the following line instead  
   // S2 S3( 2 );  
}  
  
int main()  
{  
}  
```