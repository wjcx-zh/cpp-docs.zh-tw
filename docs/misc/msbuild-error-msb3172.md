---
title: "MSBuild 錯誤 MSB3172 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ReadInputManifestFailed"
helpviewer_keywords: 
  - "MSB3172"
ms.assetid: aa7291db-1f36-41e7-a510-90cd4daaa89d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3172
**MSB3172: 無法讀取資訊清單 '\<file\>'。 '  \<error\>'**  
  
 如果建置處理序在讀取資訊清單檔時遇到了一般性的問題，就會產生這個錯誤訊息。  這個錯誤訊息包含了檔案名稱，並在後面附上問題的詳細資訊。  
  
 您可能新增了組件或資訊清單檔做為內容檔。  此時您應該使用 \[**加入參考**\] 命令取代 \[**加入檔案**\]，使專案系統可以正確地參考相依組件。  較複雜的專案通常會將 bin 資料夾內的 .exe.manifest 標記為專案檔，但您應避免這麼做。  隱藏的 app.manifest 檔會變為 .exe.manifest 檔，並且可以在進階案例下進行手動編輯。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)