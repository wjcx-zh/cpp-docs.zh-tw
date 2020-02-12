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
ms.openlocfilehash: 095f3c15546466c6a495f6aa348990ed69b04a9e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127362"
---
# <a name="rubber-banding-and-trackers"></a>拖放矩形和追蹤器

另一個追蹤器隨附的功能是「拖放矩形」選取範圍，可讓使用者透過在要選取的項目附近拖曳縮放矩形來選取多個 OLE 項目。 當使用者放開滑鼠左鍵時，將會選取使用者在區域中選取的項目，並可供使用者操作。 例如，使用者可以將選取項目拖曳到另一個容器應用程式。

若要執行此功能，您的應用程式 WM_LBUTTONDOWN 處理常式函式中需要一些額外的程式碼。

下列程式碼範例實作拖放矩形選取範圍和其他功能。

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

如果您想要在「橡膠層」期間允許追蹤程式的方向，您應該呼叫[CRectTracker：： TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) ，並將第三個參數設定為**TRUE**。 請記住，允許可還原的方向有時會導致[CRectTracker：： m_rect](../mfc/reference/crecttracker-class.md#m_rect)變得反轉。 這可以藉由呼叫[CRect：： NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect)來更正。

如需詳細資訊，請參閱[容器用戶端專案](../mfc/containers-client-items.md)和[OLE 拖放：自訂拖放](../mfc/drag-and-drop-ole.md#customize-drag-and-drop)。

## <a name="see-also"></a>另請參閱

[追蹤器：在 OLE 應用程式中實作追蹤器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[CRectTracker 類別](../mfc/reference/crecttracker-class.md)
