---
title: 介面項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1906505e75273cc62a0eac55e6ed1a9686a3b76f
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078440"
---
# <a name="interface-elements"></a>介面項目
本文說明 Visual Studio 2008 SP1 中導入的介面項目，並也描述與程式庫的舊版本的差異。  
  
 下圖顯示所使用的新介面項目建立的應用程式。  
  
 ![MFC 功能套件範例應用程式](../mfc/media/mfc_featurepack.png "mfc_featurepack")  
  
## <a name="window-docking"></a>停駐視窗  
 視窗停駐的功能類似於視窗停駐的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]圖形化使用者介面使用。  
  
## <a name="control-bars-are-now-panes"></a>控制列是現在 窗格  
 控制列現在稱為窗格，以及衍生自[CBasePane 類別](../mfc/reference/cbasepane-class.md)。 在舊版的 MFC，控制列的基底類別是`CControlBar`。  
  
 應用程式主框架視窗通常由[CFrameWndEx 類別](../mfc/reference/cframewndex-class.md)或[CMDIFrameWndEx 類別](../mfc/reference/cmdiframewndex-class.md)。 主要畫面格稱為*停駐網站*。 窗格可以有三種類型的父代的其中一個： 停駐位置、 停駐列或迷你框架視窗。  
  
 有兩種類型的窗格： 不可調整大小和可調整大小。 可調整大小的窗格中，工具列、 狀態列等可以使用分隔器或滑桿調整大小。 可調整大小的窗格會形成 （一個窗格可以固定到另一個窗格中，建立它們之間的分隔器） 的容器。 不過，可調整大小的窗格物件不可附加 （固定） 若要停駐列。  
  
 如果您的應用程式使用非可調整大小的窗格中，衍生從[CPane 類別](../mfc/reference/cpane-class.md)。  如果您的應用程式使用可調整大小的窗格中，衍生從[CDockablePane 類別](../mfc/reference/cdockablepane-class.md)  
  
## <a name="dock-site"></a>停駐位置  
 停駐位置 （或主框架視窗） 擁有所有窗格和應用程式中的迷你框架視窗。 停駐位置包含[CDockingManager](../mfc/reference/cdockingmanager-class.md)成員。 這個成員會維護屬於停駐站台的所有窗格的清單。 被排序的清單，以便建立邊緣外部的停駐窗格位於清單的開頭。 架構會重繪停駐位置，它會循環查看這份清單，並調整每個窗格，即可包含目前週框的停駐的配置。 您可以呼叫`AdjustDockingLayout`或`RecalcLayout`時您必須調整停駐的配置，並架構將重新導向此呼叫停駐的管理員。  
  
## <a name="dock-bars"></a>停駐列  
 每個主框架視窗可以放置*停駐列*沿著其框線。 停駐列是屬於窗格[CDockSite 類別](../mfc/reference/cdocksite-class.md)。 停駐列可以接受衍生自物件[CPane](../mfc/reference/cpane-class.md)，例如工具列。 若要初始化主框架視窗時，請建立停駐列，呼叫`EnableDocking`。 若要啟用自動隱藏列，請呼叫`EnableAutoHideBars`。 `EnableAutoHideBars` 建立[CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)物件，並將它們置於每個停駐列旁。  
  
 每個停駐列會分成停駐的資料列。 停駐的資料列都由[CDockingPanesRow 類別](../mfc/reference/cdockingpanesrow-class.md)。 每個停駐資料列都包含一份工具列。 如果使用者將工具列停駐，或從一個資料列移動工具列，到另一個相同的停駐列內，架構會建立新的資料列，並相應地調整停駐列或工具列置於現有的資料列。  
  
