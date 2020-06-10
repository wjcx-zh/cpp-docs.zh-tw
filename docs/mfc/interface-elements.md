---
title: 介面項目
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: 4d4d81287cb30a7d3608025085cdb3f9a208147a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619984"
---
# <a name="interface-elements"></a>介面項目

本檔說明 Visual Studio 2008 SP1 中引進的介面元素，同時描述與舊版程式庫的差異。

下圖顯示使用新介面元素建立的應用程式。

![MFC 功能套件範例應用程式](../mfc/media/mfc_featurepack.png "MFC 功能套件範例應用程式")

## <a name="window-docking"></a>視窗停駐

視窗停駐功能類似 Visual Studio 圖形化使用者介面所使用的視窗銜接。

## <a name="control-bars-are-now-panes"></a>控制列現在是窗格

控制列現在稱為窗格，衍生自[CBasePane 類別](reference/cbasepane-class.md)。 在較早版本的 MFC 中，控制列的基類是 `CControlBar` 。

應用程式主框架視窗通常以[CFrameWndEx 類別](reference/cframewndex-class.md)或[CMDIFrameWndEx 類別](reference/cmdiframewndex-class.md)表示。 主框架稱為「停*駐網站*」。 窗格可以有三種父系類型的其中一種：停駐網站、停駐線或迷你框架視窗。

窗格有兩種類型：無法調整大小和大小。 可調整大小的窗格（例如狀態列和工具列）可以使用 [分隔器] 或 [滑杆] 調整大小。 可調整大小的窗格可以形成容器（一個窗格可以停駐到另一個窗格，並在它們之間建立分隔器）。 不過，可調整大小的窗格無法附加（停駐）以停駐橫條。

如果您的應用程式使用不能調整大小的窗格，請從[CPane 類別](reference/cpane-class.md)衍生它們。  如果您的應用程式使用可調整大小的窗格，請從[CDockablePane 類別](reference/cdockablepane-class.md)衍生它們

## <a name="dock-site"></a>停駐網站

停駐網站（或主框架視窗）擁有應用程式中的所有窗格和迷你框架視窗。 Dock 網站包含[CDockingManager](reference/cdockingmanager-class.md)成員。 此成員會維護屬於 dock 網站的所有窗格清單。 清單會進行排序，以便在停駐網站的外部邊緣建立的窗格位於清單的開頭。 當架構重繪停駐網站時，它會迴圈處理此清單，並調整每個窗格的配置，以包含 dock 網站的目前周框。 `AdjustDockingLayout` `RecalcLayout` 當您必須調整停駐配置，而且架構將此呼叫重新導向至停駐管理員時，您可以呼叫或。

## <a name="dock-bars"></a>停駐橫條圖

每個主框架視窗可以沿著其框線放置停*駐線*。 停駐橫條是屬於[CDockSite 類別](reference/cdocksite-class.md)的窗格。 停駐線可以接受衍生自[CPane](reference/cpane-class.md)的物件，例如工具列。 若要在主框架視窗初始化時建立停駐線，請呼叫 `EnableDocking` 。 若要啟用自動隱藏列，請呼叫 `EnableAutoHideBars` 。 `EnableAutoHideBars`建立[CAutoHideDockSite](reference/cautohidedocksite-class.md)物件，並將它們放置在每個 dock 橫條的旁邊。

每個 dock 橫條都會分割成固定資料列。 固定資料列會以[CDockingPanesRow 類別](reference/cdockingpanesrow-class.md)表示。 每個 dock 資料列都包含一份工具列清單。 如果使用者在相同的 dock 列中停駐工具列，或將工具列從一個資料列移到另一個，則架構會建立新的資料列，並據以調整停駐線的大小，或將工具列置於現有的資料列上。

## <a name="mini-frame-windows"></a>迷你框架視窗

