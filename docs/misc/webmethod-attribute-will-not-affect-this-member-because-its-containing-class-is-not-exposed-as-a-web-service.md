---
title: "&#39;WebMethod&#39; 屬性不會影響這個成員，因為它的包含類別並未公開為 Web 服務 | Microsoft Docs"
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
  - "vbc30771"
  - "bc30771"
helpviewer_keywords: 
  - "BC30771"
ms.assetid: 20b09f6a-b61a-4d89-9ca5-4632b5e68e65
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;WebMethod&#39; 屬性不會影響這個成員，因為它的包含類別並未公開為 Web 服務
<xref:System.Web.Services.WebMethodAttribute> 屬性讓方法可從遠端 Web 用戶端呼叫，但僅限於方法的類別衍生自 <xref:System.Web.Services.WebService> 時。  
  
 **錯誤 ID︰**BC30771  
  
### 更正這個錯誤  
  
-   將類別變更為衍生自 <xref:System.Web.Services.WebService>。  
  
     — 或 —  
  
-   從方法中移除 <xref:System.Web.Services.WebMethodAttribute> 屬性。  
  
## 請參閱  
 [NIB：逐步解說：使用 Visual Basic 或 Visual C\# 建立 Web 服務](http://msdn.microsoft.com/zh-tw/295f4c3f-9540-4bd1-b1cc-3e9cb9675cc7)