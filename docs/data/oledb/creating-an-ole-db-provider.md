---
title: 建立 OLE DB 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 10/13/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c3d94bec2638901f542dfa7c412da0de9a60942
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078293"
---
# <a name="creating-an-ole-db-provider"></a>建立 OLE DB 提供者

建立 OLE DB 提供者的建議的方式是使用精靈來建立的 ATL COM 專案和提供者，然後修改使用 OLE DB 範本的檔案。 自訂您的提供者後，您可以標記為註解不必要的屬性，並新增選擇性的介面。

基本步驟如下：

1. 使用**ATL 專案精靈**來建立基本專案檔並**ATL OLEDB 提供者精靈**來建立提供者 (選取**ATL OLEDB 提供者**從**已安裝** > **Visual c + +** > **ATL**資料夾中的**加入新項目**)。

   > [!NOTE]
   > 專案必須包含 MFC 支援加入之前**ATL OLEDB 提供者**。

1. 修改中的程式碼`Execute`方法中的[CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md)。 如需範例，請參閱[讀取字串至 OLE DB 提供者](../../data/oledb/reading-strings-into-the-ole-db-provider.md)。

1. 此屬性對應中編輯[CustomDS.h](cmyprovidersource-myproviderds-h.md)， [CustomSess.h](cmyprovidersession-myprovidersess-h.md)，並[CustomRS.h](cmyproviderrowset-myproviderrs-h.md)。 此精靈會建立包含提供者可能會實作的所有屬性的屬性對應。 瀏覽屬性對應，並移除或註解您的提供者不需要支援的屬性。

1. 更新 PROVIDER_COLUMN_MAP，可以在中找到[CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md)。 如需範例，請參閱[儲存字串中的 OLE DB 提供者](../../data/oledb/storing-strings-in-the-ole-db-provider.md)。

1. 當您準備好測試您的提供者時，您可以嘗試尋找的提供者在提供者的列舉型別來測試。 例如尋找提供者列舉中的測試程式碼的詳細資訊，請參閱[CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)並[DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)範例或中的範例[實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)。

1. 新增您想要的任何其他介面。 如需範例，請參閱[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)。

   > [!NOTE]
   > 根據預設，精靈會產生為 OLE DB 層級 0 相容的程式碼。 若要確保您的應用程式層級 0 相容，請不要移除精靈所產生的任何的介面程式碼。

## <a name="see-also"></a>另請參閱

[CatDB 範例： 資料來源結構描述的瀏覽器](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[DBViewer 範例： 資料庫瀏覽器](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)
