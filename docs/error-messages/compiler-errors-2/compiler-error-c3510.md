---
title: "編譯器錯誤 C3510 | Microsoft Docs"
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
  - "C3510"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3510"
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3510
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到相依型別程式庫 'type\_lib'  
  
 [no\_registry](../../preprocessor/no-registry.md) 和 [auto\_search](../../preprocessor/auto-search.md) 已傳遞給 `#import`，但編譯器找不到參考的型別程式庫。  
  
 若要解決這項錯誤，請確定所有型別程式庫和參考的型別程式都可供編譯器使用。  
  
 下列範例會產生 C3510：  
  
 假設建置了下列兩個型別程式庫，而且已刪除了 C3510a.tlb，或 C3510a.tlb 不在路徑上。  
  
```  
// C3510a.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]  
library C3510aLib  
{  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]  
   enum E_C3510  
   {  
      one, two, three  
   };  
};  
```  
  
 然後，第二個型別程式庫的原始程式碼：  
  
```  
// C3510b.idl  
// post-build command: del /f C3510a.tlb  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]  
library C3510bLib  
{  
   importlib ("C3510a.tlb");  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]  
   struct S_C3510 {  
      enum E_C3510 e;  
   };  
};  
```  
  
 然後用戶端程式碼：  
  
```  
// C3510.cpp  
#import "c3510b.tlb" no_registry auto_search   // C3510  
int main() {  
   C3510aLib::S_C4336 ccc;  
}  
```