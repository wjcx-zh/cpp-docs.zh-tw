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
ms.openlocfilehash: 530b1772dfb623689facd5b14eebe9ed1eacd4fd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624136"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE 拖放和資料傳輸類別

這些類別會在 OLE 資料傳輸中使用。 它們可讓您使用剪貼簿或透過拖放方式，在應用程式之間傳輸資料。

[COleDropSource](reference/coledropsource-class.md)<br/>
控制從開始到完成的拖放作業。 這個類別會決定拖曳作業何時開始和結束的時間。 它也會在拖放作業期間顯示資料指標的意見反應。

[COleDataSource](reference/coledatasource-class.md)<br/>
應用程式為數據傳輸提供資料時使用。 `COleDataSource`可以視為物件導向的剪貼簿物件。

[COleDropTarget](reference/coledroptarget-class.md)<br/>
表示拖放作業的目標。 `COleDropTarget`物件會對應至螢幕上的視窗。 它會決定是否要接受任何拖放到其中的資料，並執行實際的 drop 作業。

[COleDataObject](reference/coledataobject-class.md)<br/>
用來做為的接收者端 `COleDataSource` 。 `COleDataObject`物件可讓您存取由物件儲存的資料 `COleDataSource` 。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
