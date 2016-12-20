---
title: "編譯器錯誤 CS0040 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0040"
ms.assetid: 6a600166-0335-4b6d-b050-6821b4624c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0040
建立偵錯資訊檔 'reason' 時發生未預期的錯誤  
  
 使用 [\/debug](../Topic/-debug%20\(C%23%20Compiler%20Options\).md) 編譯器選項時會發生此錯誤，並指出編譯器無法寫入 .pdb 檔案。 此錯誤的可能解決方式包括：重新安裝 Visual Studio、確保編譯器具有檔案或目錄的寫入權限  ，或不使用 \/debug 進行編譯。