---
title: "位於 &#39;&lt;類型名稱&gt;&#39; 的 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 的 &#39;InterfaceId&#39; 和 &#39;EventsId&#39; 參數不可以有相同的值。 | Microsoft Docs"
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
  - "bc32507"
  - "vbc32507"
helpviewer_keywords: 
  - "BC32507"
ms.assetid: 762e2990-e578-492d-b8ee-11658b6069fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 位於 &#39;&lt;類型名稱&gt;&#39; 的 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 的 &#39;InterfaceId&#39; 和 &#39;EventsId&#39; 參數不可以有相同的值。
`COMClassAttribute` 屬性區塊為介面指定了和建立事件相同的全域唯一識別碼 \(GUID\)。 如果兩者都獲提供這些識別項，它們必須不同。 它們也必須和類別識別項不同。  
  
 GUID 由 16 個位元組組成，前八位是數字，後八位是二進位。 它由 Microsoft 公用程式 \(例如 uuidgen.exe\) 產生，保證是唯一的。  
  
 **錯誤識別碼：** BC32507  
  
### 更正這個錯誤  
  
1.  判斷正確的 GUID 對識別 COM 物件的介面和建立事件非常必要。  
  
2.  請確定正確複製要呈現給 `COMClassAttribute` 屬性區塊的 GUID 字串。  
  
## 請參閱  
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute 類別](http://msdn.microsoft.com/zh-tw/5c2f0835-9210-47dc-bc59-5c1769953574)