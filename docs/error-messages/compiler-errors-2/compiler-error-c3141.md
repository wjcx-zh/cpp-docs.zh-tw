---
title: "編譯器錯誤 C3141 | Microsoft Docs"
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
  - "C3141"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3141"
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3141
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'interface\_name' : 介面只支援公用繼承  
  
 以 [interface \(或 \_\_interface\)](../../cpp/interface.md) 關鍵字定義的介面只支援公用 \(Public\) 繼承。  
  
 下列範例會產生 C3141：  
  
```  
// C3141.cpp  
__interface IBase {};  
__interface IDerived1 : protected IBase {};  // C3141  
__interface IDerived2 : private IBase {};    // C3141  
```