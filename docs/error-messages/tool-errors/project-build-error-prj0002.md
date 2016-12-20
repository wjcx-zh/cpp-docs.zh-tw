---
title: "專案建置錯誤 PRJ0002 | Microsoft Docs"
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
  - "PRJ0002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0002"
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置錯誤 PRJ0002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 'command line' \(命令列\) 傳回的錯誤結果。  
  
 由 \[**屬性頁**\] 對話方塊內的使用者輸入所形成的 ***command line*** 命令傳回了一個錯誤碼，但 \[輸出\] 視窗中不會出現任何資訊。  
  
 這個錯誤的解決方式視產生錯誤的工具而定。  針對 MIDL，如果已定義 \/o \(重新導向輸出\)，您對出錯的原因大致就會有一點概念。  
  
 未提供失敗狀況之資訊的批次 \(Batch\) 檔 \(例如，自訂建置步驟或建置事件\) 也可能是造成這個錯誤的原因。