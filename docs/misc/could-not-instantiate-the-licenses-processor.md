---
title: "Could not instantiate the licenses processor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.no_licx_generator"
ms.assetid: 9e95d590-f41f-4cfa-bc73-fadeacfdb879
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not instantiate the licenses processor
無法產生將 .licx 檔案轉換成二進位資源的工具。  
  
 專案系統會將文字檔 .licx 轉換為可支援 .NET 控制項授權的二進位資源，當做編譯的一部分。  接著此二進位資源將嵌入專案輸出。  
  
 如果發生這種錯誤，建置處理序將無法完成。  
  
 每當將授權控制項加入至表單時，Windows Form 設計工具便會自動產生或更新 .licx 檔案。  每個專案都有一個 .licx 檔案，該檔案通常位於其根資料夾，且一定被命名為 Licenses.licx。  
  
 **若要更正這個錯誤**  
  
-   請重新安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  
  
## 請參閱  
 [如何：授權元件和控制項](../Topic/How%20to:%20License%20Components%20and%20Controls.md)