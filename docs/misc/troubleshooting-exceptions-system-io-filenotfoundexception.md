---
title: "疑難排解例外狀況：System.IO.FileNotFoundException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "FileNotFoundException 類別"
  - "System.IO.FileNotFoundException 例外狀況"
ms.assetid: 6e5ab395-7c81-434e-835f-0fc792b9149d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IO.FileNotFoundException
嘗試存取磁碟上不存在的檔案或目錄時，就會擲回 <xref:System.IO.FileNotFoundException> 例外狀況。  
  
## 相關秘訣  
 **請確認檔案確實是在指定的位置。**  
 如果該檔案不存在，就會擲回這個例外狀況。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>。  
  
 **使用相對路徑時，請確定目前的目錄正確。**  
 如果您假設目前的目錄是不正確的，則相對路徑也不正確。  
  
## 請參閱  
 <xref:System.IO.FileNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)