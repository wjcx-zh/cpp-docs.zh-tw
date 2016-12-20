---
title: "CSession 類別 | Microsoft Docs"
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
  - "CSession"
  - "ATL::CSession"
  - "ATL.CSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSession 類別"
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSession 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示單一資料庫存取工作階段。  
  
## 語法  
  
```  
class CSession  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[Abort](../../data/oledb/csession-abort.md)|取消\(終止\)目前的交易。|  
|[關閉](../../data/oledb/csession-close.md)|結束工作階段。|  
|[認可](../../data/oledb/csession-commit.md)|認可交易。|  
|[GetTransactionInfo](../../data/oledb/csession-gettransactioninfo.md)|傳回有關交易的資訊。|  
|[開啟](../../data/oledb/csession-open.md)|啟動資料來源物件的新工作階段。|  
|[StartTransaction](../../data/oledb/csession-starttransaction.md)|啟動工作階段的一種新的交易。|  
  
## 備註  
 一或多個工作階段可以與每個提供者連接 \(資料來源\)，由 [CDataSource](../../data/oledb/cdatasource-class.md) 物件所表示。  若要建立 `CDataSource`的新 `CSession` ，請呼叫 [CSession::Open](../../data/oledb/csession-open.md)。  若要開始資料庫執行 `CSession` ，提供 `StartTransaction` 方法。  一旦交易開始，使用 **Commit** 方法，您可以對它，使用 **Abort** 方法，或是將它移除。  
  
## 需求  
 **標題:**  atldbcli.h  
  
## 請參閱  
 [CatDB](../../top/visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)