---
title: "無法自動傳送錯誤報告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc2027"
  - "vbc2027"
helpviewer_keywords: 
  - "BC2027"
ms.assetid: 84ba8580-2234-46d1-b4a5-94b03f64c0c7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法自動傳送錯誤報告
無法自動傳送錯誤報告。 請瀏覽 'http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039' 以設定傳送錯誤報告設定。  
  
 您已指定 `/errorreport:send` 編譯器選項，但電腦未設定為自動傳送錯誤報告。 不會傳送 Visual Basic 編譯器內部錯誤的相關資訊。  
  
 **錯誤 ID︰**BC2027  
  
### 更正這個錯誤  
  
-   移除 `/errorreport:send` 編譯器選項，或者取代為 `/errorreport:queue`、`/errorreport:prompt` 或 `/errorreport:none`。  
  
     — 或 —  
  
-   遵循 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039) 的指示啟用自動錯誤報告。  
  
## 請參閱  
 [\/errorreport](../Topic/-errorreport.md)   
 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039)