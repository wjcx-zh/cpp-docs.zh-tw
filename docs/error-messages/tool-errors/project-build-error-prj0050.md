---
title: "專案建置錯誤 PRJ0050 | Microsoft Docs"
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
  - "PRJ0050"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0050"
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置錯誤 PRJ0050
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法登錄輸出。請確定您擁有修改登錄的適當權限。  
  
 Visual C\+\+ 建置系統無法登錄組建 \(dll 或 .exe\) 的輸出，  您必須以系統管理員的身份登入，才能修改登錄。  
  
 如果您是在建置 .dll，可以試著手動使用 regsvr32.exe 來註冊 .dll，這應該會顯示有關建置為何失敗的資訊。  
  
 如果您建置的不是 .dll，請查看造成錯誤之命令的建置記錄檔。