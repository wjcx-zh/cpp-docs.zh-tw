---
title: 介面項目
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: 9cf38d3d469da181d15a10434525b3aca63969f0
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175895"
---
# <a name="interface-elements"></a>介面項目

本文說明 Visual Studio 2008 SP1 中導入的介面項目，並也會說明與程式庫的舊版本的差異。

下圖顯示使用新的介面項目所建置的應用程式。

![MFC 功能套件範例應用程式](../mfc/media/mfc_featurepack.png "MFC 功能套件範例應用程式")

## <a name="window-docking"></a>停駐視窗

視窗停駐的功能類似於 Visual Studio 圖形化使用者介面使用的停駐視窗。

## <a name="control-bars-are-now-panes"></a>控制列是現在 窗格

控制列現在稱為窗格，以及衍生自[CBasePane 類別](../mfc/reference/cbasepane-class.md)。 在舊版的 MFC，控制列的基底類別是`CControlBar`。

應用程式主框架視窗通常由[CFrameWndEx 類別](../mfc/reference/cframewndex-class.md)或[CMDIFrameWndEx 類別](../mfc/reference/cmdiframewndex-class.md)。 呼叫主框架*停駐網站*。 窗格可以是下列三種類型的父代： 停駐位置、 停駐列中或迷你框架視窗。

有兩種類型的窗格： 不可調整大小和可調整大小。 可調整大小的窗格中，工具列、 狀態列等可以使用分隔器或滑桿來調整大小。 可調整大小的窗格會形成 （一個窗格可以固定到另一個窗格中，建立它們之間的分隔器） 的容器。 不過，無法 （固定） 若要停駐列附加可調整大小的窗格。

如果您的應用程式使用不可調整大小的窗格中，衍生它們[CPane 類別](../mfc/reference/cpane-class.md)。  如果您的應用程式使用可調整大小的窗格中，衍生從[CDockablePane 類別](../mfc/reference/cdockablepane-class.md)

## <a name="dock-site"></a>停駐位置

停駐位置 （或主框架視窗） 擁有所有的窗格和應用程式中的迷你框架視窗。 停駐位置包含[CDockingManager](../mfc/reference/cdockingmanager-class.md)成員。 這個成員會維護一份所有屬於停駐位置的窗格。 被排序的清單，以便建立在外部邊緣停駐位置的窗格都位於清單的開頭。 時，架構會重繪停駐位置，它會循環查看這份清單，並調整每個窗格，即可包含停駐位置的目前週框矩形的配置。 您可以呼叫`AdjustDockingLayout`或`RecalcLayout`當調整停駐的配置，而架構會將重新導向此呼叫停駐的管理員。

## <a name="dock-bars"></a>停駐列

每個主框架視窗可以定位*停駐列*沿著其框線。 停駐列是屬於一個窗格[CDockSite 類別](../mfc/reference/cdocksite-class.md)。 停駐列可以接受物件衍生自[CPane](../mfc/reference/cpane-class.md)，例如工具列。 若要初始化主框架視窗時，請建立停駐列，呼叫`EnableDocking`。 若要啟用自動隱藏列，請呼叫`EnableAutoHideBars`。 `EnableAutoHideBars` 會建立[CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)物件，並將它們放置每個停駐列旁。

每個停駐列會分成停駐的資料列。 停駐的資料列都由[CDockingPanesRow 類別](../mfc/reference/cdockingpanesrow-class.md)。 每個停駐資料列都包含一份工具列。 如果使用者將工具列停駐，或將工具列從一個資料列移至另一個相同的停駐列中，架構會建立新的資料列，並據此，調整停駐列或工具列置於現有的資料列。

## <a name="mini-frame-windows"></a>迷你框架 Windows

