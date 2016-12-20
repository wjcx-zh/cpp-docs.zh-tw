---
title: "疑難排解例外狀況：System.IdentityModel.Selectors.ServiceNotStartedException | Microsoft Docs"
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
  - "System.IdentityModel.Selectors.ServiceNotStartedException 例外狀況"
  - "ServiceNotStartedException 例外狀況"
ms.assetid: 6d34bab2-994a-4b0c-893d-19b5d7acf92d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IdentityModel.Selectors.ServiceNotStartedException
當 CardSpace 未在使用者電腦上啟動時，就會擲回 <xref:System.IdentityModel.Selectors.ServiceNotStartedException> 例外狀況。 如果 CardSpace 嘗試啟動，但卻因為任何原因而無法啟動，便會擲回此例外狀況。  
  
 請檢查電腦中是否已安裝並啟用 CardSpace 服務。 嘗試以手動方式使用 Microsoft Management Console \(MMC\) 來啟動 CardSpace 服務。  
  
 CardSpace 第 1 版不支援 FAT 檔案系統。 在 FAT 系統上，CardSpace 將不會啟動，並且會發生此例外狀況。  
  
## 請參閱  
 <xref:System.IdentityModel.Selectors.ServiceNotStartedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)