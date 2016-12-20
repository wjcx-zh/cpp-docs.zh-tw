---
title: "ATL 資料庫類別 (OLE DB 樣板) | Microsoft Docs"
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
  - "資料庫類別 [C++], ATL"
  - "資料庫類別 [C++], OLE DB"
  - "OLE DB 樣板 [C++], ATL 資料庫類別"
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 資料庫類別 (OLE DB 樣板)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 提供多個 OLE DB 的實作，也就是一組 COM 介面，提供了一致的方法來存取不同資訊來源和格式的資料。  
  
 OLE DB 樣板是 ATL 裡的 C\+\+ 樣板，它提供了實作許多常用 OLE DB 介面的類別，使得此高性能的 OLE DB 資料庫技術更易於使用。  
  
 這個樣板程式庫包含兩個部分：  
  
-   [OLE DB 消費者樣板](../data/oledb/ole-db-consumer-templates-cpp.md)：用來實作 OLE DB 用戶端 \(消費者\) 應用程式  
  
-   [OLE DB 提供者樣板](../data/oledb/ole-db-provider-templates-cpp.md)：用來實作 OLE DB 伺服器 \(提供者\) 應用程式  
  
 除此之外，[OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)也提供建立 OLE DB 消費者的便利方式。  OLE DB 屬性根據 OLE DB 消費者樣板來插入程式碼，以建立運作中的 OLE DB 消費者。  
  
 注意，MFC 程式庫包含一個類別：[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)，它會在控制項內顯示資料庫記錄。  該檢視是一個直接連接至 `CRowset` 物件的表單檢視，它會將 `CRowset` 物件的欄位顯示在對話方塊樣板的控制項內。  
  
 如需詳細資訊，請參閱 [OLE DB 程式設計](../data/oledb/ole-db-programming.md) 和 [OLE DB 程式設計人員的方針](http://go.microsoft.com/fwlink/?LinkId=121548)。  
  
## 請參閱  
 [建立 OLE DB 消費者](../data/oledb/creating-an-ole-db-consumer.md)   
 [建立 OLE DB 提供者](../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB 消費者樣板參考](../data/oledb/ole-db-consumer-templates-reference.md)   
 [OLE DB 提供者樣板參考](../data/oledb/ole-db-provider-templates-reference.md)   
 [OLE DB Templates Samples](http://msdn.microsoft.com/zh-tw/08958863-0b5f-41ad-ae99-fca7440c553c)