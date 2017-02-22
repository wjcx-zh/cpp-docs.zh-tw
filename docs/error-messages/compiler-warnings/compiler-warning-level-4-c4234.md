---
title: "編譯器警告 (層級 4) C4234 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4234"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4234"
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 4) C4234
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充 : 保留 'keyword' 關鍵字供日後使用  
  
 編譯器尚未實作您使用的關鍵字。  
  
 此警告會自動提升為錯誤。  如果您要修改此行為，請使用 [\#pragma warning](../../preprocessor/warning.md)。  例如，在您的來源程式碼檔案，將 C4234 歸類為層級 4 的警告事件：  
  
```  
#pragma warning(2:4234)  
```  
  
 。