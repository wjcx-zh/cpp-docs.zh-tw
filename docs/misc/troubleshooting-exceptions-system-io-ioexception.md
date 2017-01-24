---
title: "疑難排解例外狀況：System.IO.IOException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IOException 類別"
ms.assetid: 87812daa-0784-43dc-b3dc-6652a960c362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IO.IOException
發生 I\/O 錯誤，例如無法讀取或寫入檔案時，就會擲回 <xref:System.IO.IOException>。  
  
## 相關秘訣  
 **請確定檔案和目錄都存在。**  
 確認嘗試讀取和寫入的目錄存在。 確認嘗試讀取的檔案存在。  
  
### 備註  
 使用資料流、檔案和目錄存取資訊時，<xref:System.IO.IOException> 是擲回之例外狀況的基底類別。  
  
 基本類別庫 \(Base Class Library\) 包含下列型別，每個型別都是 <xref:System.IO.IOException> 的衍生類別：  
  
-   <xref:System.IO.DirectoryNotFoundException>  
  
-   <xref:System.IO.EndOfStreamException>  
  
-   <xref:System.IO.FileNotFoundException>  
  
-   <xref:System.IO.FileLoadException>  
  
-   <xref:System.IO.PathTooLongException>  
  
## 請參閱  
 <xref:System.IO.IOException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [NOTINBUILD 如何：建立 CLR 主控台應用程式](http://msdn.microsoft.com/zh-tw/b8af4197-e65f-4b17-b18e-b9e92965d026)