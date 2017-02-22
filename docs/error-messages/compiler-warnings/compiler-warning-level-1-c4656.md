---
title: "編譯器警告 (層級 1) C4656 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4656"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4656"
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 1) C4656
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' : 自上次組建之後資料型別有新增或改變，或其他處有不同的定義  
  
 自上次成功地建置之後，您已加入或變更資料型別，更新了您的來源程式碼。  \[編輯後繼續\] 並不支援現有資料型別的變更。  
  
 此警告之後會出現[嚴重錯誤 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。  如需詳細資訊，請參閱[支援的程式碼變更](../Topic/Supported%20Code%20Changes%20\(C++\).md)。  
  
### 若要移除此警告但不結束目前的偵錯工作階段  
  
1.  請將資料型別改回錯誤發生之前的狀態。  
  
2.  從 \[偵錯\] 功能表選擇 \[套用程式碼變更\]。  
  
### 若要移除此錯誤但不更改您的程式碼  
  
1.  從 \[偵錯\] 功能表中選擇 \[**停止偵錯**\]。  
  
2.  從 \[**建置**\] 功能表上，選擇 \[**建置**\]。