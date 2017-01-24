---
title: "The referenced component &#39;component&#39; could not be found. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.referencenotfound"
ms.assetid: 35491b4d-e3e4-4e7c-8ac1-3adb09c1ef58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The referenced component &#39;component&#39; could not be found. &lt;reason&gt;
專案系統無法解析特定參考。  在這個工作清單項目上按兩下會將焦點 \(Focus\) 設定到 \[方案總管\]，並會選取無法解析的參考。  
  
 編輯 [ReferencePaths](http://msdn.microsoft.com/zh-tw/8e549b39-7256-456a-8fd7-089b23facf9c) 屬性，以致適當的目錄包含在路徑中。  
  
 如果您將專案移動到另一台電腦，就可能會發生這個錯誤。  `ReferencePath` 屬性會以絕對路徑形式儲存。  如果參考 R1 是位於電腦 A 的 c:\\R\\R1.dll 中，則 .vbproj.user 或 .csproj.user 檔案會將 c:\\R 儲存為 `ReferencePath` 屬性的一部分。  但是，如果在電腦 B 上，R1 位於 d:\\R\\R1.dll 之中，則專案系統將無法找到 R1，因為 d:\\R 不在參考路徑上。  
  
 類似的案例為原始程式碼控制案例。  如果您在專案中登記了.vbproj.user \(或 .csproj.user\) 檔案，而該檔案因為未儲存於原始檔控制中，所以並未複製到您電腦中。  因此，`ReferencePath` 屬性的初始值將是空白，依靠 `ReferencePath` 而用於解析的任何參考都將無法解析。  如需詳細資訊，請參閱《Team Development with Visual Studio .NET and Visual SourceSafe》中的「管理相依性」。  
  
 如果參考的專案不位於目前方案中，也可能會導致這個錯誤。  
  
 發生這個錯誤時，專案可能不會建置。  
  
 如需解析組件參考的詳細資訊，請參閱[中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)。  
  
## 請參閱  
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)