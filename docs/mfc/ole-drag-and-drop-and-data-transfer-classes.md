---
title: OLE 拖放和資料傳輸類別
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 7e01b6d5a7d14e0af4ca760e6e601e91359c8ab1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447622"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE 拖放和資料傳輸類別

這些類別會在 OLE 資料傳輸中使用。 它們可讓您使用剪貼簿或透過拖放方式，在應用程式之間傳輸資料。

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
控制從開始到完成的拖放作業。 這個類別會決定拖曳作業何時開始和結束的時間。 它也會在拖放作業期間顯示資料指標的意見反應。

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
應用程式為數據傳輸提供資料時使用。 `COleDataSource` 可以視為物件導向的剪貼簿物件。

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
表示拖放作業的目標。 `COleDropTarget` 物件會對應至螢幕上的視窗。 它會決定是否要接受任何拖放到其中的資料，並執行實際的 drop 作業。

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
用來做為 `COleDataSource`的接收者端。 `COleDataObject` 物件可讓您存取由 `COleDataSource` 物件所儲存的資料。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)
