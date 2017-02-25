---
title: "編譯器警告 (層級 1) C4655 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4655"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4655"
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4655
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**'**   
 ***符號* ' : 自上次組建之後變數類型有新的改變，或其他處有不同的定義**  
  
 自從上次成功組建後，您已變更或加入新的資料類型。 \[編輯後繼續\] 不支援對現有資料類型的變更。  
  
 這個警告後面接著[嚴重錯誤 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 如需詳細資訊，請參閱[支援的程式碼變更](../Topic/Supported%20Code%20Changes%20\(C++\).md)。  
  
### 移除這個警告，而不結束目前的偵錯工作階段  
  
1.  請將資料類型改回錯誤之前的狀態。  
  
2.  從 \[偵錯\] 功能表選擇 \[套用程式碼變更\]。  
  
### 移除這個警告，而不變更您的程式碼  
  
1.  從 \[偵錯\] 功能表選擇 \[停止偵錯\]。  
  
2.  從 \[建置\] 功能表選擇 \[建置\]。