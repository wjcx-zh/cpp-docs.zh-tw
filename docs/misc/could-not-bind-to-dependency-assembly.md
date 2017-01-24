---
title: "Could not bind to dependency &#39;assembly&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cantbinddependency"
ms.assetid: 0f76190d-d57e-4e0e-bec4-532aec978d08
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not bind to dependency &#39;assembly&#39;
您的專案參考之一本身包含找得到但不是有效組件的組件參考 \(相依性\)。  這個錯誤不會阻止專案建置。  但是，Run\-Time 錯誤可能會。  
  
 這種情況暗示以下三種狀況均為真：  
  
-   您磁碟上有一個以上具有相同名稱的檔案。  
  
-   檔案其中之一不是組件，但另一個是組件。  
  
-   您的參考路徑首先搜尋的目錄包含不是組件的檔案。  
  
 **若要更正這個錯誤**  
  
-   修改您專案搜尋目錄的順序，以尋找參考。  如需詳細資訊，請參閱[NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/8e549b39-7256-456a-8fd7-089b23facf9c)。  
  
## 請參閱  
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)   
 [如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-tw/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)