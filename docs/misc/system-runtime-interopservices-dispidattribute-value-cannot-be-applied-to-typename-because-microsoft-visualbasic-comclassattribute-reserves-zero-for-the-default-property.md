---
title: "&#39;System.Runtime.InteropServices.DispIdAttribute&#39; 值無法套用至 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 保留給預設屬性的值為零 | Microsoft Docs"
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
  - "vbc32505"
  - "bc32505"
helpviewer_keywords: 
  - "BC32505"
ms.assetid: a7d5b948-2d72-48b1-8baf-bfaae36b0128
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DispIdAttribute&#39; 值無法套用至 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 保留給預設屬性的值為零
<xref:System.Runtime.InteropServices.DispIdAttribute> 屬性區塊指定 DISPID 值 0，這是保留供 `COMClassAttribute` 用來代表套用它之類別的預設屬性。  
  
 分派識別項 \(DISPID\) 是作為 `IDispatch:Invoke` 方法的引數用於 COM 中，以存取 COM 物件所公開的屬性和方法。  
  
 **錯誤 ID︰**BC32505  
  
### 更正這個錯誤  
  
-   在 <xref:System.Runtime.InteropServices.DispIdAttribute> 中指定大於零的 DISPID 值。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute 類別](http://msdn.microsoft.com/zh-tw/5c2f0835-9210-47dc-bc59-5c1769953574)