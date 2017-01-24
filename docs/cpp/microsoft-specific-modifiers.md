---
title: "Microsoft 專有的修飾詞 | Microsoft Docs"
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
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Microsoft 專有的修飾詞
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本節將描述下列各層面 Microsoft 專有的 C\+\+ 擴充功能：  
  
-   [基底定址](../cpp/based-addressing.md)，使用指標做為其他指標可以位移之基底的做法  
  
-   [函式呼叫慣例](../cpp/calling-conventions.md)  
  
-   以 [\_\_declspec](../cpp/declspec.md) 關鍵字宣告的擴充儲存類別屬性  
  
-   [\_\_w64](../cpp/w64.md) 關鍵字  
  
 許多 Microsoft 專有關鍵字可用來將宣告子修改為衍生類型。  如需宣告子的詳細資訊，請參閱[宣告子](http://msdn.microsoft.com/zh-tw/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)。  
  
### Microsoft 專有關鍵字  
  
|關鍵字|意義|是否用來形成衍生類型？|  
|---------|--------|-----------------|  
|[\_\_based](../cpp/based-grammar.md)|後面的名稱會將 32 位元位移宣告為宣告中包含的 32 位元基底。|是|  
|[\_\_cdecl](../cpp/cdecl.md)|後面的名稱會使用 C 命名和呼叫慣例。|是|  
|[\_\_declspec](../cpp/declspec.md)|後面的名稱會指定 Microsoft 專有的儲存類別屬性。|否|  
|[\_\_fastcall](../cpp/fastcall.md)|後面的名稱會將函式宣告為使用暫存器 \(如果有的話\)，而不使用可進行引數傳遞的堆疊。|是|  
|[\_\_restrict](../cpp/extension-restrict.md)|類似於 \_\_declspec\([restrict](../cpp/restrict.md)\)，但是用於變數。|否|  
|[\_\_stdcall](../cpp/stdcall.md)|後面的名稱會指定採用標準呼叫慣例的函式。|是|  
|[\_\_w64](../cpp/w64.md)|在 64 位元編譯器上將資料類型標示為較大。|否|  
|[\_\_unaligned](../cpp/unaligned.md)|指出某個類型或其他資料的指標未對齊。|否|  
|[\_\_vectorcall](../cpp/vectorcall.md)|後面的名稱會將函式宣告為只要有暫存器可用即使用暫存器 \(包括 SSE 暫存器\)，而不使用可進行引數傳遞的堆疊。|是|  
  
## 請參閱  
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)