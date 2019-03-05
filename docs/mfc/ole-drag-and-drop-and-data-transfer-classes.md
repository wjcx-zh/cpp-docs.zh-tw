---
title: OLE 拖放和資料傳輸類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: e30a358da55b29f9519bc1ab8ee5c93ada308d98
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284420"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE 拖放和資料傳輸類別

這些類別會用於 OLE 的資料傳輸。 允許在讓應用程式使用剪貼簿，或透過拖曳和置放之間傳輸的資料。

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
控制從開始到結束拖放作業。 這個類別會決定當拖曳作業開始和結束時。 它也會顯示拖放作業期間的資料指標的意見反應。

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
應用程式提供的資料傳輸的資料時使用。 `COleDataSource` 無法檢視做為物件導向的剪貼簿物件。

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
表示拖放作業的目標。 A`COleDropTarget`物件對應到螢幕上的視窗。 它會判斷是否要接受任何資料拖曳至其本身，並實作實際的卸除作業。

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
做為在接收者端`COleDataSource`。 `COleDataObject` 物件會提供所儲存資料的存取權`COleDataSource`物件。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
