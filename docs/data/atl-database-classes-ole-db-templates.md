---
title: ATL 資料庫類別 (OLE DB 樣板)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: 5b13a27540b12e7ac1503fbf7cd0e1fe396ce8c8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501891"
---
# <a name="atl-database-classes-ole-db-templates"></a>ATL 資料庫類別 (OLE DB 樣板)

Microsoft 提供數個 OLE DB 的執行，這是一組 COM 介面，可讓您統一存取各種資訊來源和格式的資料。

OLE DB 範本是 ATL 中的 c + + 範本，可讓您藉由提供可執行許多常用 OLE DB 介面的類別，讓 OLE DB 的資料庫技術更容易使用。

此範本程式庫包含兩個部分：

- [OLE DB 取用者範本](../data/oledb/ole-db-consumer-templates-cpp.md) 用來執行 OLE DB 用戶端 (取用者) 應用程式。

- [OLE DB 提供者範本](../data/oledb/ole-db-provider-templates-cpp.md) 用來執行 OLE DB server (提供者) 應用程式。

此外，OLE DB 的取用 [者屬性](../windows/attributes/ole-db-consumer-attributes.md) 提供了一個便利的方式來建立 OLE DB 取用者。 OLE DB 屬性會根據 OLE DB 取用者範本插入程式碼，以建立工作 OLE DB 取用者。

請注意，MFC 程式庫包含一個類別 [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)，可在控制項中顯示資料庫記錄。 視圖是直接連接至物件的表單檢視 `CRowset` ，會 `CRowset` 在對話方塊範本的控制項中顯示物件的欄位。

如需詳細資訊，請參閱 [OLE DB 程式設計](../data/oledb/ole-db-programming.md) 和 OLE DB 程式設計 [人員指南](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)。

## <a name="see-also"></a>另請參閱

[建立 OLE DB 取用者](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[建立 OLE DB 提供者](../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 取用者範本參考](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 提供者範本參考](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 範本範例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)
