---
title: "No files were found to look in. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_FRLookInEmpty"
  - "vs.message.0x800A00DE"
ms.assetid: d560aef3-7a55-4fbb-a541-1a43fc13c18b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No files were found to look in.
這個錯誤通常在 \[查詢\] 清單中所指定的檔案名稱或目錄不存在或找不到時發生。  如果您所指定的有效目錄沒有包括 \[檔案類型\] 清單中所指定的副檔名，或所指定的目錄沒有任何檔案時，這個錯誤也會出現。  在含有 `Hidden` 或 `System` 屬性集的目錄中搜尋時，也會出現這個錯誤。  
  
### 若要更正這個錯誤  
  
1.  請使用 \[**自訂目錄集**\] 對話方塊來瀏覽欲搜尋的目錄或檔案名稱，而不是自行輸入路徑或檔案名稱。  您可以藉由選擇 \[**查詢**\] 清單旁的省略按鈕來存取 \[**自訂目錄集**\] 對話方塊。  
  
2.  將 \[**檔案類型**\] 清單中指定的副檔名變更為 \*.\*，即可在指定的目錄中搜尋所有檔案。  
  
### 若要略過這個錯誤  
  
1.  按住 CTRL 鍵並按下 ScrLk。  
  
     這麼做會取消對話方塊。  
  
## 請參閱  
 [尋找和取代文字](../Topic/Finding%20and%20Replacing%20Text.md)   
 [檔案中尋找](../Topic/Find%20in%20Files.md)   
 [Choose Search Folders](http://msdn.microsoft.com/zh-tw/85af6458-dcde-4a84-9ea4-f5cc6550dc80)