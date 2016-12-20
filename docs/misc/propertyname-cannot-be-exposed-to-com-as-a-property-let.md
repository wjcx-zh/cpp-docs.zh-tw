---
title: "&#39;&lt;屬性名稱&gt;&#39; 無法以屬性 &#39;Let&#39; 公開 (Expose) 給 COM | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42102"
  - "vbc42102"
helpviewer_keywords: 
  - "BC42102"
ms.assetid: b77c5b7c-ac43-4b2d-b8bc-582e65e6f7e7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;屬性名稱&gt;&#39; 無法以屬性 &#39;Let&#39; 公開 (Expose) 給 COM
'\<屬性名稱\>' 無法以屬性 'Let' 公開 \(Expose\) 給 COM。 您無法從 Visual Basic 6.0 使用 'Let' 陳述式將非物件值 \(例如數值或字串\) 指定給這個屬性。  
  
 使用 `COMClassAttribute` 屬性區塊的類別宣告資料類型為 `Object` 的 `Public` 屬性。 Visual Basic 6.0 程式可以將這個屬性當做 `Variant` 來存取，但只能使用 `Set` 陳述式為其指派物件參考， 而不能使用 `Let` 陳述式指派實值類型。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42102  
  
### 解決這個警告  
  
-   考慮通知這個類別的潛在 Visual Basic 6.0 使用者，他們無法搭配 `Let` 陳述式使用這個屬性。  
  
## 請參閱  
 [Default Property Changes in Visual Basic](http://msdn.microsoft.com/zh-tw/9b8cfad7-40ac-4b83-affb-1ff781755a4c)   
 [Property Statement](../Topic/Property%20Statement.md)   
 [Public](../Topic/Public%20\(Visual%20Basic\).md)   
 [Object Data Type](../Topic/Object%20Data%20Type.md)   
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute 類別](http://msdn.microsoft.com/zh-tw/5c2f0835-9210-47dc-bc59-5c1769953574)