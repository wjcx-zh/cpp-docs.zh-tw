---
title: OLE DB 樣板、屬性和其他實作
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 217db304c7d0b5723b7af383e07290f160cc9465
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500921"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB 樣板、屬性和其他實作

## <a name="atl-ole-db-templates"></a>ATL OLE DB 範本

OLE DB 的範本（屬於 ATL (Active Template Library) 的一部分）提供可執行許多常用 OLE DB 介面的類別，讓您更容易使用高效能 OLE DB 資料庫技術。 以及此範本庫的 wizard 支援，可讓您建立 OLE DB 入門應用程式。

此範本程式庫包含兩個部分：

- **OLE DB 取用者範本** 用來執行 OLE DB 用戶端 (取用者) 應用程式。

- **OLE DB 提供者範本** 用來執行 OLE DB server (提供者) 應用程式。

若要使用此 OLE DB 樣板，必須熟悉 C++ 樣板、COM 和 OLE DB 介面。 如果您不熟悉 OLE DB，請參閱 [OLE DB 程式設計人員參考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)。

如需詳細資訊，您可以：

- 閱讀 [OLE DB 取用者範本](../../data/oledb/ole-db-consumer-templates-cpp.md) 或 [OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)的相關主題。

- 建立 [OLE DB 取用者](../../data/oledb/creating-an-ole-db-consumer.md) 或 [OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)。

- 請參閱 OLE DB 取用 [者類別](../../data/oledb/ole-db-consumer-templates-reference.md) 或 [OLE DB 提供者類別](../../data/oledb/ole-db-provider-templates-reference.md)的清單。

- 請參閱 [OLE DB 範本範例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)的清單。

- 請參閱 Windows SDK) 中 OLE DB 程式設計 [人員參考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (。

## <a name="ole-db-attributes"></a>OLE DB 屬性

OLE DB 的取用 [者屬性](../../windows/attributes/ole-db-consumer-attributes.md) 提供了一個便利的方式來建立 OLE DB 取用者。 OLE DB 屬性會根據 [OLE DB 取用者範本](../../data/oledb/ole-db-consumer-templates-reference.md) 插入程式碼，以建立工作 OLE DB 取用者和提供者。 如果您需要指定屬性不支援的功能，您可以搭配程式碼中的屬性使用 OLE DB 範本。

## <a name="mfc-ole-db-classes"></a>MFC OLE DB 類別

MFC 程式庫有一個類別 [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)，可在控制項中顯示資料庫記錄。 視圖是直接連接至物件的表單檢視 `CRowset` ，會 `CRowset` 在對話方塊範本的控制項中顯示物件的欄位。 此外，它也會提供移至第一個、下一個、上一個或最後一筆記錄的預設執行，以及用來更新目前視圖中之記錄的介面。 如需詳細資訊，請參閱`COleDBRecordView`。

## <a name="ole-db-sdk-interfaces"></a>OLE DB SDK 介面

在 OLE DB 範本不支援 OLE DB 功能的情況下，您需要使用 OLE DB 介面本身。 如需詳細資訊，請參閱 Windows SDK 中的 OLE DB 程式設計 [人員參考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) 。

## <a name="see-also"></a>另請參閱

[OLE DB 程式設計](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 程式設計總覽](../../data/oledb/ole-db-programming-overview.md)
