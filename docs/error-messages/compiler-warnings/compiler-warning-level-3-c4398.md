---
title: "編譯器警告 (層級 3) C4398 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4398"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4398"
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 3) C4398
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : 處理序專屬全域物件可能無法對多重 appdomain 正確運作，請考慮使用 \_\_declspec\(appdomain\)  
  
 原生型別中有 [\_\_clrcall](../../cpp/clrcall.md) 呼叫慣例的虛擬函式導致建立應用程式定義域專屬 vtable。  這種變數用於多重應用程式定義域中時，可能無法正確地更正。  
  
 您可以用 **\/clr:pure** 編譯 \(預設值為 per appdomain 設定全域變數\)，或是明確標記變數 `__declspec(appdomain)`，就能解除這項警告。  
  
 如需詳細資訊，請參閱[appdomain](../../cpp/appdomain.md)與[應用程式定義域和 Visual C\+\+](../../dotnet/application-domains-and-visual-cpp.md)。  
  
## 範例  
 下列範例會產生 C4398。  
  
```  
// C4398.cpp  
// compile with: /clr /W3 /c  
struct S {  
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall  
};  
  
S glob_s;   // C4398  
__declspec(appdomain) S glob_s2;   // OK  
```