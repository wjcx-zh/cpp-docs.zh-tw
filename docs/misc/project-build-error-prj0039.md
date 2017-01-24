---
title: "專案建置錯誤 PRJ0039 | Microsoft Docs"
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
  - "PRJ0039"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0039"
ms.assetid: 207bbc28-922f-44d6-8bdd-3016c850f5b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 專案建置錯誤 PRJ0039
無法建立暫存檔。 必須能夠建立暫存檔案，NMake 工具才可以執行。  
  
 在建置 Makefile 專案時 \(請參閱[建立 Makefile 專案](../ide/creating-a-makefile-project.md)\)，Visual C\+\+ 專案系統必須建立一些暫存檔案。 這個錯誤指出專案系統無法建立一或多個此種檔案。  
  
 TMP 環境變數包含暫存目錄的名稱。  
  
 下面列出發生這個錯誤的可能原因，以及建議的解決方式：  
  
 使用者對暫存目錄沒有寫入權限  
 請確定您對暫存目錄具有寫入權限。  
  
 暫存目錄中有太多的暫存檔案  
 其他處理序可能已建立暫存檔案，但並未刪除它們。 請刪除部分或全部的暫存檔案。  
  
 沒有可用磁碟空間  
 請刪除磁碟上的一些檔案，或是將暫存目錄變更到具有可用空間的磁碟上。  
  
 TMP 環境變數不正確  
 TMP 環境變數可能指向不存在的目錄。