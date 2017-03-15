---
title: "OLE DB 資源集中化和服務 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供者, 資源集中化"
  - "OLE DB 服務 [OLE DB]"
  - "OLE DB 服務 [OLE DB], 提供者需求"
  - "OLE DB, 資源集中化"
  - "資源集中化 [OLE DB], 提供者需求"
  - "服務提供者 [OLE DB]"
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 資源集中化和服務
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要妥善地使用 OLE DB 共用或任何一種 OLE DB 服務，您的提供者必須支援所有物件的彙總 \(Aggregation\)。  這是任何 OLE DB 1.5 或更新提供者的需求。  這對於運用服務而言相當重要。  不支援彙總的提供者無法共用，並且沒有提供其他服務。  
  
 若要被共用，提供者必須支援無限制執行緒模型。  資源集區將根據 **DBPROP\_THREADMODEL** 屬性決定提供者的執行緒模型。  
  
 如果提供者具有的全域連接狀態可能會在資料來源處於初始化狀態時發生變更，它就應該支援新的 **DBPROP\_RESETDATASOURCE** 屬性。  在重複使用連接之前呼叫此屬性，並給予提供者機會在下次使用前先清除狀態。  如果提供者無法清除一些和連接相關的狀態，它可能傳回屬性的 **DBPROPSTATUS\_NOTSETTABLE**，將無法重複使用該連接。  
  
 連接至遠端資料庫並可偵測連接是否遺失的提供者，應該支援 **DBPROP\_CONNECTIONSTATUS** 屬性。  這個屬性提供 OLE DB 偵測無作用連接的能力，並確認它們並未傳回至集區的服務。  
  
 最後，自動交易登記一般都無法運作，除非它實作的層級和共用發生的層級相同。  支援自動交易登記的提供者本身應可透過顯露 **DBPROP\_INIT\_OLEDBSERVICES** 屬性來支援停用此登記，並且當 **DBPROPVAL\_OS\_TXNENLISTMENT** 取消選取時停用登記。  
  
## 請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)