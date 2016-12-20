---
title: "MSBuild 錯誤 MSB3126 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNotInstalled"
helpviewer_keywords: 
  - "MSB3126"
ms.assetid: 0c92cbb6-9100-4433-8113-f2f3a1432243
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3126
**MSB3126: 此應用程式使用檔案關聯，但未標記為用於安裝。  檔案關聯不可使用於未安裝的應用程式，例如 Web 瀏覽器中裝載的應用程式。**  
  
 當應用程式設定為使用檔案關聯，但是應用程式的安裝模式卻設成僅供線上使用時，就會發生這個錯誤。  因為僅供線上使用的應用程式通常是在瀏覽器中執行，所以不能使用檔案關聯。  
  
### 若要更正這個錯誤  
  
-   將 \[**安裝模式和設定**\] 設定為 \[**應用程式也可以在離線時使用 \(從 \[開始\] 功能表啟動\)**\]。  如需詳細資訊，請參閱 [如何：指定 ClickOnce 離線或線上安裝模式](../Topic/How%20to:%20Specify%20the%20ClickOnce%20Offline%20or%20Online%20Install%20Mode.md)。  
  
## 請參閱  
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)