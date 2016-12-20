---
title: "專案 &#39;&lt;專案名稱&gt;&#39; 需要組件 &#39;&lt;組件名稱&gt;&#39; 版本 &#39;&lt;版本號碼1&gt;&#39; 的參考，但是參考的卻是組件 &#39;&lt;組件名稱&gt;&#39; 的版本 &#39;&lt;版本號碼2&gt;&#39; (Visual Basic 警告) | Microsoft Docs"
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
  - "vbc42203"
  - "bc42203"
helpviewer_keywords: 
  - "BC42203"
ms.assetid: 26a3fa34-ec5d-4817-a947-3959446a924a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 專案 &#39;&lt;專案名稱&gt;&#39; 需要組件 &#39;&lt;組件名稱&gt;&#39; 版本 &#39;&lt;版本號碼1&gt;&#39; 的參考，但是參考的卻是組件 &#39;&lt;組件名稱&gt;&#39; 的版本 &#39;&lt;版本號碼2&gt;&#39; (Visual Basic 警告)
專案 '\<專案名稱\>' 需要組件 '\<組件名稱\>' 版本 '\<版本號碼1\>' 的參考，但是參考的卻是組件 '\<組件名稱\>' 的版本 '\<版本號碼2\>'。 已發出版本 '\<版本號碼1\>' 的參考。  
  
 專案除了間接參考其他地方所定義的組件之外，還直接參考該組件的較舊版本。  
  
 若要存取新版中所定義但舊版中未定義的類型和程式設計項目，編譯器會在解析存取時使用新版的間接參考。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42203  
  
### 更正這個錯誤  
  
-   移除舊版組件的直接參考，或變更它，使其參考新版。  
  
## 請參閱  
 [Common Language Runtime 中的組件](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)   
 [NIB：參考命名空間和元件](http://msdn.microsoft.com/zh-tw/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB：管理參考](http://msdn.microsoft.com/zh-tw/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)