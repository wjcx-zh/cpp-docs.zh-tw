---
title: "嚴重錯誤 C1092 | Microsoft Docs"
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
  - "C1092"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1092"
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1092
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編輯後繼續不支援對資料型別的變更；需要建置  
  
 您在上次成功組建時變更或加入了一個資料型別。  
  
-   編輯後繼續並不支援現有資料型別 \(包括類別、結構或列舉定義\) 的變更。  您必須停止偵錯，並建置應用程式。  
  
-   編輯後繼續在程式資料庫檔 \(例如，vc*x*0.pdb，此處的 *x* 是指正在使用 Visual C\+\+ 主要版本\) 是唯讀時，不支援新加入的資料型別。  若要加入資料型別，編譯器必須在寫入模式開啟 .pdb 檔。  
  
### 若要不結束目前的偵錯工作階段來移除這個錯誤  
  
1.  請將資料型別改回錯誤發生之前的狀態。  
  
2.  從 \[**偵錯**\] 功能表選擇 \[**套用程式碼變更**\]。  
  
### 若要移除此錯誤但不更改您的程式碼  
  
1.  從 \[**偵錯**\] 功能中表選擇 \[**停止偵錯**\]。  
  
2.  從 \[**建置**\] 功能表上，選擇 \[**建置**\]。  
  
 如需詳細資訊，請參閱[支援的程式碼變更](../Topic/Supported%20Code%20Changes%20\(C++\).md)。