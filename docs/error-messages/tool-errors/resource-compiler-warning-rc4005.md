---
title: "資源編譯器警告 RC4005 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC4005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4005"
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 資源編譯器警告 RC4005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 巨集重複定義  
  
 識別項定義了兩次。  編譯器使用第二個巨集定義。  
  
 出現這項警告的原因，可能是由於同時在命令列和程式碼中以 `#define` 指示詞定義了一個巨集。  也可能是從包含檔案匯入的巨集所引起。  
  
 若要排除這項警告，可移除其中一個定義，或是在第二個定義之前使用 `#undef` 指示詞。