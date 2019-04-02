---
title: 拖放 (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: 98bd58745e56a62bf5700e9b5fe4963a7b584953
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58766796"
---
# <a name="drag-and-drop-ole"></a>拖放 (OLE)

OLE 的拖放功能主要是複製並貼上資料的捷徑。 當您使用 [剪貼簿] 複製或貼上資料時，需要幾個步驟。 您選取的資料，請按一下**剪下**或是**複製**從**編輯** 功能表中，移至目的地檔案、 視窗或應用程式中，將游標放在想要的位置，然後按一下**貼上**從**編輯**功能表。

OLE 拖放與檔案管理員拖放機制不同，它只能處理檔名且是特別設計用來傳遞檔名給應用程式。 OLE 拖放的應用範圍更為廣泛。 它允許您拖放可以放置在剪貼簿上的任何資料。

當您使用 OLE 拖放時，您會從整個流程中移除兩個步驟。 您會從來源視窗 (置放來源) 選取資料，將它拖曳至想要的目的 (置放目標)，並透過放開滑鼠按鈕置放該資料。 此作業不需要使用功能表，且比複製/貼上操作流程更快。 其唯一的需求是必須開啟置放來源和置放目標，且至少有部分顯示在螢幕上。

使用 OLE 拖放功能，您可以在文件中的不同位置、不同的文件或是應用程式之間傳輸資料。 它可以在容器或伺服器應用程式中實作，而且所有應用程式都可以是置放來源、置放目標或兩者都是。 如果某個應用程式同時實作為支援置放來源和置放目標，則可以在子視窗之間，或在一個視窗中進行拖放。 此功能可讓應用程式更容易使用。

如果您只想要使用 OLE 的拖放功能，請參閱[將拖放：自訂](../mfc/drag-and-drop-customizing.md)。 您可以使用在該文件中說明的技巧，讓非 OLE 應用程式成為置放來源。 發行項[將拖放：實作置放目標](../mfc/drag-and-drop-implementing-a-drop-target.md)說明如何實作 OLE 和非 OLE 應用程式的置放目標支援。 它也會檢查 MFC OLE 範例很有幫助[OCLIENT](../overview/visual-cpp-samples.md)並[HIERSVR](../overview/visual-cpp-samples.md)。

如果您未讀[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)一系列的文章，建議您立刻登出。 這些文章說明資料傳輸的基本概念，以及如何在您的應用程式實作它。

如需拖放功能的詳細資訊，請參閱：

- [拖放：實作置放來源](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [拖放：實作置放目標](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [拖放：自訂](../mfc/drag-and-drop-customizing.md)

## <a name="see-also"></a>另請參閱

[OLE](../mfc/ole-in-mfc.md)<br/>
[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)
