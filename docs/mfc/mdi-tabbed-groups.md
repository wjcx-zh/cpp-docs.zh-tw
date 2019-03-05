---
title: MDI 索引標籤式群組
ms.date: 11/04/2016
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
ms.openlocfilehash: 6b68d1bc06a6827ca94b05fa2760206f424d40fe
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289516"
---
# <a name="mdi-tabbed-groups"></a>MDI 索引標籤式群組

多個文件介面 (MDI) 索引標籤式的群組功能可讓多個文件介面 (MDI) 應用程式，以顯示一或多個索引標籤式的視窗 (或群組的索引標籤式視窗，稱為*索引標籤式群組*) 在 MDI 工作區中。 索引視窗可以垂直或水平對齊。 如果應用程式裝載多個 MDI 索引群組，則群組會以分隔器分隔。

## <a name="features"></a>功能

以下是 MDI 索引群組的功能：

- 應用程式可以動態建立索引視窗。

- 應用程式可以水平或垂直對齊索引視窗。

- 索引視窗會以分隔器分隔。 使用者可以使用分隔器調整索引群組的大小。

- 使用者可以在群組間拖曳個別索引標籤。

- 使用者可以拖曳個別索引標籤以建立新群組。

- 使用者可以使用捷徑功能表移動索引標籤或者建立新群組。

- 應用程式可以儲存和載入索引視窗的配置。

- 應用程式可以儲存和載入 MDI 文件清單。

- 應用程式可以存取個別的索引群組以及修改其參數。

### <a name="using-mdi-tabbed-groups"></a>使用 MDI 索引群組

以下是經常以 MDI 索引群組執行的工作：

- 若要啟用的主框架視窗的 MDI 索引群組，請呼叫[cmdiframewndex:: Enablemditabbedgroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups)。 此方法的第二個參數是 `CMDITabInfo` 類別的執行個體。 在呼叫 `CMDIFrameWndEx::EnableMDITabbedGroups`之前，您可以使用預設參數或加以修改。

- 若要在執行時間修改 MDI 索引群組的屬性，請建立或修改 `CMDITabInfo` 物件並再次呼叫 `CMDIFrameWndEx::EnableMDITabbedGroups`。

- 若要取得 MDI 索引視窗清單，請呼叫 `CMDIFrameWndEx::GetMDITabGroups`。

- 若要在現用的索引群組旁邊建立新的 MDI 索引群組，請呼叫 `CMDIFrameWndEx::MDITabNewGroup`。

- 若要將輸入焦點移位至索引群組的上一個或下一個視窗，請呼叫 `CMDIFrameWndEx::MDITabMoveToNextGroup`。

- 若要判斷視窗是否為 MDI 索引群組的成員，請呼叫 `CMDIFrameWndEx::IsMemberOfMDITabGroup`。

- 若要判斷是否已針對主框架視窗啟用 MDI 索引標籤或 MDI 索引群組，請呼叫 `CMDIFrameWndEx::AreMDITabs`。 若僅要判斷 MDI 索引式群組成員是否已啟用，請呼叫 `CMDIFrameWndEx::IsMDITabbedGroup`。

- 若要在使用者按一下索引標籤或將其拖曳至另一個 MDI 索引群組時顯示捷徑功能表，請覆寫 `CMDIFrameWndEx::OnShowMDITabContextMenu` 衍生類別中的 `CMDIFrameWndEx`。 如果您沒有實行此方法，則應用程式不會顯示捷徑功能表。

- 若要儲存應用程式中 MDI 索引群組的配置，請呼叫 `CMDIFrameWndEx::SaveMDIState`。 若要載入先前儲存的 MDI 索引群組設定檔，請呼叫 `CMDIFrameWndEx::LoadMDIState`。 您可以呼叫這些方法以載入或儲存 MDI 應用程式中開啟的文件清單。 如需有關儲存和載入 MDI 狀態的詳細資訊，請參閱 < [cmdiframewndex:: Loadmdistate](../mfc/reference/cmdiframewndex-class.md#loadmdistate)。

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)<br/>
[CMDIFrameWndEx 類別](../mfc/reference/cmdiframewndex-class.md)<br/>
[CMDIChildWndEx 類別](../mfc/reference/cmdichildwndex-class.md)<br/>
[CMDITabInfo 類別](../mfc/reference/cmditabinfo-class.md)
