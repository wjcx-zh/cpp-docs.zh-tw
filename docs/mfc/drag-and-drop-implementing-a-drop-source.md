---
title: "將拖放： 實作置放來源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 301980f7f5a901aa4e2cba40357b18311eef581e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>拖放：實作置放來源
本文說明如何取得您的應用程式提供資料給拖放作業。  
  
 基本實作置放來源是相當簡單。 第一個步驟是判斷哪些事件開始拖曳作業。 建議的使用者介面指導方針定義拖曳作業開始時，為選取的資料和`WM_LBUTTONDOWN`內選取的資料點上所發生的事件。 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)和[HIERSVR](../visual-cpp-samples.md)遵循這些指導方針。  
  
 如果您的應用程式是一個容器，而且選取的資料連結或內嵌的物件的型別`COleClientItem`，呼叫其`DoDragDrop`成員函式。 否則，便建構`COleDataSource`物件、 選取項目，以將其初始化，並且呼叫資料來源物件`DoDragDrop`成員函式。 如果您的應用程式伺服器，請使用`COleServerItem::DoDragDrop`。 如需自訂標準拖放行為的資訊，請參閱文章[將拖放： 自訂](../mfc/drag-and-drop-customizing.md)。  
  
 如果`DoDragDrop`傳回`DROPEFFECT_MOVE`，立即刪除來源文件的來源資料。 從任何其他傳回值`DoDragDrop`置放來源上的任何作用。  
  
 如需詳細資訊，請參閱:  
  
-   [實作置放目標](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [自訂儲存拖放](../mfc/drag-and-drop-customizing.md)  
  
-   [建立和終結 OLE 資料物件和資料來源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [管理 OLE 資料物件和資料來源](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>請參閱  
 [拖放 (OLE)](../mfc/drag-and-drop-ole.md)   
 [Coledatasource:: Dodragdrop](../mfc/reference/coledatasource-class.md#dodragdrop)   
 [COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)   
 [CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)

