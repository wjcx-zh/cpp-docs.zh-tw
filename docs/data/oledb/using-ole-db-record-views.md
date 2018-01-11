---
title: "使用 OLE DB 資料錄檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03e88eaafa82e346c720810bf567d867a9cd6096
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-ole-db-record-views"></a>使用 OLE DB 資料錄檢視
如果您想要在 MFC 應用程式中顯示 OLE DB 資料列集資料，您應該使用 MFC 類別[COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)。 從資料錄檢視物件建立`COleDBRecordView`可讓您在 MFC 控制項中顯示資料庫記錄。 資料錄檢視是直接連接至所建立的 OLE DB 資料列集物件的對話方塊表單檢視`CRowset`範本類別。 取得資料列集物件的控制代碼很簡單：  
  
```  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 檢視會顯示的欄位`CRowset`對話方塊的控制項中的物件。 `COleDBRecordView`物件會使用對話方塊資料交換 (DDX) 和導覽功能內建在`CRowset`(**MoveFirst**， `MoveNext`， `MovePrev`，和`MoveLast`) 來自動化資料移動之間的控制項在表單和資料列集的欄位。 `COleDBRecordView`會追蹤的資料列集中的使用者的位置，使資料錄檢視可以更新使用者介面並提供[OnMove](../../mfc/reference/coledbrecordview-class.md#onmove)更新目前的記錄，再移至另一個方法。  
  
 您可以使用 DDX 函式與**COleDbRecordView**可直接從資料庫資料錄集取得資料，並顯示在對話方塊的控制項。 您應該使用**DDX_\*** 方法 (例如`DDX_Text`)，而非**DDX_Field\*** 函式 (例如`DDX_FieldText`) 與**COleDbRecordView**.  
  
## <a name="see-also"></a>請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)   
 [COleDBRecordView 類別](../../mfc/reference/coledbrecordview-class.md)