浮動窗格位於迷你框架視窗。 迷你框架視窗由兩個類別： [CMDITabInfo 類別](../mfc/reference/cmditabinfo-class.md)（其中包含只有一個窗格） 和[CMultiPaneFrameWnd 類別](../mfc/reference/cmultipaneframewnd-class.md)（可以包含多個窗格）。 若要在程式碼中浮動窗格，呼叫[CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane)。 浮動窗格之後，架構會自動建立迷你框架視窗，而該迷你框架視窗變成浮動窗格的父代。 當停駐在浮動窗格時，架構會重設其父代，，而且浮動窗格會變成停駐列 （適用於工具列） 或 （適用於可調整大小的窗格） 與停駐位置。

## <a name="pane-dividers"></a>窗格分割線

窗格分割線 （也稱為滑桿或分隔器） 都由[CPaneDivider 類別](../mfc/reference/cpanedivider-class.md)。 當使用者將窗格停駐於時，framework 就會建立窗格分割線，不論是否窗格停駐在停駐位置，或在另一個窗格。 當窗格停駐於停駐位置時，會呼叫的窗格分割線*預設窗格分割線*。 預設的窗格分割線負責停駐位置中的所有停駐窗格的配置。 停駐的管理員會維護一份預設窗格分割線和窗格的清單。 停駐的管理員會負責所有停駐窗格的配置。

## <a name="containers"></a>容器

所有可調整大小的窗格，停駐於彼此時，會保留在容器中。 容器由[CPaneContainer 類別](../mfc/reference/cpanecontainer-class.md)。 每個容器的左邊和右邊的組件之間有其左邊的窗格，右窗格、 左子容器、 正確的子容器和分隔器的指標。 (*左*並*右*未參考實體的側邊，但而不是識別樹狀結構的分支。)以這種方式，我們可以建置窗格和分隔器的樹狀結構，並因此達成複雜的版面配置，可以一起調整大小的窗格。 `CPaneContainer`類別維護容器的樹狀結構; 它也會維護兩份清單的窗格和存在於此樹狀結構中的滑桿。 窗格容器管理員通常會內嵌至預設滑桿和執行多個窗格的迷你框架視窗中。

## <a name="auto-hide-control-bars"></a>自動隱藏控制列

根據預設，每個`CDockablePane`支援 「 自動隱藏 」 功能。 當使用者按一下 [釘選] 按鈕的標題`CDockablePane`，架構會切換窗格自動隱藏模式。 若要處理按一下，架構會建立[CMFCAutoHideBar 類別](../mfc/reference/cmfcautohidebar-class.md)並[CMFCAutoHideButton 類別](../mfc/reference/cmfcautohidebutton-class.md)相關聯`CMFCAutoHideBar`物件。 新的架構，對`CMFCAutoHideBar`上[CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)。 此架構也會將附加`CMFCAutoHideButton`至工具列。 [CDockingManager Class](../mfc/reference/cdockingmanager-class.md)維護`CDockablePane`。

## <a name="tabbed-control-bars-and-outlook-bars"></a>索引標籤式的控制列和 Outlook 橫條

[CMFCBaseTabCtrl 類別](../mfc/reference/cmfcbasetabctrl-class.md)實作具有可拆式索引標籤的索引標籤式視窗的基本功能。 若要使用`CMFCBaseTabCtrl`物件，初始化[CBaseTabbedPane 類別](../mfc/reference/cbasetabbedpane-class.md)應用程式中。 `CBaseTabbedPane` 衍生自`CDockablePane`會保留指標和`CMFCBaseTabCtrl`物件。 `CBaseTabbedPane`可讓使用者將停駐和調整索引標籤式的控制列的大小。 使用[cdockablepane:: Attachtotabwnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd)以動態方式建立停駐和索引標籤式控制列。

Outlook 功能區控制項也根據索引標籤式的橫條圖。 [CMFCOutlookBar 類別](../mfc/reference/cmfcoutlookbar-class.md)衍生自`CBaseTabbedPane`。 如需如何使用 Outlook 功能區的詳細資訊，請參閱[CMFCOutlookBar 類別](../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="see-also"></a>另請參閱

[概念](../mfc/mfc-concepts.md)

