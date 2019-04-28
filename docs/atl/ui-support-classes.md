---
title: UI 支援類別 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- user interfaces, support classes
- user interfaces, ATL classes
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
ms.openlocfilehash: 4aa508a028eb0a90233b7baa34db9ee78bbe2b83
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274205"
---
# <a name="ui-support-classes"></a>UI 支援類別

下列類別會提供一般的 UI 支援：

- [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md)介面的 Microsoft HTML 剖析和轉譯引擎。

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md)與控制項提供透過其中一個容器進行通訊的主要方法。 管理啟用和停用就地控制項的作業。

- [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)管理就地控制項重新啟動。 啟用無視窗控制項以接收訊息，以及參與拖放作業。

- [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md)協助就地控制項與其容器之間的通訊。

- [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md)啟用控制項，使其直接顯示，並通知其顯示變更的容器。 提供無重繪閃動的繪圖、 非矩形和透明的控制項，並支援點擊測試。

## <a name="related-articles"></a>相關文章

[ATL 教學課程](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../atl/atl-class-overview.md)
