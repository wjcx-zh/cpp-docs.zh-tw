---
title: OLE DB 樣板、 屬性和其他實作 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef9baf43ded1533eb7f4962db7344f9dc1def0ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB 樣板、屬性和其他實作
## <a name="atl-ole-db-templates"></a>ATL OLE DB 樣板  
 OLE DB 樣板，也就是 ATL (Active Template Library) 的一部分，簡化高效能的 OLE DB 資料庫技術提供實作許多常用的 OLE DB 介面的類別使用。 此範本以及程式庫隨附支援精靈建立 OLE DB 起始應用程式。  
  
 此範本程式庫包含兩個部分：  
  
-   **OLE DB 消費者樣板**用來實作 OLE DB 用戶端 （消費者） 應用程式。  
  
-   **OLE DB 提供者樣板**用來實作 OLE DB 伺服器 （提供者） 應用程式。  
  
 若要使用此 OLE DB 樣板，必須熟悉 C++ 樣板、COM 和 OLE DB 介面。 如果您不熟悉使用 OLE DB，請參閱[OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)。  
  
 如需詳細資訊，您可以：  
  
-   閱讀有關的主題[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)或[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)。  
  
-   建立[OLE DB 取用者](../../data/oledb/creating-an-ole-db-consumer.md)或[OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)。  
  
-   查看清單[OLE DB 取用者類別](../../data/oledb/ole-db-consumer-templates-reference.md)或[OLE DB 提供者類別](../../data/oledb/ole-db-provider-templates-reference.md)。  
  
-   查看清單[OLE DB 範本範例](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)。  
  
-   請參閱[OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)（在 Windows SDK 中)。  
  
## <a name="ole-db-attributes"></a>OLE DB 屬性  
 [OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)提供便利的方式來建立 OLE DB 取用者。 OLE DB 屬性插入程式碼，根據[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-reference.md)建立使用 OLE DB 消費者和提供者。 如果您需要指定屬性不支援的功能，您可以使用屬性搭配 OLE DB 樣板程式碼中。  
  
## <a name="mfc-ole-db-classes"></a>MFC OLE DB 類別  
 MFC 程式庫有一個類別， [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)，可在控制項中顯示資料庫記錄。 檢視是表單檢視，直接連接至`CRowset`物件，並顯示欄位的`CRowset`對話方塊範本的控制項中的物件。 它也提供的預設實作移動到第一個下, 一個、 上一個或最後一筆和更新記錄目前的檢視介面。 如需詳細資訊，請參閱`COleDBRecordView`。  
  
## <a name="ole-db-sdk-interfaces"></a>OLE DB SDK 介面  
 在 OLE DB 範本不支援 OLE DB 功能的情況下，您需要使用 OLE DB 介面本身。 如需詳細資訊，請參閱[OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [OLE DB 程式設計概觀](../../data/oledb/ole-db-programming-overview.md)