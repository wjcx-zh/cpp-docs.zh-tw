---
title: "Error copying the application configuration file to the run directory. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cant_copy_appcfg_file"
ms.assetid: 15699a76-16ef-40a8-8ed4-5eef4d2c0e72
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error copying the application configuration file to the run directory. &lt;reason&gt;
專案系統無法將 app.config 檔案複製至專案執行使用的目錄。  如果發生這種錯誤，建置處理序將無法完成。  
  
 只有在建置 .exe 檔時才會發生這種錯誤。  
  
 建置系統試圖在專案根資料夾內尋找名為 app.config 的檔案。  然後，該檔案會被複製到專案輸出目錄中，在輸出目錄內的名稱為 *outputfile.*config。  
  
 這個錯誤的原因包括：  
  
-   磁碟空間不足  
  
-   超過 MAX\_PATH  
  
 您可能也需要確定沒有另一個應用程式的複本在執行。  
  
## 請參閱  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)