---
title: 拖放：自訂
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
ms.openlocfilehash: b4749f8d45c962f8b9217e4c6367538d3e6a3608
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405946"
---
# <a name="drag-and-drop-customizing"></a>拖放：自訂

拖放功能的預設實作對大部分應用程式而言已經足夠。 不過，不過應用程式可能需要變更這個標準行為。 本文說明變更這些預設值的必要步驟。 此外，您可以使用這項技術建立不支援將複合文件作為放置來源的應用程式。

如果您自訂標準 OLE 拖放行為，或者有非 OLE 應用程式，就必須建立 `COleDataSource` 物件以包含資料。 當使用者開始拖放作業時，您的程式碼應該從此物件而不是從其他支援拖放作業的類別呼叫 `DoDragDrop` 函式。

或者，您可以建立 `COleDropSource` 物件來控制置放並且根據您要變更的行為類型覆寫其中的一些函式。 這個置放來源物件隨後會傳遞至 `COleDataSource::DoDragDrop`，以變更這些函式的預設行為。 這些不同選項可讓您在支援應用程式的拖放作業時擁有更多的彈性。 如需有關資料來源的詳細資訊，請參閱[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)。

您可以覆寫下列函式以自訂拖放作業：

|覆寫|自訂|
|--------------|------------------|
|`OnBeginDrag`|如何在呼叫 `DoDragDrop`之後啟始拖曳。|
|`GiveFeedback`|不同置放結果的視覺化回饋，例如游標外觀。|
|`QueryContinueDrag`|拖放作業的終止。 此函式可讓您在拖曳作業期間檢查輔助按鍵狀態。|

## <a name="see-also"></a>另請參閱

[拖放 (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDropSource 類別](../mfc/reference/coledropsource-class.md)<br/>
[COleDataSource 類別](../mfc/reference/coledatasource-class.md)
