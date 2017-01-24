---
title: "Unable to read the resource information from the licx file | Microsoft Docs"
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
  - "vs.tasklisterror.fail_reading_licx_file"
ms.assetid: e59f0965-fa1c-4852-bd39-63430d5b7d9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to read the resource information from the licx file
專案系統無法讀取 .licx 檔案。  專案系統會將文字檔 .licx 轉換為適合與 COM\+ 授權模型共用的二進位資源檔，當做準備授權的一部分。  
  
 每當將授權控制項加入至表單時，Windows Form 設計工具便會自動產生或更新 .licx 檔案。  每個專案都有一個 .licx 檔案，該檔案通常位於其根資料夾，且一定被命名為 Licenses.licx。  
  
 一些導致這個錯誤的原因如下：  
  
-   使用權限遭拒。  
  
-   失去與 Web 專案的 Web 伺服器的通訊。  
  
 如果發生這種錯誤，建置處理序將無法完成。  
  
## 請參閱  
 [如何：授權元件和控制項](../Topic/How%20to:%20License%20Components%20and%20Controls.md)