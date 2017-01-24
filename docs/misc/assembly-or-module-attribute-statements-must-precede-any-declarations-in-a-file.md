---
title: "組件或模組屬性陳述式必須在檔案中的任何宣告之前 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30637"
  - "bc30637"
helpviewer_keywords: 
  - "BC30637"
ms.assetid: 80242581-fa8a-4903-9395-6f7ad1610231
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 組件或模組屬性陳述式必須在檔案中的任何宣告之前
全域屬性必須宣告在原始程式檔頂端，`Option` 和 `Imports` 陳述式之後，但任何其他陳述式之前。  
  
 **錯誤 ID：**BC30637  
  
### 更正這個錯誤  
  
1.  請將全域屬性，例如 `<Module:>` 和 `<Assembly:>` 放在原始程式檔的頂端。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [不在組建中：Visual Basic 中的全域屬性](http://msdn.microsoft.com/zh-tw/253a32d8-1531-4504-b687-088554ab71d2)