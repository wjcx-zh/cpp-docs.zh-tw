---
title: "類別 &#39;&lt;類別名稱&gt;&#39; 上的 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 隱含地宣告與 &lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 中同名成員衝突的 &lt;類別&gt; &#39;&lt;成員名稱&gt;&#39;。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BC42101"
ms.assetid: 001c8eaa-19b6-44fa-8056-4186ecffbda8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類別 &#39;&lt;類別名稱&gt;&#39; 上的 &#39;Microsoft.VisualBasic.ComClassAttribute&#39; 隱含地宣告與 &lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 中同名成員衝突的 &lt;類別&gt; &#39;&lt;成員名稱&gt;&#39;。
類別 '\<類別名稱\>' 上的 'Microsoft.VisualBasic.ComClassAttribute' 隱含地宣告與 \<類別\> '\<類型名稱\>' 中同名成員衝突的 \<類別\> '\<成員名稱\>'。 如果您想要隱藏基底 '\<類型名稱\>' 上的名稱，請使用 'Microsoft.VisualBasic.ComClassAttribute\(InterfaceShadows:\=True\)'。  
  
 使用 `COMClassAttribute` 屬性區塊的類別會隱含地定義與基底類別成員同名的介面。 在此情況下，介面名稱應該會遮蔽基底類別成員。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42101  
  
### 更正這個錯誤  
  
1.  如果您要隱藏基底類別成員，請在 `ComClassAttribute` 屬性區塊中設定 `InterfaceShadows:=True`。  
  
2.  如果您不要隱藏基底類別成員，請變更類別名稱。  
  
## 請參閱  
 [不在組建中：Visual Basic 中使用的屬性](http://msdn.microsoft.com/zh-tw/22231318-8a40-49af-9245-e0aab723563b)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute 類別](http://msdn.microsoft.com/zh-tw/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [ComClassAttribute.InterfaceShadows 屬性](http://msdn.microsoft.com/zh-tw/0fae25bd-e0ba-4755-a76c-3b526b1ac795)