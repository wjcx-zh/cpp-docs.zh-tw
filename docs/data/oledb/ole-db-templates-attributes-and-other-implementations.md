---
title: "OLE DB 樣板、屬性和其他實作 | Microsoft Docs"
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
  - "OLE DB 樣板"
  - "OLE DB 樣板, 關於 OLE DB 樣板"
  - "OLE DB, 實作"
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 樣板、屬性和其他實作
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## ATL OLE DB 樣板  
 OLE DB 樣板是 ATL \(Active Template Library\) 的一部分。它提供了實作許多常用 OLE DB 介面的類別，使得高效能的 OLE DB 資料庫技術更易於使用。  這個樣板程式庫還有支援建立 OLE DB 起始應用程式的精靈。  
  
 這個樣板程式庫包含兩個部分：  
  
-   **OLE DB 消費者樣板**：用來實作 OLE DB 用戶端 \(消費者\) 應用程式  
  
-   **OLE DB 提供者樣板**：用來實作 OLE DB 伺服器 \(提供者\) 應用程式  
  
 若要使用此 OLE DB 樣板，必須熟悉 C\+\+ 樣板、COM 和 OLE DB 介面。  如果您不熟悉 OLE DB，請參閱 [OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)。  
  
 如需詳細資訊，您可以：  
  
-   閱讀 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)或 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)的主題  
  
-   建立 [OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer.md)或 [OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   請參閱 [OLE DB 消費者類別](../../data/oledb/ole-db-consumer-templates-reference.md)或 [OLE DB 提供者類別](../../data/oledb/ole-db-provider-templates-reference.md)清單  
  
-   請參閱 [OLE DB 樣板範例](http://msdn.microsoft.com/zh-tw/08958863-0b5f-41ad-ae99-fca7440c553c)清單  
  
-   請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的 [OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)。  
  
## OLE DB 屬性  
 [OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)提供了建立 OLE DB 消費者的便利方法。  OLE DB 屬性 \(Attribute\) 插入以 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-reference.md)為基礎的程式碼，以建立可用的 OLE DB 消費者和提供者。  如果您需指定屬性不支援的功能，則您可以聯合 OLE DB 樣板與程式碼中的屬性一起使用。  
  
## MFC OLE DB 類別  
 MFC 程式庫具有一個 [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md) 類別，它會顯示控制項內的資料庫資料錄。  該檢視是一個直接連接至 `CRowset` 物件的表單檢視，它會將 `CRowset` 物件的欄位顯示在對話方塊樣板的控制項內。  對於移動至第一筆、下一筆、前一筆或最後一筆資料錄，它也提供了預設實作，還有提供一個用來更新目前檢視上資料錄的介面。  如需詳細資訊，請參閱`COleDBRecordView`。  
  
## OLE DB SDK 介面  
 對於 OLE DB 樣板沒有支援的 OLE DB 功能，您需要使用 OLE DB 介面本身。  如需詳細資訊，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的 [OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)。  
  
## 請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)