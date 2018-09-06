---
title: Windows 支援類別 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.windows
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9693fdc524953c9fa1070ec5e286cb2a999f5a0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767721"
---
# <a name="windows-support-classes"></a>Windows 支援類別

下列類別會提供適用於 windows 的支援：

- [_U_MENUorID](../atl/reference/u-menuorid-class.md)提供的包裝函式`CreateWindow`和`CreateWindowEx`。

- [CWindow](../atl/reference/cwindow-class.md)包含用於管理視窗的方法。 `CWindow` 是 `CWindowImpl`、`CDialogImpl` 和 `CContainedWindow` 的基底類別。

- [CWindowImpl](../atl/reference/cwindowimpl-class.md)實作新的視窗類別為基礎的視窗。 也可讓您子類別或超級類別的視窗。

- [CDialogImpl](../atl/reference/cdialogimpl-class.md)可實作對話方塊。

- [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)實作裝載 ActiveX 控制項對話方塊中 （強制回應或非強制回應）。

- [CSimpleDialog](../atl/reference/csimpledialog-class.md)實作基本功能的對話方塊 （強制回應或非強制回應）。

- [CAxWindow](../atl/reference/caxwindow-class.md)操作裝載 ActiveX 控制項的視窗。

- [CAxWindow2T](../atl/reference/caxwindow2t-class.md)提供方法來管理裝載 ActiveX 控制項，也有支援授權的 ActiveX 控制項裝載的視窗。

- [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)實作包含在另一個物件的視窗。

- [CWndClassInfo](../atl/reference/cwndclassinfo-class.md)管理新的視窗類別的資訊。

- [CDynamicChain](../atl/reference/cdynamicchain-class.md)支援訊息對應的動態鏈結。

- [CMessageMap](../atl/reference/cmessagemap-class.md)允許物件公開其訊息對應至其他物件。

- [CWinTraits](../atl/reference/cwintraits-class.md)提供簡單的方法，來標準化的 ATL 視窗物件的特徵。

- [CWinTraitsOR](../atl/reference/cwintraitsor-class.md)如視窗樣式，以及用來建立視窗的延伸的樣式會提供預設值。 這些值會加入，使用邏輯 OR 運算子，在視窗的建立期間提供的值。

## <a name="related-articles"></a>相關文章

[ATL 視窗類別](../atl/atl-window-classes.md)

[ATL 教學課程](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../atl/atl-class-overview.md)   
[訊息對應巨集](../atl/reference/message-map-macros-atl.md)   
[視窗類別巨集](../atl/reference/window-class-macros.md)

