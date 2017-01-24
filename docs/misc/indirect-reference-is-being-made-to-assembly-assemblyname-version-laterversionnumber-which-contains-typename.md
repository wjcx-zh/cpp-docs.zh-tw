---
title: "間接參考了含有 &#39;&lt;類型名稱&gt;&#39; 的組件 &lt;組件名稱&gt; 版本 &lt;較新版本號碼&gt; | Microsoft Docs"
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
  - "vbc32207"
  - "bc32207"
helpviewer_keywords: 
  - "BC32207"
ms.assetid: a3de74b5-bedd-4e36-b379-485e4b3903f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 間接參考了含有 &#39;&lt;類型名稱&gt;&#39; 的組件 &lt;組件名稱&gt; 版本 &lt;較新版本號碼&gt;
間接參考了含有 '\<類型名稱\>' 的組件 \<組件名稱\> 版本 \<較新版本號碼\>。 這個專案參考了 \<組件名稱\> 版本 \<早期版本號碼\> 的早期版本。 若要使用 '\<類型名稱\>'，您必須用版本 \<較新版本號碼\> \(含\) 以上版本取代 \<組件名稱\> 的參考。  
  
 運算式間接參考另一個專案，但這個專案參考相同組件的舊版本。  
  
 您通常應該僅使用組件的最新版本。  
  
 **錯誤 ID︰**BC32207  
  
### 更正這個錯誤  
  
1.  使用提到的類型名稱來判斷哪個專案也參考相同的組件。  
  
2.  判斷另一個專案所參考的組件版本，並將專案變更為參考相同的版本。  
  
## 請參閱  
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)