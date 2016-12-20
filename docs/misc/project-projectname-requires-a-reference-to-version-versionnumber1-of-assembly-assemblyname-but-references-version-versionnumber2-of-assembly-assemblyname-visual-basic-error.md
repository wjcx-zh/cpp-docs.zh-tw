---
title: "專案 &#39;&lt;專案名稱&gt;&#39; 需要組件 &#39;&lt;組件名稱&gt;&#39; 版本 &#39;&lt;版本號碼1&gt;&#39; 的參考，但是參考的卻是組件 &#39;&lt;組件名稱&gt;&#39; 的版本 &#39;&lt;版本號碼2&gt;&#39; (Visual Basic 錯誤) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32209"
  - "bc32209"
helpviewer_keywords: 
  - "BC32209"
ms.assetid: fe50736b-444f-4e40-8f80-9760ff13a153
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 專案 &#39;&lt;專案名稱&gt;&#39; 需要組件 &#39;&lt;組件名稱&gt;&#39; 版本 &#39;&lt;版本號碼1&gt;&#39; 的參考，但是參考的卻是組件 &#39;&lt;組件名稱&gt;&#39; 的版本 &#39;&lt;版本號碼2&gt;&#39; (Visual Basic 錯誤)
專案除了間接參考其他地方所定義的組件之外，還直接參考該組件的較新版本。  
  
 如果編譯器允許您的程式碼使用間接參考，您可能無法存取新版中所定義但舊版中未定義的類型和程式設計項目。  
  
 **錯誤 ID︰**BC32209  
  
### 更正這個錯誤  
  
-   移除舊版組件的間接參考，並使用新版的直接參考。  
  
## 請參閱  
 [Common Language Runtime 中的組件](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB：參考命名空間和元件](http://msdn.microsoft.com/zh-tw/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB：管理參考](http://msdn.microsoft.com/zh-tw/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)