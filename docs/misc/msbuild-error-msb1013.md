---
title: "MSBuild 錯誤 MSB1013 | Microsoft Docs"
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
  - "MSBuild.RepeatedResponseFileError"
helpviewer_keywords: 
  - "MSB1013"
ms.assetid: 3e85c710-99e6-4141-b058-63a144a06454
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1013
**回應檔 \(Response File\) 指定了兩次。  一個回應檔只能指定一次。**  
  
 命令列包含了多個回應檔的參考。  例如 `msbuild @response.rsp @response.rsp`。  
  
 如果指定的回應檔包含了另一個回應檔的參考，而該回應檔又包含了原始回應檔的參考，也可能會發生這個錯誤訊息。  相同的回應檔在每次編譯 \(Compilation\) 中只能指定一次。  
  
### 若要更正這個錯誤  
  
-   移除重複的回應檔參考。  例如，不要使用 `msbuild @response.rsp @response.rsp`，而改用 `msbuild @response.rsp`。  
  
-   從這個回應檔所參考的另一個回應檔中，移除對原始回應檔的參考。  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)