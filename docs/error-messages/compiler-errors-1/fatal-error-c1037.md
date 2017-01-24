---
title: "嚴重錯誤 C1037 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1037"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1037"
ms.assetid: 79103bca-ccfb-42e7-aef9-9b90c15b162f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1037
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法開啟目的檔名稱  
  
 找不到 [\/Fo](../../build/reference/fo-object-file-name.md) 所指定的目的檔。  
  
### 透過檢查下列可能原因進行修正  
  
1.  無效的檔名。  
  
2.  記憶體不足，無法開啟檔案。  
  
3.  另一個處理序正在使用檔案。  
  
4.  唯讀檔具有相同的名稱。  
  
 在 Visual C\+\+ .NET \(編譯器的 1300 版\) 中，有一個錯誤是檔名 \(或檔名的目錄路徑\) 包含 MBCS 字元時，需要正確地設定使用者地區設定。 設定系統地區設定是不夠的；必須設定使用者地區設定，才能處理 MBCS 字元。