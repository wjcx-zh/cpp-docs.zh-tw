---
title: "MSBuild 錯誤 MSB3071 | Microsoft Docs"
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
  - "MSBuild.Exec.AllDriveLettersMappedError"
helpviewer_keywords: 
  - "MSB3071"
ms.assetid: 8afbc6ec-e399-4f06-a30b-f33c87642ef7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3071
**從 A: 到 Z: 的所有磁碟機代號目前都在使用中。  因為工作目錄 "'\<path\>'" 是 UNC 路徑，所以 "Exec" 工作需要有可用的磁碟機代號以便對應 UNC 路徑。  請先中斷連接一或多個共用資源以釋放磁碟機代號，或指定本機工作目錄，再嘗試重新執行這個命令。**  
  
 從 A: 到 Z: 的所有磁碟機代號目前都在使用中。  由於指定的工作目錄是 UNC 路徑，因此 `Exec` 工作需要有可用的磁碟機代號以便對應 UNC 路徑。  
  
### 若要更正這個錯誤  
  
-   中斷一或多個共用資源的連接，以釋放磁碟機代號。  
  
-   再度嘗試這個命令之前，先指定本機工作目錄。  
  
## 請參閱  
 [Exec Task](../Topic/Exec%20Task.md)