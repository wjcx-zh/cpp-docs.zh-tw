---
title: "編譯器錯誤 C2026 | Microsoft Docs"
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
  - "C2026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2026"
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字串太大，尾端字元已經截斷  
  
 字串長度超過 16380 單一位元組字元的限制。  
  
 在相鄰字串進行串連之前，字串長度不可超過 16380 單一位元組字元。  
  
 長度為此限制一半的 Unicode 字串也會產生此錯誤。  
  
 如果您依照下列方式定義一個字串，將產生 C2026：  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 您可以下列方式來分割字串：  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 您可能希望將特別大的字串常值 \(32K 或更大\) 儲存於自訂資源或外部檔案。  如需詳細資訊，請參閱[建立新的自訂或資料資源](../../mfc/creating-a-new-custom-or-data-resource.md)。