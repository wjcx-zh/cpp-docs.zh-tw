---
title: "編譯器警告 (層級 4) C4714 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4714"
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4714
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標記為 \_\_forceinline 的函式 'function' 無法被內嵌  
  
 已選取提供的函式進行內嵌擴充，但編譯器未進行內嵌。  
  
 雖然 `__forceinline` 對編譯器的指示強於 `__inline`，編譯器還是會判斷是否進行內嵌，但沒有 Heuristic 會被用來決定內嵌此函式的益處。  
  
 在某些情況下，編譯器因為技術方面的因素而不會內嵌特定的函式。  例如，編譯器不會內嵌：  
  
-   會使 SEH 和 C\+\+ EH 混淆的函式。  
  
-   當 \-GX\/EHs\/EHa 啟動時，以傳值方式傳送複製建構物件的某些函式。  
  
-   當 \-GX\/EHs\/EHa 啟動時，以傳值方式傳回無法還原物件的函式。  
  
-   當不用 \-Og\/Ox\/O1\/O2 編譯時，具有內嵌組件的函式。  
  
-   具有變數引數清單的函式。  
  
-   具有 **try** \(C\+\+ 例外狀況處理\) 陳述式的函式。  
  
 下列範例會產生 C4714：  
  
```  
// C4714.cpp  
// compile with: /Ob1 /GX /W4  
__forceinline void func1()  
{  
   try  
   {  
   }  
   catch (...)  
   {  
   }  
}  
  
void func2()  
{  
   func1();   // C4714  
}  
  
int main()  
{  
}  
```