---
title: 使用 OLE DB 資料錄檢視 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: febb247e96669951ea24b3e1633fa0857a6acf7c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083200"
---
# <a name="using-ole-db-record-views"></a>使用 OLE DB 資料錄檢視

如果您想要在 MFC 應用程式中顯示 OLE DB 資料列集資料，請使用 MFC 類別[COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)。 資料錄檢視物件從建立`COleDBRecordView`可讓您在 MFC 控制項中顯示資料庫記錄。 資料錄檢視是直接連線到所建立的 OLE DB 資料列集物件的對話方塊表單檢視`CRowset`範本類別。 取得資料列集物件的控制代碼很簡單：

```cpp
COleDBRecordView myRecordView;
...
// CProductAccessor is a user record class
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();
```

檢視會顯示的欄位`CRowset`對話方塊的控制項中的物件。 `COleDBRecordView`物件會使用對話方塊資料交換 (DDX)，並瀏覽功能內建`CRowset`(`MoveFirst`， `MoveNext`， `MovePrev`，和`MoveLast`) 來自動化的表單上控制項之間的資料移動與資料列集的欄位。 `COleDBRecordView` 會追蹤的資料列集中的使用者的位置，以便資料錄檢視可以更新使用者介面並提供[OnMove](../../mfc/reference/coledbrecordview-class.md#onmove)方法來更新目前的記錄，再移至另一個。

您可以使用 DDX 函式與`COleDbRecordView`直接從資料庫資料錄集取得資料，並顯示在對話方塊控制項。 使用**DDX_** <strong>\*</strong>方法 (例如`DDX_Text`)，而非**DDX_Field** <strong>\*</strong>函式 （這類`DDX_FieldText`) 與`COleDbRecordView`。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)<br/>
[COleDBRecordView 類別](../../mfc/reference/coledbrecordview-class.md)<br/>
