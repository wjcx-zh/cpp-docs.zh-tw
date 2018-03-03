---
title: "ATL 資料庫類別 （OLE DB 樣板） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ca7607c037cdb1f6a42a2267d64ef274d1041cb2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="atl-database-classes-ole-db-templates"></a>ATL 資料庫類別 (OLE DB 樣板)
Microsoft 提供數種實作的 OLE DB，一組 COM 介面，可讓您統一存取各種資訊來源和格式的資料。  OLE DB 已正式被取代。這份文件是針對開發人員會維護舊版的程式碼。 新的應用程式應該使用 ODBC 連接到 SQL 資料來源。
  
 OLE DB 樣板是 ATL 中的 c + + 範本可讓您更輕鬆地提供實作許多常用的 OLE DB 介面的類別使用 OLE DB 資料庫技術。  
  
 此範本程式庫包含兩個部分：  
  
-   [OLE DB 消費者樣板](../data/oledb/ole-db-consumer-templates-cpp.md)用來實作 OLE DB 用戶端 （消費者） 應用程式。  
  
-   [OLE DB 提供者樣板](../data/oledb/ole-db-provider-templates-cpp.md)用來實作 OLE DB 伺服器 （提供者） 應用程式。  
  
 此外， [OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)提供便利的方式來建立 OLE DB 取用者。 OLE DB 屬性插入程式碼，根據 OLE DB 消費者範本來建立使用 OLE DB 取用者。  
  
 請注意，MFC 程式庫包含一個類別， [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)，可在控制項中顯示資料庫記錄。 檢視是表單檢視，直接連接至`CRowset`物件，並顯示欄位的`CRowset`對話方塊範本的控制項中的物件。  
  
 如需詳細資訊，請參閱[OLE DB 程式設計](../data/oledb/ole-db-programming.md)和[OLE DB 程式設計人員指南](http://go.microsoft.com/fwlink/p/?linkid=121548)。  
  
## <a name="see-also"></a>請參閱  
 [建立 OLE DB 消費者](../data/oledb/creating-an-ole-db-consumer.md)   
 [建立 OLE DB 提供者](../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB 消費者樣板參考](../data/oledb/ole-db-consumer-templates-reference.md)   
 [OLE DB 提供者樣板參考](../data/oledb/ole-db-provider-templates-reference.md)   
 [OLE DB 範本範例](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)