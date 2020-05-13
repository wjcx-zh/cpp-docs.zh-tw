---
title: 工具列基本概念
ms.date: 11/04/2016
f1_keywords:
- RT_TOOLBAR
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
ms.openlocfilehash: d4e8793337beb2eed533fe04daf549ec21efc61d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373471"
---
# <a name="toolbar-fundamentals"></a>工具列基本概念

本文介紹了通過選擇應用程式嚮導中的選項向應用程式添加預設工具列的基本 MFC 實現。 涵蓋的主題包括：

- [應用程式精靈工具列選項](#_core_the_appwizard_toolbar_option)

- [程式碼中的工具列](#_core_the_toolbar_in_code)

- [編輯工具列資源](#_core_editing_the_toolbar_resource)

- [多個工具列](#_core_multiple_toolbars)

## <a name="the-application-wizard-toolbar-option"></a><a name="_core_the_appwizard_toolbar_option"></a>應用程式精靈工具列選項

要獲取帶有預設按鈕的單個工具列,請在標記為「使用者介面功能」的頁面上選擇「標準停靠」工具列選項。 這會向應用程式新增程式碼:

- 創建工具列物件。

- 管理工具列,包括其停靠或浮動的能力。

## <a name="the-toolbar-in-code"></a><a name="_core_the_toolbar_in_code"></a>程式碼中的工具列

工具列是[CToolBar](../mfc/reference/ctoolbar-class.md)物件,聲明`CMainFrame`為應用程式 類的數據成員。 換句話說,工具列物件嵌入在主框架視窗物件中。 這意味著 MFC 在建立框架視窗時創建工具列,並在破壞框架視窗時銷毀工具列。 以下部分類聲明(對於多個文檔介面 (MDI) 應用程式)顯示嵌入工具列和嵌入狀態列的數據成員。 它還顯示成員函數的`OnCreate`重寫。

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

工具列建立發生在中`CMainFrame::OnCreate`。 MFC 在為框架創建視窗后,但在其變為可見之前調用[OnCreate。](../mfc/reference/cwnd-class.md#oncreate) 應用程式精靈`OnCreate`產生的預設值執行以下工具列工作:

1. 呼叫`CToolBar`物件的[「創建](../mfc/reference/ctoolbar-class.md#create)成員」函數以創建基礎[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件。

1. 調用[LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)以載入工具列資源資訊。

1. 調用函數以啟用停靠、浮動和工具提示。 有關這些調用的詳細資訊,請參閱文章[「停靠」和「浮動工具列](../mfc/docking-and-floating-toolbars.md)」。

> [!NOTE]
> MFC 一般示例[DOCKTOOL](../overview/visual-cpp-samples.md)包括新舊 MFC 工具列的插圖。 使用`COldToolbar`工具列需要步驟 2 的`LoadBitmap`呼叫`LoadToolBar`(`SetButtons`而不是 ) 與呼叫 。 新的工具列需要呼叫`LoadToolBar`。

停靠、浮動和工具提示調用是可選的。 `OnCreate`如果您願意,可以從中刪除這些行。 結果是工具列保持固定、無法浮動或重新停靠以及無法顯示工具提示。

## <a name="editing-the-toolbar-resource"></a><a name="_core_editing_the_toolbar_resource"></a>編輯工具列資源

使用應用程式精靈獲取的預設工具列基於 mFC 版本 4.0 中介紹**的RT_TOOLBAR**自訂資源。 您可以使用[工具列編輯器](../windows/toolbar-editor.md)編輯此資源。 編輯器可讓您輕鬆添加、刪除和重新排列按鈕。 它包含與 Visual C++ 中的一般圖形編輯器非常相似的按鈕的圖形編輯器。 如果您在早期版本的 Visual C++ 中編輯了工具列,則現在將發現該任務要容易得多。

要將工具列按鈕連線到指令,請為此按鈕提供命令 ID,`ID_MYCOMMAND`如 。 在工具列編輯器中指定按鈕的屬性頁中的命令 ID。 然後為命令創建處理程式函數(有關詳細資訊,請參閱[將消息映射到函數](../mfc/reference/mapping-messages-to-functions.md))。

新的[CToolBar](../mfc/reference/ctoolbar-class.md)成員函數使用**RT_TOOLBAR**資源。 [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar)現在取代[LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap)來載入工具列按鈕影像的點陣圖,[然後設定 Button](../mfc/reference/ctoolbar-class.md#setbuttons)來設置按鈕樣式,並連接帶有點陣圖圖像的按鈕。

有關使用工具列編輯器的詳細資訊,請參考[工具列編輯器](../windows/toolbar-editor.md)。

## <a name="multiple-toolbars"></a><a name="_core_multiple_toolbars"></a>多個工具列

應用程式精靈為您提供一個預設工具列。 如果應用程式中需要多個工具列,則可以根據預設工具列的嚮導生成的代碼為其他工具列建模代碼。

如果要將工具列顯示為命令的結果,則需要:

- 使用工具列編輯器創建新工具列資源,然後`OnCreate`使用[LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar)成員函數載入它。

- 在主框架視窗類中嵌入新的[CToolBar](../mfc/reference/ctoolbar-class.md)物件。

- 進行適當的函數調用以`OnCreate`停靠或浮動工具列、設置其樣式等。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [MFC 工具列實現(工具列概述資訊)](../mfc/mfc-toolbar-implementation.md)

- [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)

- [工具列工具提示](../mfc/toolbar-tool-tips.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別

- [使用工具列控制項](../mfc/working-with-the-toolbar-control.md)

- [使用舊工具列](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>另請參閱

[MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)
