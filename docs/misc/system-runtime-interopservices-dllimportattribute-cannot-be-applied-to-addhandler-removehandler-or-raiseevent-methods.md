---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至 &#39;AddHandler&#39;、&#39;RemoveHandler&#39; 或 &#39;RaiseEvent&#39; 方法 | Microsoft Docs"
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
  - "bc31531"
  - "vbc31531"
helpviewer_keywords: 
  - "BC31531"
ms.assetid: 0ea3a16c-cfe0-4cb5-b740-358679272f8d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; 無法套用至 &#39;AddHandler&#39;、&#39;RemoveHandler&#39; 或 &#39;RaiseEvent&#39; 方法
`DllImportAttribute` 屬性已套用至 `AddHandler`、`RemoveHandler` 或 `RaiseEvent` 方法宣告。 這個屬性只能與空白 `Function` 或 `Sub` 搭配使用。  
  
 **錯誤 ID︰**BC31531  
  
### 更正這個錯誤  
  
-   請從方法宣告中移除 `DllImportAttribute` 屬性。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-tw/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/zh-tw/7f765da0-5491-40b6-9ed5-24c98f9daad9)