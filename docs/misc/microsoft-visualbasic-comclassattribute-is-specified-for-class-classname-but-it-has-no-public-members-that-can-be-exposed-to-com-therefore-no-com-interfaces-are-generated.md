---
title: "將 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 指定給類別 &#39;&lt;類別名稱&gt;&#39;，但它沒有可公開 (Expose) 至 COM 的公用成員；因此，沒有產生 COM 的介面 | Microsoft Docs"
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
  - "bc40011"
  - "vbc40011"
helpviewer_keywords: 
  - "BC40011"
ms.assetid: 39aed273-bf27-4667-8116-022c4dd8f3c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 將 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 指定給類別 &#39;&lt;類別名稱&gt;&#39;，但它沒有可公開 (Expose) 至 COM 的公用成員；因此，沒有產生 COM 的介面
使用 `COMClassAttribute` 屬性區塊的類別未定義任何 `Public` 屬性或方法。 如果類別是要公開為 COM 物件，則必須以 `Public` 存取來宣告其屬性和方法。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40011  
  
### 更正這個錯誤  
  
-   將 `Public` 關鍵字加入類別中的一個或多個屬性或方法，或移除 `COMClassAttribute` 屬性區塊。  
  
## 請參閱  
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Public](../Topic/Public%20\(Visual%20Basic\).md)   
 [ComClassAttribute 類別](http://msdn.microsoft.com/zh-tw/5c2f0835-9210-47dc-bc59-5c1769953574)