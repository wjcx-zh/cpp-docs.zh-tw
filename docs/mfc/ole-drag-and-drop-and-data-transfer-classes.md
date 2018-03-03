---
title: "OLE 拖放和資料傳輸類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e8c5a54184bcf6450bf39b39a6b90d7865c09d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE 拖放和資料傳輸類別
OLE 資料傳輸中使用這些類別。 它們允許應用程式使用剪貼簿或透過拖曳和卸除之間傳輸資料。  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 控制從開始到完成拖放作業。 這個類別會決定當拖曳作業開始和結束時。 也會在拖放作業期間顯示資料指標的意見反應。  
  
 [COleDataSource](../mfc/reference/coledatasource-class.md)  
 應用程式提供資料傳輸的資料時使用。 `COleDataSource`無法為物件導向的剪貼簿物件檢視。  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 表示拖放作業的目標。 A`COleDropTarget`物件會對應至螢幕上的視窗。 它會判斷是否要接受任何資料拖曳至其本身，並實作實際的卸除作業。  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 做為讓接收者端`COleDataSource`。 `COleDataObject`物件提供存取所儲存的資料`COleDataSource`物件。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

