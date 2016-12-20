---
title: "增強簡單唯讀提供者 | Microsoft Docs"
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
  - "IRowsetLocate 類別"
  - "IRowsetLocate 類別, 加入至 OLE DB 樣板提供者"
  - "唯讀提供者 [C++]"
  - "簡單唯讀提供者 [C++]"
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 增強簡單唯讀提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本章節示範如何增強在前一章節所建立的[簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)。  `IRowsetLocateImpl` 會建立 `IRowsetLocate` 介面的實作，並為您加入書籤支援。  
  
 當您擁有可運作的提供者之後，可能會想增強它，以便進行更新提供者、處理交易，或增強資料列擷取演算法的效能。  大多數的提供者增強都牽涉到將介面加入至現有的 COM 物件內。  
  
 下列主題的範例透過將 `IRowsetLocate` 介面加入至 `CAgentRowset` 來增強資料列擷取機制。  本主題說明其作法：  
  
-   [讓 RMyProviderRowset 繼承自 IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md)。  
  
-   [動態決定傳回給消費者的資料行](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## 請參閱  
 [建立簡單唯讀提供者](../../data/oledb/creating-a-simple-read-only-provider.md)