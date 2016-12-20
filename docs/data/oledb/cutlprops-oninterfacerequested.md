---
title: "CUtlProps::OnInterfaceRequested | Microsoft Docs"
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
  - "CUtlProps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnInterfaceRequested 方法"
ms.assetid: a5e1a879-cff3-4e01-b902-2249a152984f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps::OnInterfaceRequested
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當消費者呼叫其中一個方法物件建立介面時，處理會要求選擇性介面。  
  
## 語法  
  
```  
  
      virtual HRESULT CUtlPropsBase::OnInterfaceRequested(  
   REFIID riid  
);  
```  
  
#### 參數  
 `riid`  
 \[in\] 所要求介面的 IID。  如需詳細資訊，請參閱 *OLE DB 程式設計人員參考* \( *MDAC SDK*\) 中 `ICommand::Execute` 的 `riid` 參數的說明。  
  
## 備註  
 **OnInterfaceRequested** 處理使用者要求的選擇性介面，當使用者呼叫其中一個方法物件建立介面時 \(例如 **IDBCreateSession**和 **IDBCreateCommand**、 `IOpenRowset`或 `ICommand`\)。  它會設定要求的介面對應的 OLE DB 屬性。  例如，如果消費者要求 **IID\_IRowsetLocate**， **OnInterfaceRequested** 設定 **DBPROP\_IRowsetLocate** 介面。  在資料列集建立期間做維護正確狀態。  
  
 當消費者呼叫 **IOpenRowset::OpenRowset** 或 `ICommand::Execute`時，會呼叫這個方法。  
  
 如果消費者開啟物件並要求選擇性介面，提供者會將屬性設定為與該介面的 `VARIANT_TRUE`。  在提供者的 **Execute**呼叫方法之前，要允許特定處理屬性 **OnInterfaceRequested** 呼叫。  根據預設， **OnInterfaceRequested** 處理下列介面:  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   **IConnectionPointContainer**  
  
-   `IRowsetScroll`  
  
 如果您希望處理其他介面，請在這個函式覆寫您的資料來源、工作階段、命令或資料列集類別以處理函式。  您的覆寫應該經歷正常 set\/get 屬性的介面以確保設定屬性會一同設定所有繫結的屬性 \(請參閱 [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)\)。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CUtlProps 類別](../../data/oledb/cutlprops-class.md)