---
title: "轉換提供者不支援的資料 | Microsoft Docs"
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
  - "OLE DB 提供者樣板, 不支援的資料類型"
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 轉換提供者不支援的資料
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當消費者要求提供者不支援的資料型別時，`IRowsetImpl::GetData` 的 OLE DB 提供者樣板程式碼會呼叫 Msdadc.dll 來轉換資料型別。  
  
 實作像 `IRowsetChange` 這類需要資料轉換的介面時，您可呼叫 Msdaenum.dll 來進行轉換。  使用定義於 Atldb.h 內的 `GetData` 做為範例。  
  
## 請參閱  
 [使用 OLE DB 提供者樣板](../../data/oledb/working-with-ole-db-provider-templates.md)