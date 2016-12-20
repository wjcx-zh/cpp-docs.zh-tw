---
title: "&#39;System.Runtime.InteropServices.DispIdAttribute&#39; 值無法套用至 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 保留的值小於零。 | Microsoft Docs"
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
  - "bc32506"
  - "vbc32506"
helpviewer_keywords: 
  - "BC32506"
ms.assetid: c6f52e1d-45d8-45cb-9ecb-a2f23b3ca779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DispIdAttribute&#39; 值無法套用至 &#39;&lt;類型名稱&gt;&#39;，因為 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 保留的值小於零。
<xref:System.Runtime.InteropServices.DispIdAttribute> 屬性區塊指定小於 0 的 DISPID 值，這是保留供 `COMClassAttribute` 用於套用它的類別上的特殊函式。  
  
 分派識別項 \(DISPID\) 是作為 `IDispatch:Invoke` 方法的引數用於 COM 中，以存取 COM 物件所公開的屬性和方法。  
  
 **錯誤 ID︰**BC32506  
  
### 更正這個錯誤  
  
-   在 `DispIdAttribute` 中指定大於零的 DISPID 值。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute 類別](http://msdn.microsoft.com/zh-tw/5c2f0835-9210-47dc-bc59-5c1769953574)