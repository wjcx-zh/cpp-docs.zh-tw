---
title: "疑難排解例外狀況：System.NotSupportedException | Microsoft Docs"
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
  - "NotSupportedException 類別"
ms.assetid: a214e851-ee0f-4bbd-9f72-8769046526f3
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.NotSupportedException
不支援被叫用的方法，或嘗試讀取、尋找或寫入不支援叫用功能的資料流時，就會擲回 <xref:System.NotSupportedException> 例外狀況。  
  
## 相關秘訣  
 **請確認此方法是支援的。**  
 有些方法在基底類別不受支援，但在衍生類別中卻支援這些方法。 如果衍生類別只從某些方法的基底類別中實作這些方法的子集，則會針對不受支援的方法擲回 <xref:System.NotSupportedException> 例外狀況。  
  
## 備註  
 與 [!INCLUDE[Compact](../misc/includes/compact_md.md)] 搭配使用，並在原生函式中使用 P\/Invoke 時，可能會在下列情況中擲回這個例外狀況：  
  
-   Managed 程式碼中的宣告不正確。  
  
-   [!INCLUDE[Compact](../misc/includes/compact_md.md)] 不支援您嘗試進行的動作。  
  
-   DLL 名稱在輸出期間損壞。  
  
-   在這種情況中，請檢查：  
  
-   任何違反 [!INCLUDE[Compact](../misc/includes/compact_md.md)] P\/Invoke 限制的行為。  
  
-   需要預先配置記憶體的任何引數。 如果這些引數存在的話，您必須將參考傳遞至現有變數。  
  
-   輸出函式的所有名稱都是正確的。 可以使用 DumpBin.exe 進行確認。  
  
-   您並未嘗試傳遞過多的引數。  
  
## 請參閱  
 <xref:System.NotSupportedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)