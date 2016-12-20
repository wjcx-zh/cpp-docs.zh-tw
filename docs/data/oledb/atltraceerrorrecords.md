---
title: "AtlTraceErrorRecords | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.AtlTraceErrorRecords"
  - "ATL::AtlTraceErrorRecords"
  - "AtlTraceErrorRecords"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AtlTraceErrorRecords 函式"
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AtlTraceErrorRecords
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果傳回錯誤，傾印 OLE DB 錯誤記錄資訊傾印至裝置。  
  
## 語法  
  
```  
  
      inline void AtlTraceErrorRecords(   
   HRESULT hrErr = S_OK    
);  
```  
  
#### 參數  
 `hErr`  
 \[ `HRESULT` 由 OLE DB 消費者樣板成員函式所傳回。  
  
## 備註  
 如果 `hErr` 不是 `S_OK`， `AtlTraceErrorRecords` 會傾印 OLE DB 錯誤記錄資訊到傾印裝置 \(輸出視窗或檔案的 **Debug** 選項\)。  錯誤記錄資訊，從提供者取得，包括資料列編號、來源、說明、說明檔、內容和 GUID 每個錯誤記錄的目錄項目。  `AtlTraceErrorRecords` 只傾印這項資訊在偵錯組建。  在發行的組建，它是最佳化的空白 Stub。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)