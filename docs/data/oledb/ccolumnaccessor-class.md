---
title: "CColumnAccessor 類別 | Microsoft Docs"
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
  - "CColumnAccessor"
  - "ATL::CColumnAccessor"
  - "ATL.CColumnAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CColumnAccessor 類別"
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CColumnAccessor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生插入的消費者程式碼。  
  
## 語法  
  
```  
class CColumnAccessor : public CAccessorBase  
```  
  
## 備註  
 在插入的程式碼，每行繫結為個別的存取子。  您應該對這個用於插入的程式碼的類別小心使用\(例如，您可能會偵錯時遇到這個工具\)，不過，您通常不需要直接使用其或其方法。  
  
 `CColumnAccessor` 會實作下列 Stub 方法，其中每個型別都功能上對應到其他存取子類別方法:  
  
-   `CColumnAccessor` 建構函式;執行個體化及初始化 `CColumnAccessor` 物件。  
  
-   `CreateAccessor`資料繫結配置記憶體結構和初始化的資料成員。  
  
-   **BindColumns** 對存取子的繫結資料行。  
  
-   **SetParameterBuffer** 參數的配置緩衝區。  
  
-   `AddParameter`將參數輸入到參數輸入結構。  
  
-   **HasOutputColumns** 判斷存取子是否輸出資料行  
  
-   **HasParameters** 判斷存取子是否有參數。  
  
-   `BindParameters` 繫結所建立的參數至資料行。  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)