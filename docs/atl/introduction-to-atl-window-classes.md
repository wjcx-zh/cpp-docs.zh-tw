---
title: ATL 視窗類別簡介
ms.date: 11/04/2016
helpviewer_keywords:
- window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
ms.openlocfilehash: 987e2eab5fe4eec32d88b7c1528f1e3189fc925a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459796"
---
# <a name="introduction-to-atl-window-classes"></a>ATL 視窗類別簡介

下列的 ATL 類別被設計來實作和管理 windows︰

- [CWindow](../atl/reference/cwindow-class.md)可讓您附加的視窗控制代碼`CWindow`物件。 然後呼叫`CWindow`管理視窗的方法。

- [CWindowImpl](../atl/reference/cwindowimpl-class.md)可讓您實作新的視窗，並處理訊息的訊息對應。 您可以建立視窗根據新的 Windows 類別、 超級類別現有的類別或子類別化現有視窗。

- [CDialogImpl](../atl/reference/cdialogimpl-class.md)可讓您實作強制回應或非強制回應對話方塊方塊和處理訊息使用訊息對應。

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)是預先建置的類別，另一個類別中實作包含其訊息對應的視窗。 使用`CContainedWindowT`可讓您集中在一個班級中的訊息處理。

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)可讓您實作裝載 ActiveX 控制項對話方塊中 （強制回應或非強制回應）。

- [CSimpleDialog](../atl/reference/csimpledialog-class.md)可讓您實作基本功能的強制回應對話方塊。

- [CAxWindow](../atl/reference/caxwindow-class.md)可讓您實作裝載 ActiveX 控制項的視窗。

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md)可讓您實作裝載授權的 ActiveX 控制項的視窗。

除了特定的視窗類別，ATL 還提供旨在讓您更輕鬆的 ATL 視窗物件實作的數個類別。 分別為：

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)管理新的視窗類別的資訊。

- [CWinTraits](../atl/reference/cwintraits-class.md)並[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)提供標準化的 ATL 視窗物件的特徵的簡單方法。

## <a name="see-also"></a>另請參閱

[視窗類別](../atl/atl-window-classes.md)

