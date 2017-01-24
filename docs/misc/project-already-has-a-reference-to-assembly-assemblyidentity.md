---
title: "專案已經有組件 &lt;組件識別&gt; 的參考 | Microsoft Docs"
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
  - "bc32208"
  - "vbc32208"
helpviewer_keywords: 
  - "BC32208"
ms.assetid: a9f73a2c-5135-4315-bf2c-710ef216095d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 專案已經有組件 &lt;組件識別&gt; 的參考
專案已經有組件 \<組件識別\> 的參考。 無法對 '\<檔案路徑\>' 加入第二個參考。  
  
 專案多次參考相同的組件。  
  
 組件識別包含組件的名稱、版本、公開金鑰 \(如果有的話\) 和文化特性。  
  
 這個錯誤的其中一個可能原因是另一份組件的參考，而且是透過與原始參考之檔案路徑不同的檔案路徑。  
  
 **錯誤 ID︰**BC32208  
  
### 更正這個錯誤  
  
-   請移除第二個參考。 它是不需要的，因為它參考相同的組件。  
  
## 請參閱  
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)