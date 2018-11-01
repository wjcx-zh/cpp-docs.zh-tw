---
title: 追蹤器
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
ms.openlocfilehash: 74e70f989d3803b11f05150f9b55c6dfe79ed876
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481948"
---
# <a name="trackers"></a>追蹤器

[CRectTracker](../mfc/reference/crecttracker-class.md)類別會提供您的應用程式和您的使用者，藉由提供各種不同的顯示樣式中的矩形項目之間的使用者介面。 這些樣式包含純色、 規劃、 或虛線框線;規劃的模式，它涵蓋了項目;可以是位於外部或內部框線的調整大小控點。 追蹤器通常用於搭配 OLE 項目，也就是物件衍生自`COleClientItem`。 追蹤器矩形的目前狀態的項目提供視覺提示。

MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)示範使用追蹤器與 OLE 用戶端項目從觀點來看的容器應用程式的通用介面。 如需示範不同的樣式以及追蹤器物件的能力，請參閱 MFC 一般範例[TRACKER](../visual-cpp-samples.md)。

如需有關在 OLE 應用程式中實作追蹤器的詳細資訊，請參閱[追蹤器： 在 OLE 應用程式中實作的追蹤器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>另請參閱

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleClientItem 類別](../mfc/reference/coleclientitem-class.md)
