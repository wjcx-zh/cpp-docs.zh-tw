---
title: 資料物件和資料來源 (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
ms.openlocfilehash: 09e328171657c3c6557a5d77acae0f034e517955
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612481"
---
# <a name="data-objects-and-data-sources-ole"></a>資料物件和資料來源 (OLE)

使用剪貼簿或拖放功能執行資料傳輸時，資料會有來源端和目的端。 某個應用程式會提供複製資料，而另一個應用程式會接受貼上文字。 每個傳輸端需要執行不同的作業來成功傳輸相同資料。 Microsoft Foundation Class (MFC) 程式庫提供代表各傳輸端的兩個類別：

- 資料來源 (如 `COleDataSource` 物件實作) 代表資料傳輸的來源。 資料來源由來源應用程式在資料複製到剪貼簿，或當提供資料以供拖放作業使用時建立。

- 資料物件 (由 `COleDataObject` 物件實作) 代表資料傳輸的目的端。 資料物件在由目的端應用程式接收到放入的資料，或當被要求執行從剪貼簿貼上的作業時建立。

下列文件說明如何使用您應用程式中的資料物件和資料來源。 這份資訊適用於容器和伺服器應用程式，因為它們可能同時被要求複製並貼上資料。

- [資料物件和資料來源：建立和解構](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [資料物件和資料來源：管理](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>本節內容

[拖放](../mfc/drag-and-drop-ole.md)

[剪貼簿](../mfc/clipboard.md)

## <a name="see-also"></a>另請參閱

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleDataObject 類別](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource 類別](../mfc/reference/coledatasource-class.md)
