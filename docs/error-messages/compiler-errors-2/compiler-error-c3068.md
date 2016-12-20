---
title: "編譯器錯誤 C3068 | Microsoft Docs"
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
  - "C3068"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3068"
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3068
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 'naked' 函式不可包含必須在發生 C\+\+ 例外狀況時回溯的物件  
  
 編譯器無法在其中建立了暫存物件而擲回例外狀況，並指定了 C\+\+ 例外處理 \([\/EHsc](../../build/reference/eh-exception-handling-model.md)\) 的 [naked](../../cpp/naked-cpp.md) 函式上執行堆疊回溯。  
  
 若要解決這個錯誤，請至少執行下列一種方法：  
  
-   不要使用 \/EHsc 編譯。  
  
-   不要將函式標記為 `naked`。  
  
-   不要在函式中建立暫存物件。  
  
 如果函式在堆疊上建立了暫存物件，如果函式擲回例外狀況，而且如果啟用了 C\+\+ 例外處理，若擲回例外狀況，編譯器會清除堆疊。  
  
 擲回例外狀況時，編譯器會產生程式碼，呼叫初構 \(prolog\) 和終解 \(Epilog\) 程式碼，兩者都不在 naked 函式中，而是從函式中執行。  
  
## 範例  
 下列範例會產生 C3068：  
  
```  
// C3068.cpp  
// compile with: /EHsc  
// processor: x86  
class A {  
public:  
   A(){}  
   ~A(){}  
};  
  
void b(A){}  
  
__declspec(naked) void c() {  
   b(A());   // C3068   
};  
```