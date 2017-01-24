---
title: "編譯器警告 (層級 2) C4099 | Microsoft Docs"
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
  - "C4099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4099"
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 2) C4099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 型別名稱之前使用 'objecttype1'，現在則使用 'objecttype2'  
  
 宣告為結構的物件定義為類別，或是宣告為類別的物件定義為結構。  編譯器會使用定義中給定的型別。  
  
## 範例  
 下列範例會產生 C4099。  
  
```  
// C4099.cpp  
// compile with: /W2 /c  
struct A;  
class A {};   // C4099, use different identifer or use same object type  
```