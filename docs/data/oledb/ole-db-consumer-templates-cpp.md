---
title: OLE DB 消費者樣板 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- databases [C++], OLE DB templates
- OLE DB consumers [C++], data access
- OLE DB consumer templates [C++]
- databases [C++], consumers
ms.assetid: d3e42612-0bc0-4d65-9c32-0e8a7b219e82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 39264ed7485e67377963316730689645c73f185f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-consumer-templates-c"></a>OLE DB 消費者樣板 (C++)
OLE DB 消費者樣板可以支援 OLE DB 2.6 版規格 (OLE DB 消費者樣板是以 OLE DB 2.6 做為測試對象，但並不支援規格裡的每一個介面)。消費者樣板可將為實作 OLE DB 消費者而必須撰寫的程式碼數量降到最低。 此樣板提供了：  
  
-   OLE DB 功能的簡易存取以及 ATL 和 MFC 的簡易整合。  
  
-   資料庫參數和資料行的簡易繫結模型。  
  
-   OLE DB 程式設計的原生 C/C++ 資料型別。  
  
 若要使用此 OLE DB 樣板，必須熟悉 C++ 樣板、COM 和 OLE DB 介面。 如果您還不熟悉如何使用 OLE DB，請參閱 [OLE DB 設計人員參考](https://msdn.microsoft.com/en-us/library/ms718124.aspx)。  
  
 OLE DB 樣板會支援現有的 OLE DB 物件模型而不是加入新的物件模型。 OLE DB 消費者樣板裡的上層類別相當於 OLE DB 規格中所定義的元件。 OLE DB 消費者樣板的設計包括一些進階功能，例如，用於資料列集的多重存取子。 使用樣板和多重繼承會使程式庫更小且具備彈性。  
  
## <a name="how-ole-db-consumers-access-data"></a>OLE DB 消費者如何存取資料  
 消費者可以使用的幾種類型物件將於下列主題中說明：  
  
-   [資料來源和工作階段](../../data/oledb/data-sources-and-sessions.md)  
  
-   [存取子和資料列集](../../data/oledb/accessors-and-rowsets.md)  
  
-   [命令和資料表](../../data/oledb/commands-and-tables.md)  
  
-   [使用者資料錄](../../data/oledb/user-records.md)  
  
 您必須先選取適合要存取之資料庫類型的 OLE DB 提供者 (例如，SQL、Oracle、ODBC 和 MSDS)，然後消費者才能進行任何想要的工作。 為了達到這個目的，您通常會使用列舉值 (請參閱 [資料來源和工作階段](../../data/oledb/cenumerator-class.md) 所說明的 [CEnumerator](../../data/oledb/data-sources-and-sessions.md))。  
  
 [資料來源物件](../../data/oledb/data-sources-and-sessions.md) 可以提供連接所選取之資料來源的必要連接資訊。 資料來源物件也包含驗證資訊 (例如登入名稱和密碼)，該資訊可用來給予使用者存取資料來源的使用權限。 資料來源物件會連接到資料庫，接著建立一個或多個工作階段物件。 每個 [工作階段物件](../../data/oledb/data-sources-and-sessions.md) 都會管理自己和該資料庫的互動關係 (即查詢和擷取資料)，而執行這些交易將獨立於其他現有的工作階段。  
  
 工作階段會建立資料列集和命令物件。 [命令物件](../../data/oledb/commands-and-tables.md) 可讓使用者與資料庫進行互動，例如，使用 SQL 命令。 [資料列集物件](../../data/oledb/accessors-and-rowsets.md) 是一組資料，您可以透過它瀏覽資料，並且在其中進行 [更新、刪除和插入資料列](../../data/oledb/updating-rowsets.md)。  
  
 OLE DB 消費者可以繫結資料庫的資料表資料行和區域變數；它會使用 [存取子](../../data/oledb/accessors-and-rowsets.md)來完成這個動作，該存取子包含消費者資料儲存方式的對應。 這個對應含有一組資料表資料行和消費者應用程式的本機緩衝區 (變數) 之間的繫結。  
  
 使用消費者時有一個重要的概念，就是您要在消費者中宣告兩個類別： [命令 (或資料表) 類別](../../data/oledb/commands-and-tables.md) 和 [使用者資料錄類別](../../data/oledb/user-records.md)。 您會透過命令 (或資料表) 類別存取資料列集，而此類別是繼承自存取子類別和資料列集類別。 使用者資料錄類別包含先前已說明的資料列集繫結對應。  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer.md)  
  
-   [通用 OLE DB 消費者案例 (範例)](../../data/oledb/working-with-ole-db-consumer-templates.md)  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)   
 [資料存取](../data-access-in-cpp.md)   
 [OLE DB SDK 文件](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [OLE DB 程式設計人員參考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)