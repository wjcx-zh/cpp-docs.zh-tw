---
title: "MSBuild 錯誤 MSB1027 | Microsoft Docs"
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
  - "MSBuild.CannotAutoDisableAutoResponseFile"
helpviewer_keywords: 
  - "MSB1027"
ms.assetid: 2ef8d643-616c-4608-be76-5c2c8e18a9e7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1027
**無法在 MSBuild.rsp 自動回應檔中指定 \/noautoresponse 參數，也無法在該自動回應檔所參考的任何回應檔中指定此參數。**  
  
 **\/noautoresponse** 參數是位於 MSBuild.rsp 檔或 MSBuild.rsp 檔所包含的另一個回應檔中，  自動回應檔無法用來停用它自己。  
  
### 若要更正這個錯誤  
  
-   指定不同的回應檔。  
  
-   移除 MSBuild.rsp 回應檔中的 **\/noautoresponse** 參數。  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)