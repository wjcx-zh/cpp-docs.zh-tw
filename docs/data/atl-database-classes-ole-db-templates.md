---
title: ATL 資料庫類別 （OLE DB 樣板） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5147610e580d3a67400893d41af8ad9728cc72a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071215"
---
# <a name="atl-database-classes-ole-db-templates"></a>ATL 資料庫類別 (OLE DB 樣板)

Microsoft 提供數個 OLE DB 的實作，一組 COM 介面，可讓您統一存取各種資訊來源和格式的資料。  OLE DB 正式被取代;這份文件適用於開發人員會維護舊版的程式碼。 新的應用程式應該使用 ODBC 來連接到 SQL 資料來源。

OLE DB 範本是 ATL 中的 c + + 範本，讓您更輕鬆地提供實作許多常用的 OLE DB 介面的類別來使用 OLE DB 資料庫技術。

此範本程式庫包含兩個部分：

- [OLE DB 消費者樣板](../data/oledb/ole-db-consumer-templates-cpp.md)用來實作 OLE DB 用戶端 （消費者） 應用程式。

- [OLE DB 提供者樣板](../data/oledb/ole-db-provider-templates-cpp.md)用來實作 OLE DB 伺服器 （提供者） 應用程式。

颾魤 ㄛ [OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)提供便利的方式，來建立 OLE DB 取用者。 OLE DB 屬性會插入基礎 OLE DB 消費者範本來建立使用 OLE DB 取用者的程式碼。

請注意，MFC 程式庫包含一個類別， [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)，會顯示在控制項中的資料庫記錄。 檢視是表單檢視，直接連接到`CRowset`物件，並會顯示的欄位`CRowset`對話方塊範本的控制項中的物件。

如需詳細資訊，請參閱 < [OLE DB 程式設計](../data/oledb/ole-db-programming.md)並[OLE DB 程式設計人員指南](/previous-versions/windows/desktop/ms713643)。

## <a name="see-also"></a>另請參閱

[建立 OLE DB 消費者](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[建立 OLE DB 提供者](../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 消費者範本參考](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 提供者範本參考](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 範本範例](https://github.com/Microsoft/VCSamples)