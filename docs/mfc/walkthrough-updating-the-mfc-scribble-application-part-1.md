---
title: 逐步解說：更新 MFC Scribble 應用程式 (第 1 部分)
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 18803d2222c80b80ac2b1fde75b442ea1e9a89bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360251"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>逐步解說：更新 MFC Scribble 應用程式 (第 1 部分)

本演練演示如何修改現有 MFC 應用程式以使用功能區用戶介面。 Visual Studio 同時支援 Office 2007 功能區和 Windows 7 風景功能區。 有關功能區使用者介面的詳細資訊,請參閱[功能區](/windows/win32/uxguide/cmd-ribbons)。

本演練修改經典 Scribble 1.0 MFC 範例,該示例允許您使用滑鼠創建線條圖。 演練的這一部分演示如何修改 Scribble 範例,以便顯示功能區列。 [第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)向功能區列添加更多按鈕。

## <a name="prerequisites"></a>Prerequisites

[塗鴉 1.0 MFC 樣品](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe)。 有關轉換為 Visual Studio 2017 或更高版本的説明,請參閱[移植指南:MFC 塗鴉](../porting/porting-guide-mfc-scribble.md)。

## <a name="sections"></a><a name="top"></a>部分

本演練的這一部分有以下部分:

- [取代基本類別](#replaceclass)

- [新增點圖](#addbitmap)

- [新增專案加入功能區資源](#addribbon)

- [建立功能區列的實體](#createinstance)

- [新增類別](#addcategory)

- [設定應用程式的外觀](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a>取代基本類別

要將支援功能表的應用程式轉換為支援功能區的應用程式,必須從更新的基類派生應用程式、框架視窗和工具列類。 (我們建議您不要修改原始塗鴉示例。 相反,請清理 Scribble 專案,將其複製到其他目錄,然後修改副本。

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>取代 Scribble 應用程式中的基類別

1. 在塗鴉.cpp 中,驗證`CScribbleApp::InitInstance`其中包括 對[AfxOleInit 的](../mfc/reference/ole-initialization.md#afxoleinit)呼叫。

1. 將以下代碼加入*pch.h*檔(Visual Studio 2017 和更早版本中的*stdafx.h):*

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. 在 scribble.h 中`CScribbleApp`,修改類的定義,以便從[CWinAppEx 類](../mfc/reference/cwinappex-class.md)派生。

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. 當 Windows 應用程式使用初始化 (.ini) 檔案儲存使用者首選項數據時,編寫了 Scribble 1.0。 修改 Scribble 以在註冊表中儲存使用者首選項,而不是初始化檔。 要設置註冊表項和庫,請鍵入`CScribbleApp::InitInstance``LoadStdProfileSettings()`語句之後的以下代碼。

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. 多個文件介面 (MDI) 應用程式的主框架不再`CMDIFrameWnd`從類 派生。 相反,它派生自[CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)類。

    在 mainfrm.h 與 mainfrm.cpp 檔`CMDIFrameWnd`中`CMDIFrameWndEx`,將所有參考取代為 。

1. 在子frm.h和子frm.cpp檔案中,取代為`CMDIChildWnd``CMDIChildWndEx`。

    在孩子裡 h 檔`CSplitterWnd`,`CSplitterWndEx`取代為 。

1. 修改工具列和狀態列以使用新的 MFC 類。

    在 mainfrm.h 檔中:

    1. 將 `CToolBar` 取代為 `CMFCToolBar`。

    1. 將 `CStatusBar` 取代為 `CMFCStatusBar`。

1. 在 mainfrm.cpp 檔中:

    1. 將 `m_wndToolBar.SetBarStyle` 取代為 `m_wndToolBar.SetPaneStyle`

    1. 將 `m_wndToolBar.GetBarStyle` 取代為 `m_wndToolBar.GetPaneStyle`

    1. 將 `DockControlBar(&m_wndToolBar)` 取代為 `DockPane(&m_wndToolBar)`

1. 在 ipframe.cpp 檔中,註釋出以下三行代碼。

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. 保存更改,然後生成並運行應用程式。

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a>新增點圖

本演練的後續四個步驟需要位圖資源。 您可以通過多種方式取得適當的點陣圖:

- 使用[資源編輯器](../windows/resource-editors.md)發明您自己的點陣圖。 或者使用資源編輯器從 Visual Studio 中包含的便攜式網路圖形 (.png) 圖像中組裝位圖,並且可以從[Visual Studio 圖像庫](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library)下載。

    但是,**功能區**用戶介面要求某些位圖支援透明圖像。 透明點陣圖使用 32 位元圖,其中 24 位元指定顏色的紅色、綠色和藍色分量,8 位元定義指定顏色透明度的*Alpha 通道*。 當前資源編輯器可以查看,但不能修改具有 32 位圖元的位圖。 因此,使用外部圖像編輯器而不是資源編輯器來操作透明的位圖。

- 將適當的資源檔從其他應用程式複製到專案,然後從該文件導入位圖。

這個演練從演練中建立的範例複製資源檔[:使用 MFC 建立功能區應用程式](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)。

### <a name="to-add-bitmaps-to-the-project"></a>新增點圖

1. 使用檔案資源管理員將以下 .bmp 檔案從功能區範例`res`的資源 目錄 () 複製`res`到 Scribble 專案的資源目錄 ( ):

   1. 將 main.bmp 複製到您的塗鴉專案。

   1. 將檔案 small.bmp 和 filelarge.bmp 複製到您的塗鴉專案。

   1. 製作 filelarge.bmp 和 filesmall.bmp 檔的新副本,但將副本保存在功能區示例中。 重新命名副本 homesmall.bmp 和 homelarge.bmp,然後將副本移至您的 Scribble 專案。

   1. 製作工具列.bmp 檔案的副本,但將副本保存在功能區示例中。 重新命名複製面板.bmp,然後將副本移至 Scribble 專案。

1. 導入 MFC 應用程式的點陣圖。 在 **「資源檢視**」中,按兩下**scribble.rc**節點,按兩下**位圖**節點,然後按下「**添加資源**」。 在顯示的對話框中,按一下「**導入**」。。 瀏覽`res`到 目錄,選擇主.bmp 檔案,然後按下「**打開**」 。

   main.bmp 位圖包含 26x26 圖像。 將點陣圖的 ID`IDB_RIBBON_MAIN`變更為 。

1. 匯入附加到**應用程式**按鈕的檔案功能表的點陣圖。

   1. 導入檔案 small.bmp 檔,該檔包含 11 個 16x16 (16x176) 圖像。 將點陣圖的 ID`IDB_RIBBON_FILESMALL`變更為 。

   > [!NOTE]
   > 由於我們只需要前八張 16x16 圖像 (16x128),因此您可以選擇將此位圖的右側寬度從 176 裁剪到 128。

   1. 匯入包含九張 32x32 (32x288) 圖像的檔 large.bmp。 將點陣圖的 ID`IDB_RIBBON_FILELARGE`變更為 。

1. 導入功能區類別和面板的點陣圖。 功能區列上的每個選項卡都是一個類別,由文本標籤和可選圖像組成。

   1. 導入 homesmall.bmp 位圖,其中包含 11 個 16x16 圖像,用於小按鈕位圖。 將點陣圖的 ID`IDB_RIBBON_HOMESMALL`變更為 。

   1. 導入 homelarge.bmp 位圖,其中包含 9 個用於大型按鈕位圖的 32x32 圖像。 將點陣圖的 ID`IDB_RIBBON_HOMELARGE`變更為 。

1. 導入調整大小的功能區面板的位圖。 如果功能區太小而無法顯示整個面板,則這些位圖或面板圖示在調整大小操作后使用。

   1. 匯入包含八張 16x16 圖像的面板圖示.bmp 位圖。 在**點陣編輯器****的屬性視窗中,** 將位圖的寬度調整到 64 (16x64)。 將點陣圖的 ID`IDB_PANEL_ICONS`變更為 。

   > [!NOTE]
   > 由於我們只需要前四個 16x16 圖像 (16x64),您可以選擇將此位圖的右側寬度從 128 裁剪到 64。

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a>新增專案加入功能區資源

將使用功能表的應用程式轉換為使用功能區的應用程式時,不必刪除或禁用現有功能表。 只需創建功能區資源,添加功能區按鈕,然後將新按鈕與現有功能表項相關聯。 儘管功能表不再可見,但功能區欄中的消息通過功能表路由,功能表快捷方式繼續工作。

功能區由 **「應用程式**」按鈕(功能區左上角的大按鈕)和一個或多個類別選項卡組成。 每個類別選項卡包含一個或多個面板,這些面板充當功能區按鈕和控制項的容器。 以下過程演示如何創建功能區資源,然後自定義**應用程式**按鈕。

### <a name="to-add-a-ribbon-resource-to-the-project"></a>新增專案加入功能區資源

1. 在 **「解決方案資源管理器**」 選擇了「塗鴉」**專案**,按下「**新增資源**」

1. 在「**新增資源」** 對話方塊中,選擇 **「功能區**」,然後按下「**新建**」。

   Visual Studio 創建功能區資源並在設計視圖中打開它。 功能區資源識別`IDR_RIBBON1`碼是 ,顯示在**資源檢視中**。 功能區包含一個類別和一個面板。

1. 您可以通過修改**應用程式**屬性來自定義應用程式按鈕。 在此代碼中使用的消息 ID 已在 Scribble 1.0 的功能表中定義。

1. 在設計檢視中,按下 **「應用程式**」按鈕以顯示其屬性。 按下以下的屬性值**Image**:`IDB_RIBBON_MAIN`影像**Prompt**到`File`,`f`提示到`IDB_RIBBON_FILELARGE`,**鍵**到`IDB_RIBBON_FILESMALL`,**大影像**到,**將小圖像**變更為 。

1. 以下修改將創建使用者按下「**應用程式**」按鈕時顯示的功能表。 點選**此項目**旁邊的省略號 (**...)** 以開啟**項目編輯器**。

   1. 選取「**項目**類型 **」 按鈕**後,按下「**添加」** 來新增按鈕。 將**標題**變更`&New`為 **,ID**`ID_FILE_NEW`變更為`0``0`,**影像**變更為 **,影像大**變更為 。

   1. 按下「**新增**」 以新增按鈕。 將**標題**更改`&Save`為 **,ID**`ID_FILE_SAVE`更改為`2`,`2`**將圖像**更改為 ,將 **"圖像"更改為 "圖像"**

   1. 按下「**新增**」 以新增按鈕。 將**標題**更改`Save &As`為 **,ID**`ID_FILE_SAVE_AS`更改為`3`,`3`**將圖像**更改為 ,將 **"圖像"更改為 "圖像"**

   1. 按下「**新增**」 以新增按鈕。 將**標題**更改`&Print`為 **,ID**`ID_FILE_PRINT`更改為`4`,`4`**將圖像**更改為 ,將 **"圖像"更改為 "圖像"**

   1. 將**項目**類型更改為**分隔符**,然後按下「**添加**」 。

   1. 將**項目**型態變更為**按鍵**。 按下「**新增」** 可新增第五個按鈕。 將**標題**更改`&Close`為 **,ID**`ID_FILE_CLOSE`更改為`5`,`5`**將圖像**更改為 ,將 **"圖像"更改為 "圖像"**

1. 以下修改在上一步中創建的 **「列印」** 按鈕下創建子功能表。

   1. 按下 **「列印」** 按鈕,將 **「專案**」類型更改為 **「標籤**」,然後單擊「 插入」**。** 將**標題**變更`Preview and print the document`為 。

   1. 按下 **「列印」** 按鈕,將 **「專案**」類型更改為 **「按鈕**」,然後單擊「 插入」**。** 將**標題**更改`&Print`為 **,ID**`ID_FILE_PRINT`更改為`4`,`4`**將圖像**更改為 ,將 **"圖像"更改為 "圖像"**

   1. 按下 **「列印」** 按鈕,然後按下「**插入」** 以新增按鈕。 將**標題**更改`&Quick Print`為 **,ID**`ID_FILE_PRINT_DIRECT`更改為`7`,`7`**將圖像**更改為 ,將 **"圖像"更改為 "圖像"**

   1. 按下 **「列印」** 按鈕,然後按一下「**插入」** 以新增另一個按鈕。 將**標題**更改`Print Pre&view`為 **,ID**`ID_FILE_PRINT_PREVIEW`更改為`6`,`6`**將圖像**更改為 ,將 **"圖像"更改為 "圖像"**

   1. 您現在已經變更**了主要項目**。 點選 **「關閉」** 以離開**項目編輯器**。

1. 以下修改將創建一個顯示在 **「應用程式」** 按鈕選單底部的退出按鈕。

   1. 在**解決方案資源管理員**中選擇 **「資源檢視**」選項卡。
   1. 在 **「屬性」** 視窗中,按下**按鍵**旁邊的省略號 **(...)** 以開啟**專案編輯器**。

   1. 選取「**項目**類型 **」 按鈕**後,按下「**添加」** 來新增按鈕。 將**標題**變更為`E&xit` **, ID**變更`ID_APP_EXIT``8`為 ,**影像**變更為 。

   1. 您已變更**按鍵**。 點選 **「關閉」** 以離開**項目編輯器**。

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a>建立功能區列的實體

以下步驟演示如何在應用程式啟動時創建功能區欄的實例。 要向應用程式添加功能區列,請聲明 mainfrm.h 檔中的功能區列。 然後,在 mainfrm.cpp 檔中,編寫代碼以載入功能區資源。

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>建立功能區列的實體

1. 在 mainfrm.h 檔中,將數據成員`CMainFrame`添加到的受保護部分,主幀的類定義。 此成員適用於功能區欄。

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. 在 mainfrm.cpp 檔中`return``CMainFrame::OnCreate`,在函數末尾的最後語句之前添加以下代碼。 它創建功能區欄的實例。

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a>自訂功能區資源

現在,您已經創建了 **「應用程式」** 按鈕,您可以將元素添加到功能區。

> [!NOTE]
> 本演練對所有面板使用相同的面板圖示。 但是,您可以使用其他圖像清單索引來顯示其他圖示。

### <a name="to-add-a-home-category-and-edit-panel"></a>新增首頁「類別和」編輯面板

1. 塗鴉程式只需要一個類別。 在設計檢視中,在 **「工具箱**」中,按兩下 **「類別」** 以添加一個並顯示其屬性。 將屬性值變更為:**Caption**標題`&Home`到,**大圖像**更改為`IDB_RIBBON_HOMELARGE`,`IDB_RIBBON_HOMESMALL`**小圖像**變更為 。

1. 每個功能區類別都組織成命名面板。 每個面板包含一組完成相關操作的控制項。 此類別有一個面板。 點選**面板**,然後將**標題**變更`Edit`為 。

1. 到 **「編輯」** 面板,添加一個按鈕,負責清除文檔的內容。 此按鈕的消息 ID`IDR_SCRIBBTYPE`已在功能表資源中定義。 指定`Clear All`為按鈕文本和修飾按鈕的位圖的索引。 開啟**工具箱**,然後將**按鈕**拖曳到 **「編輯」** 面板。 點選這個按鈕,然後將 **「標題」**`Clear All`變更為`ID_EDIT_CLEAR_ALL`**「%** 到」**影像索引**`0`」 則`0`**會將「大圖像索引」** 變更為 。

1. 保存更改,然後生成並運行應用程式。 應顯示 Scribble 應用程式,並且視窗頂部應有一個功能區列,而不是功能表欄。 功能區列應該有一個類別,**主頁****,和主頁**應該有一個面板,**編輯**。 添加的功能區按鈕應與現有事件處理程式關聯,**並且"打開**、**關閉**、**儲存**、**列印**'和**清除所有按鈕**應按預期工作。

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a>設定應用程式的外觀

*可視化管理員*是控制應用程式所有繪圖的全域物件。 由於原始 Scribble 應用程式使用 Office 2000 使用者介面 (UI) 樣式,因此應用程式可能看起來過時。 您可以重置應用程式以使用 Office 2007 可視化管理器,使其類似於 Office 2007 應用程式。

### <a name="to-set-the-look-of-the-application"></a>設定應用程式的外觀

1. 在`CMainFrame::OnCreate`函數中,`return 0;`在語句之前鍵入以下代碼以更改預設可視管理器和樣式。

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. 保存更改,然後生成並運行應用程式。 應用程式 UI 應類似於 Office 2007 UI。

## <a name="next-steps"></a>後續步驟

您已變更經典 Scribble 1.0 MFC 範例以使用**功能區設計器**。 現在轉到[第二部份](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)<br/>
[逐步解說：更新 MFC Scribble 應用程式 (第 2 部分)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
