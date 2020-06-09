---
title: 控制列
ms.date: 11/04/2016
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
ms.openlocfilehash: a2d3683b744493bb5566456b9e1358c1ddc418d4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615969"
---
# <a name="control-bars"></a>控制列

「控制列」是工具列、狀態列和對話方塊列的一般名稱。 MFC 類別 `CToolBar` 、 `CStatusBar` 、 `CDialogBar` 、 `COleResizeBar` 和 `CReBar` 衍生自類別[CControlBar](reference/ccontrolbar-class.md)，它會實作為其通用功能。

控制列是一些顯示控制項列的視窗，使用者可以選取這些選項、執行命令，或者取得程式資訊。 控制列的類型包括工具列、對話方塊列和狀態列。

- 類別[CToolBar](reference/ctoolbar-class.md)中的工具列

- 狀態列，位於 [類別] [CStatusBar](reference/cstatusbar-class.md)

- 對話方塊列，在 [類別[CDialogBar](reference/cdialogbar-class.md) ] 中

- Rebar，在類別[CReBar](reference/crebar-class.md)中

> [!IMPORTANT]
> 從 MFC 版本4.0、工具列、狀態列和工具提示，都是使用*comctl32.dll*中所實的系統功能來執行，而不是 mfc 特有的先前執行。 在 MFC 版本6.0 中， `CReBar` 已新增也會包裝 comctl32.dll 的功能。

以下簡要介紹控制列的類型。 如需詳細資訊，請參閱下列連結。

## <a name="control-bars"></a>控制列

控制列藉由提供快速的單一步驟命令動作，大幅提高程式的可用性。 `CControlBar` 類別提供所有工具列、狀態列和對話方塊列的一般功能。 `CControlBar` 提供在其父框架視窗中放置控制列的功能。 由於控制列通常是父框架視窗的子視窗，因此與框架視窗的工作區檢視或 MDI 工作區屬於「同層級」。 控制列物件會使用父視窗工作區矩形的相關資訊來決定本身的位置。 然後它會修改父視窗的其他工作區視窗矩形，讓工作區檢視或 MDI 工作區視窗填滿工作區視窗的其餘部分。

> [!NOTE]
> 如果控制列上的按鈕沒有**命令**或**UPDATE_COMMAND_UI**處理常式，則架構會自動停用該按鈕。

## <a name="toolbars"></a>工具列

工具列是一種控制列，會顯示執行命令的點陣圖按鈕。 按下工具列按鈕相當於選擇功能表項目，如果該功能表項目的識別碼與工具列按鈕相同，則會呼叫對應至功能表項目的相同處理常式。 您可以將按鈕設定為顯示且運作為按鈕、選項按鈕或核取方塊。 工具列通常會對齊框架視窗的頂端，不過，MFC 工具列可以「停駐」至其父視窗的任何一側，或在自己的迷你框架視窗中浮動顯示。 工具列也可以「浮動」顯示，您也可以使用滑鼠變更其大小及拖曳它。 當使用者將滑鼠移至工具列按鈕的上方時，工具列也會顯示工具提示。 工具提示是一個小型的快顯視窗，用於簡短描述按鈕的用途。

> [!NOTE]
> 從 MFC 4.0 版，類別[CToolBar](reference/ctoolbar-class.md)會使用 Windows 工具列通用控制項。 `CToolBar`包含[CToolBarCtrl](reference/ctoolbarctrl-class.md)。 不過仍支援舊版的工具列。 請參閱[工具列](mfc-toolbar-implementation.md)文章。

## <a name="status-bars"></a>狀態列

狀態列是一種控制列，其中包含文字輸出窗格或「指示器」。 輸出窗格通常用來做為訊息列和狀態指示器。 訊息列的範例包括簡要說明所選取之功能表的說明訊息行，或由 [MFC 應用程式精靈] 所建立之預設狀態列最左邊窗格中的工具列命令。 狀態指示器的範例包括 SCROLL LOCK、NUM LOCK 和其他按鍵。 狀態列通常會對齊框架視窗的底部。 請參閱類別[CStatusBar](reference/cstatusbar-class.md)和類別[CStatusBarCtrl](reference/cstatusbarctrl-class.md)。

## <a name="dialog-bars"></a>對話方塊列

對話方塊列是一種控制列，以對話方塊範本資源為基礎，具有非強制回應對話方塊的功能。 對話方塊列可包含視窗、自訂或 ActiveX 控制項。 和對話方塊一樣，使用者可以在控制項中使用定位點。 對話方塊列可對齊於框架視窗的頂端、底端，或是右側，也可以在自己的框架視窗中浮動顯示。 請參閱類別[CDialogBar](reference/cdialogbar-class.md)。

## <a name="rebars"></a>Rebar

[Rebar](using-crebarctrl.md)是一種控制列，可提供 Rebar 控制項的停駐、版面配置、狀態和持續性資訊。 Rebar 物件可以包含各種子視窗 (通常是其他控制項)，包括編輯方塊、工具列和清單方塊。 Rebar 物件可以在指定的點陣圖上顯示其子視窗。 按一下或拖曳它的移駐夾列即可自動或手動調整其大小。 請參閱類別[CReBar](reference/crebar-class.md)。

## <a name="see-also"></a>另請參閱

[使用者介面元素](user-interface-elements-mfc.md)