浮動窗格位於迷你框架視窗中。 迷你框架視窗是由兩個類別所代表： [CMDITabInfo 類別](reference/cmditabinfo-class.md)（只能包含一個窗格）和[CMultiPaneFrameWnd 類別](reference/cmultipaneframewnd-class.md)（可以包含數個窗格）。 若要在程式碼中浮動窗格，請呼叫[CBasePane：： FloatPane](reference/cbasepane-class.md#floatpane)。 在窗格浮動之後，架構會自動建立一個迷你框架視窗，而該迷你框架視窗會變成浮動窗格的父系。 當浮動窗格銜接時，架構會重設其父系，而浮動窗格會變成停駐列（適用于工具列）或停駐網站（適用于可調整大小的窗格）。

## <a name="pane-dividers"></a>窗格分隔線

窗格分隔線（也稱為滑杆或分隔器）是由[CPaneDivider 類別](reference/cpanedivider-class.md)表示。 當使用者停駐窗格時，架構會建立窗格分隔線，而不論窗格是否停駐在 dock 網站或另一個窗格。 當窗格停駐到 dock 網站時，窗格分割就稱為*預設窗格分割線*。 預設窗格分割線會負責停駐網站中所有銜接窗格的版面配置。 [Dock 管理員] 會維護預設窗格分隔清單和窗格清單。 停駐管理員負責所有銜接窗格的版面配置。

## <a name="containers"></a>容器

所有可調整大小的窗格在停駐時，都會保留在容器中。 容器是由[CPaneContainer 類別](reference/cpanecontainer-class.md)表示。 每個容器都有指向其左窗格、右窗格、左子容器、右子容器，以及左和右部分之間分隔器的指標。 （*Left*和*right*不會參考實體邊，而是識別樹狀結構的分支）。如此一來，我們就可以建立窗格和分隔器的樹狀結構，因而達到可在一起調整大小的窗格的複雜版面配置。 `CPaneContainer`類別會維護容器的樹狀結構，也會維護位於此樹狀結構中的兩個窗格和滑杆清單。 窗格容器管理員通常會內嵌到包含多個窗格的預設滑杆和迷你框架視窗中。

## <a name="auto-hide-control-bars"></a>自動隱藏控制列

根據預設，每個都 `CDockablePane` 支援自動隱藏功能。 當使用者按一下標題上的 [釘選] 按鈕時 `CDockablePane` ，架構會將窗格切換為自動隱藏模式。 為了處理點擊，架構會建立一個[CMFCAutoHideBar 類別](reference/cmfcautohidebar-class.md)，以及與該物件相關聯的[CMFCAutoHideButton 類別](reference/cmfcautohidebutton-class.md) `CMFCAutoHideBar` 。 架構會將新的放 `CMFCAutoHideBar` 在[CAutoHideDockSite](reference/cautohidedocksite-class.md)上。 架構也會將附加 `CMFCAutoHideButton` 至工具列。 [CDockingManager 類別](reference/cdockingmanager-class.md)會維護 `CDockablePane` 。

## <a name="tabbed-control-bars-and-outlook-bars"></a>索引標籤式控制列和 Outlook 橫條圖

[CMFCBaseTabCtrl 類別](reference/cmfcbasetabctrl-class.md)會使用可卸離的索引標籤，來執行索引標籤式視窗的基本功能。 若要使用 `CMFCBaseTabCtrl` 物件，請在您的應用程式中初始化[CBaseTabbedPane 類別](reference/cbasetabbedpane-class.md)。 `CBaseTabbedPane`衍生自 `CDockablePane` ，並維護物件的指標 `CMFCBaseTabCtrl` 。 `CBaseTabbedPane`可讓使用者停駐和調整索引標籤式控制列。 使用[CDockablePane：： AttachToTabWnd](reference/cdockablepane-class.md#attachtotabwnd)以動態方式建立停駐和索引標籤式的控制列。

Outlook bar 控制項也是以索引標籤式列為基礎。 [CMFCOutlookBar 類別](reference/cmfcoutlookbar-class.md)衍生自 `CBaseTabbedPane` 。 如需如何使用 Outlook bar 的詳細資訊，請參閱[CMFCOutlookBar 類別](reference/cmfcoutlookbar-class.md)。

## <a name="see-also"></a>另請參閱

[概念](mfc-concepts.md)
