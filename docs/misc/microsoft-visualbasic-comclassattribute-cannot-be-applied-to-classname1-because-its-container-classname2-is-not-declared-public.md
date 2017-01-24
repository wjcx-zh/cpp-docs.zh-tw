---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; 無法套用至 &#39;&lt;類別名稱1&gt;&#39;，因為其容器 &#39;&lt;類別名稱2&gt;&#39; 未宣告為 &#39;Public&#39; | Microsoft Docs"
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
  - "vbc32504"
  - "bc32504"
helpviewer_keywords: 
  - "BC32504"
ms.assetid: 4138b639-88d6-4b51-afcd-c92a1be36f1c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 無法套用至 &#39;&lt;類別名稱1&gt;&#39;，因為其容器 &#39;&lt;類別名稱2&gt;&#39; 未宣告為 &#39;Public&#39;
使用 `COMClassAttribute` 屬性區塊的類別是宣告於不為 `Public` 的類別內部。 如果類別是要公開為 COM 物件，則必須以 `Public` 存取來宣告其整個內含項目階層。  
  
 **錯誤 ID︰**BC32504  
  
### 更正這個錯誤  
  
-   宣告所有內含項目類別 `Public`，或移除 `COMClassAttribute` 屬性區塊。  
  
## 請參閱  
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute 類別](http://msdn.microsoft.com/zh-tw/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [Public](../Topic/Public%20\(Visual%20Basic\).md)