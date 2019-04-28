---
title: ATL 控制項：一般支援類別
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
ms.openlocfilehash: 3f00348ab0c9f25bdd4f6b7a2b05cd4b82ea48e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262810"
---
# <a name="controls-general-support-classes"></a>控制項:一般支援類別

下列類別會提供一般支援，ATL 控制項：

- [CComControl](../atl/reference/ccomcontrol-class.md) ATL 控制項不可或缺的 helper 函式和資料成員所組成。

- [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md)提供控制項所需的方法。

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md)與控制項提供透過其中一個容器進行通訊的主要方法。 管理啟用和停用就地控制項的作業。

- [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md)結合成單一的呼叫，以協助避免延遲載入的控制項時的容器的初始化。

- [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md)提供最少的滑鼠互動，否則為非作用中的控制項。

## <a name="sample-program"></a>範例程式

[ATLFire](../overview/visual-cpp-samples.md)

## <a name="related-articles"></a>相關文章

[ATL 教學課程](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../atl/atl-class-overview.md)
