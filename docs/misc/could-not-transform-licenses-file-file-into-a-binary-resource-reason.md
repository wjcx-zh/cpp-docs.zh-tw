---
title: "Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.licx_generator_failed"
ms.assetid: 875e948c-d7a3-4ffc-be0d-f341de5f6310
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt;
一些原因導致授權處理器失敗，而無法將 .licx 檔案轉換成二進位資源。  
  
 這個錯誤一般是因為錯誤的 .licx 檔案所產生。  例如，檔案可能曾在文字編輯器中開啟和修改過。  
  
 如果發生這種錯誤，建置處理序將無法完成。  
  
### 若要更正這個錯誤  
  
1.  在 \[方案總管\] 中選取專案。  
  
2.  從 \[**專案**\] 功能表，按一下 \[**顯示所有檔案**\]。  
  
3.  在 \[方案總管\] 中，展開 \[obj\] 資料夾，接著再展開 \[**偵錯**\] 資料夾。  
  
4.  找出名為 "myApplication.exe.licenses" 的檔案，其中 myApplication 是 Windows Form 應用程式的名稱。  
  
5.  刪除這個檔案並且重建方案。  
  
## 請參閱  
 [如何：授權元件和控制項](../Topic/How%20to:%20License%20Components%20and%20Controls.md)