---
title: "引數 BasePath 必須是資料夾路徑 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b180ce60-ad57-41a6-a313-491d86d84cc7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引數 BasePath 必須是資料夾路徑
引數 `BasePath` 必須是由資料夾路徑所組成。 您可能不正確地剖析字串，並提供無法辨識為有效路徑的值。  
  
### 更正這個錯誤  
  
-   檢查您提供給 `BasePath` 的值，確定它是有效的資料夾路徑。  
  
## 請參閱  
 <xref:System.CodeDom.Compiler.TempFileCollection.BasePath%2A>   
 <xref:System.Resources.ResXResourceWriter.BasePath%2A>   
 <xref:System.Resources.ResXResourceReader.BasePath%2A>   
 [如何：剖析檔案路徑](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)