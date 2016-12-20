---
title: "參考非共用成員需要物件參考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30469"
  - "vbc30469"
helpviewer_keywords: 
  - "BC30469"
ms.assetid: af503e8b-2e1f-4f91-a07f-b1ddd73dd4a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 參考非共用成員需要物件參考
您的程式碼內已參考了非共用成員，而且無法提供物件參考。 您無法使用類別名稱本身來限定非共用的成員。 執行個體必須先宣告為物件變數，再依變數名稱參考。  
  
 **錯誤 ID：**BC30469  
  
### 更正這個錯誤  
  
1.  宣告執行個體為物件變數。  
  
2.  依變數名稱參考執行個體。  
  
## 請參閱  
 [不在組建中：了解類別](http://msdn.microsoft.com/zh-tw/cc2355a2-cb98-4353-9440-736585aec46c)   
 [不在組建中：Visual Basic 中的共用成員](http://msdn.microsoft.com/zh-tw/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)   
 [NOTINBUILD：當多個變數擁有相同名稱時解析參考](http://msdn.microsoft.com/zh-tw/9601e39f-1911-44e1-ace5-3f6e090408b9)