## <a name="mini-frame-windows"></a>迷你框架視窗  
 浮動窗格位於迷你框架視窗。 迷你框架視窗由兩個類別： [CMDITabInfo 類別](../mfc/reference/cmditabinfo-class.md)（其中可以包含一個窗格） 和[CMultiPaneFrameWnd 類別](../mfc/reference/cmultipaneframewnd-class.md)（其中可以包含數個窗格）。 若要在程式碼中浮動窗格，呼叫[CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane)。 浮動窗格之後，架構會自動建立迷你框架視窗，而且該迷你框架視窗變成浮動窗格的父系。 當停駐浮動窗格時，架構會重設其父代，而且浮動窗格會變成停駐列 （適用於工具列） 或 （適用於可調整大小的窗格） 與停駐位置。  
  
## <a name="pane-dividers"></a>窗格分割線  
 窗格分割線 （也稱為滑桿或分隔器） 都由[CPaneDivider 類別](../mfc/reference/cpanedivider-class.md)。 當使用者停駐窗格時，架構會建立窗格分割線，不論是否窗格停駐於停駐或另一個窗格。 當窗格停駐於停駐位置時，就會呼叫的窗格分割線*預設窗格分割線*。 預設的窗格分割線會負責配置的固定位置中的所有停駐窗格。 停駐管理員會維護一份預設窗格分割線，以及窗格的清單。 停駐的管理員會負責配置的所有停駐窗格。  
  
## <a name="containers"></a>容器  
 所有可調整大小窗格停駐於彼此時，會維護在容器中。 容器由[CPaneContainer 類別](../mfc/reference/cpanecontainer-class.md)。 每個容器的左邊和右邊的組件之間有其左的窗格，右窗格、 左子容器、 正確的子容器和分隔器的指標。 (*左*和*右*並未參考實體的側邊，但是而找出樹狀結構的分支。)以這種方式，我們可以建置窗格和分隔器的樹狀結構，並因此達成複雜的配置，可以一起調整大小的窗格。 `CPaneContainer`類別會維護容器的樹狀目錄，則也會維護兩個窗格和位於此樹狀結構中的滑桿清單。 窗格容器經理通常會內嵌至預設滑桿和執行多個窗格的迷你框架視窗。  
  
## <a name="auto-hide-control-bars"></a>自動隱藏控制列  
 根據預設，每個`CDockablePane`支援自動隱藏功能。 當使用者按一下 [固定] 按鈕上的標題`CDockablePane`，架構將窗格切換到自動隱藏模式。 若要處理按一下，架構會建立[CMFCAutoHideBar 類別](../mfc/reference/cmfcautohidebar-class.md)和[CMFCAutoHideButton 類別](../mfc/reference/cmfcautohidebutton-class.md)聯`CMFCAutoHideBar`物件。 架構對新`CMFCAutoHideBar`上[CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)。 架構也會將附加`CMFCAutoHideButton`至工具列。 [CDockingManager 類別](../mfc/reference/cdockingmanager-class.md)維護`CDockablePane`。  
  
## <a name="tabbed-control-bars-and-outlook-bars"></a>索引標籤式的控制列和 Outlook 列  
 [CMFCBaseTabCtrl 類別](../mfc/reference/cmfcbasetabctrl-class.md)實作具有可拆式索引標籤索引標籤式視窗的基本功能。 若要使用`CMFCBaseTabCtrl`物件，初始化[CBaseTabbedPane 類別](../mfc/reference/cbasetabbedpane-class.md)應用程式中。 `CBaseTabbedPane` 衍生自`CDockablePane`及維護的指標`CMFCBaseTabCtrl`物件。 `CBaseTabbedPane`可讓使用者將停駐和調整大小的索引標籤式的控制列。 使用[cdockablepane:: Attachtotabwnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd)以動態方式建立停駐和索引標籤式控制列。  
  
 Outlook 狀態列控制項也根據索引標籤式的橫條。 [CMFCOutlookBar 類別](../mfc/reference/cmfcoutlookbar-class.md)衍生自`CBaseTabbedPane`。 如需如何使用 outlook 功能區的詳細資訊，請參閱[CMFCOutlookBar 類別](../mfc/reference/cmfcoutlookbar-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../mfc/mfc-concepts.md)

