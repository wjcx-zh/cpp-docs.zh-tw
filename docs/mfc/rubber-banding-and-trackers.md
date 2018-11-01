---
title: 拖放矩形和追蹤器
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
ms.openlocfilehash: f15256f99a744273b3487925bf273ad563c32aff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450800"
---
# <a name="rubber-banding-and-trackers"></a>拖放矩形和追蹤器

另一個追蹤器隨附的功能是「拖放矩形」選取範圍，可讓使用者透過在要選取的項目附近拖曳縮放矩形來選取多個 OLE 項目。 當使用者放開滑鼠左鍵時，將會選取使用者在區域中選取的項目，並可供使用者操作。 例如，使用者可以將選取項目拖曳到另一個容器應用程式。

實作這項功能需要一些額外的程式碼，在您的應用程式 WM_LBUTTONDOWN 處理常式函式。

下列程式碼範例實作拖放矩形選取範圍和其他功能。

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

如果您想要允許還原方向的追蹤程式，拖放矩形期間，您應該呼叫[crecttracker:: Trackrubberband](../mfc/reference/crecttracker-class.md#trackrubberband)第三個參數設定為 **，則為 TRUE**。 請記住，允許還原方向有時候會使[crecttracker:: M_rect](../mfc/reference/crecttracker-class.md#m_rect)反轉。 這可以藉由呼叫更正[Normalizerect](../atl-mfc-shared/reference/crect-class.md#normalizerect)。

如需詳細資訊，請參閱 <<c0> [ 容器用戶端項目](../mfc/containers-client-items.md)並[自訂拖曳和置放](../mfc/drag-and-drop-customizing.md)。

## <a name="see-also"></a>另請參閱

[追蹤器：在 OLE 應用程式中實作追蹤器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[CRectTracker 類別](../mfc/reference/crecttracker-class.md)
