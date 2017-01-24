---
title: "MSBuild 錯誤 MSB3127 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationDefaultIconNotInstalled"
helpviewer_keywords: 
  - "MSB3127"
ms.assetid: 161eea9a-332f-463e-a49e-d4030e937d52
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3127
**MSB3127: 預設圖示 \<iconname\> 在目前的檔案參考中找不到，或者未包含在所需的下載群組中。  預設圖示檔案名稱要區分大小寫，所以應用程式資訊清單中參考的檔案名稱必須與圖示的檔案名稱完全相符。**  
  
 當您發行設定為使用檔案關聯的應用程式時，資訊清單中參考的預設圖示必須位於目前的檔案參考中，或者必須是所需下載群組的一部分。  預設圖示就是具有已設定之檔案關聯 \(已設定之副檔名\) 的檔案所顯示的圖示。  
  
### 若要更正這個錯誤  
  
-   將圖示檔加入至目前的專案，並將它包含在所需的下載群組中。  如需詳細資訊，請參閱 [如何：指定哪些檔案是由 ClickOnce 發行](../Topic/How%20to:%20Specify%20Which%20Files%20Are%20Published%20by%20ClickOnce.md)。  
  
## 請參閱  
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)