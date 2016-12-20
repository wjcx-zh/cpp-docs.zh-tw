---
title: "疑難排解例外狀況：System.Drawing.Printing.InvalidPrinterException | Microsoft Docs"
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
  - "InvalidPrinterException 類別"
ms.assetid: e19b9b9c-2b0f-4839-85c0-ae75e1c356d2
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Drawing.Printing.InvalidPrinterException
嘗試使用無效的印表機設定存取印表機時，就會擲回 <xref:System.Drawing.Printing.InvalidPrinterException> 例外狀況。  
  
## 相關秘訣  
 **請確定印表機存在。**  
 造成無效印表機設定的原因，大多是因為參考了不存在的印表機。 如需詳細資訊，請參閱<xref:System.Drawing.Printing>。  
  
 **請確定已安裝預設的印表機。**  
 如果尚未指定印表機，請確定已安裝預設印表機。 如需詳細資訊，請參閱<xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>。  
  
## 請參閱  
 <xref:System.Drawing.Printing.InvalidPrinterException>   
 <xref:System.Drawing.Printing.PrinterSettings>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)