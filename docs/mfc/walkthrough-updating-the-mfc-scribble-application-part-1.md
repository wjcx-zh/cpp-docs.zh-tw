---
title: '逐步解說：更新 MFC 自由曲線應用程式 (第1部) '
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: a9eda80fbabf939b9e3a5f8a0ef5b76e46656740
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840254"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>逐步解說：更新 MFC 自由曲線應用程式 (第1部) 

本逐步解說將示範如何修改現有的 MFC 應用程式，以使用功能區使用者介面。 Visual Studio 同時支援 Office 2007 功能區和 Windows 7 Scenic 功能區。 如需功能區使用者介面的詳細資訊，請參閱 [功能區](/windows/win32/uxguide/cmd-ribbons)。

本逐步解說修改了傳統的自由曲線 1.0 MFC 範例，可讓您使用滑鼠來建立線條繪圖。 本逐步解說的這個部分將示範如何修改自由曲線範例，讓它顯示功能區列。 [第2部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) 會將更多按鈕新增至功能區列。

## <a name="prerequisites"></a>先決條件

[自由曲線 1.0 MFC 範例](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe)。 如需轉換為 Visual Studio 2017 或更新版本的說明，請參閱 [移植指南： MFC 自由繪製](../porting/porting-guide-mfc-scribble.md)。

## <a name="sections"></a><a name="top"></a> 部分

本逐步解說的這個部分包含下列各節：

- [取代基類](#replaceclass)

- [將點陣圖新增至專案](#addbitmap)

- [將功能區資源新增至專案](#addribbon)

- [建立功能區列的實例](#createinstance)

- [加入功能區類別](#addcategory)

- [設定應用程式的外觀](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a> 取代基類

若要將支援功能表的應用程式轉換為支援功能區的應用程式，您必須從更新的基類衍生應用程式、框架視窗和工具列類別。  (我們建議您不要修改原始的自由曲線範例。 相反地，請清除自由曲線專案、將它複製到另一個目錄，然後修改複製。 ) 

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>取代自由曲線應用程式中的基類

1. 在隨意的 .cpp 中，確認 `CScribbleApp::InitInstance` 包含對 [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)的呼叫。

1. 將下列程式碼新增至 stdafx.h 中的*pch*檔案 (*stdafx.h* ，Visual Studio 2017 和更早的) ：

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. 在隨意，修改類別的定義， `CScribbleApp` 使其衍生自 [CWinAppEx 類別](../mfc/reference/cwinappex-class.md)。

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. 當 Windows 應用程式使用初始化 ( .ini) 檔案來儲存使用者喜好設定資料時，就會撰寫塗抹1.0。 您可以修改「自由化」以將使用者喜好設定儲存在登錄中，而不是初始化檔。 若要設定登錄機碼和基底，請在語句之後輸入下列程式碼 `CScribbleApp::InitInstance` `LoadStdProfileSettings()` 。

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. 多個檔介面的主框架 (MDI) 應用程式不再衍生自 `CMDIFrameWnd` 類別。 相反地，它是衍生自 [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) 類別。

    在 mainfrm.cpp .h 和 mainfrm.cpp .cpp 檔案中，將所有的參考取代為 `CMDIFrameWnd` `CMDIFrameWndEx` 。

1. 在 childfrm .h 和 childfrm .cpp 檔案中，將取代 `CMDIChildWnd` 為 `CMDIChildWndEx` 。

    在 childfrm 中。 h 檔案，將取代 `CSplitterWnd` 為 `CSplitterWndEx` 。

1. 修改工具列和狀態列，以使用新的 MFC 類別。

    在 mainfrm.cpp .h 檔案中：

    1. 將 `CToolBar` 取代為 `CMFCToolBar`。

    1. 將 `CStatusBar` 取代為 `CMFCStatusBar`。

1. 在 mainfrm.cpp .cpp 檔案中：

    1. 將 `m_wndToolBar.SetBarStyle` 取代為 `m_wndToolBar.SetPaneStyle`

    1. 將 `m_wndToolBar.GetBarStyle` 取代為 `m_wndToolBar.GetPaneStyle`

    1. 將 `DockControlBar(&m_wndToolBar)` 取代為 `DockPane(&m_wndToolBar)`

1. 在 ipframe .cpp 檔案中，將下列三行程式碼標記為批註。

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. 儲存變更，然後建立並執行應用程式。

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a> 將點陣圖新增至專案

本逐步解說的後續四個步驟需要點陣圖資源。 您可以透過各種方式取得適當的點陣圖：

- 使用 [資源編輯器](../windows/resource-editors.md) 來創造您自己的點陣圖。 或者，您也可以使用資源編輯器，將點陣圖從可攜的網狀圖形組合 ( .png) Visual Studio 隨附的影像，而且可以從 [Visual Studio 的影像庫](/visualstudio/designers/the-visual-studio-image-library)中下載。

    但是， **功能區** 使用者介面需要某些點陣圖支援透明影像。 透明點陣圖使用32位圖元，其中24位指定色彩的紅色、綠色和藍色元件，而8位則定義指定色彩透明度的 *Alpha* 色板。 目前的資源編輯器可以看到，但不能修改具有32位圖元的點陣圖。 因此，請使用外部影像編輯器而非資源編輯器來操作透明點陣圖。

- 從另一個應用程式將適當的資源檔案複製到您的專案，然後從該檔案匯入點陣圖。

本逐步解說會從 [逐步解說：使用 MFC 建立功能區應用程式](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)中建立的範例複製資源檔。

### <a name="to-add-bitmaps-to-the-project"></a>將點陣圖新增至專案

1. 使用檔案總管將下列 .bmp 檔案從 `res` 功能區範例 () 複製到「自由」專案的「資原始目錄」 (`res`) ：

   1. 將 main.bmp 複製到您的塗抹專案。

   1. 將 filesmall.bmp 和 filelarge.bmp 複製到您的塗抹專案。

   1. 製作 filelarge.bmp 和 filesmall.bmp 檔案的新複本，但是將複本儲存在功能區範例中。 將複本重新命名 homesmall.bmp 並 homelarge.bmp，然後將複本移至您的塗抹專案。

   1. 製作 toolbar.bmp 檔案的複本，但是將複本儲存在功能區範例中。 將複製 panelicons.bmp 重新命名，然後將複本移至您的塗抹專案。

1. 匯入 MFC 應用程式的點陣圖。 在 **資源檢視**中，按兩下 [ **塗抹] .rc** 節點，按兩下 **點陣圖** 節點，然後按一下 [ **新增資源**]。 在出現的對話方塊上，按一下 [匯 **入**]。 流覽至 `res` 目錄，選取 main.bmp 檔案，然後按一下 [ **開啟**]。

   main.bmp 點陣圖包含26x26 影像。 將點陣圖的識別碼變更為 `IDB_RIBBON_MAIN` 。

1. 匯入附加至 **應用程式** 按鈕的 [檔案] 功能表點陣圖。

   1. 匯入 filesmall.bmp 檔案，其中包含11個 16x16 (16x176) 映射。 將點陣圖的識別碼變更為 `IDB_RIBBON_FILESMALL` 。

   > [!NOTE]
   > 因為我們只需要前八個16個影像 (16x128) ，所以您可以選擇性地將此點陣圖的右邊寬度從176裁剪至128。

   1. 匯入 filelarge.bmp，其中包含九個 32 (32x288) 映射。 將點陣圖的識別碼變更為 `IDB_RIBBON_FILELARGE` 。

1. 匯入功能區類別和麵板的點陣圖。 功能區列上的每個索引標籤都是類別目錄，而且是由文字標籤和選擇性影像所組成。

   1. 匯入 homesmall.bmp 點陣圖，其中包含小型按鈕點陣圖的11個16x16 影像。 將點陣圖的識別碼變更為 `IDB_RIBBON_HOMESMALL` 。

   1. 匯入 homelarge.bmp 點陣圖，其中包含九個大型按鈕點陣圖的32x32 影像。 將點陣圖的識別碼變更為 `IDB_RIBBON_HOMELARGE` 。

1. 匯入調整大小功能區面板的點陣圖。 如果功能區太小而無法顯示整個面板，則在調整大小作業之後，會使用這些點陣圖或面板圖示。

   1. 匯入包含八個16x16 影像的 panelicons.bmp 點陣圖。 在**點陣圖編輯器**的 [**屬性**] 視窗中，將點陣圖的寬度調整為 64 (16x64) 。 將點陣圖的識別碼變更為 `IDB_PANEL_ICONS` 。

   > [!NOTE]
   > 因為我們只需要前四個16個影像 (16x64) ，所以您可以選擇性地將此點陣圖的右邊寬度從128裁剪至64。

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a> 將功能區資源新增至專案

當您將使用功能表的應用程式轉換為使用功能區的應用程式時，您不需要移除或停用現有的功能表。 您只需建立功能區資源、加入功能區按鈕，然後將新按鈕與現有的功能表項目產生關聯。 雖然不會再顯示功能表，但是來自功能區列的訊息會透過功能表和功能表快捷方式繼續運作。

功能區是由 **應用程式** 按鈕所組成，也就是功能區左上方的大型按鈕，以及一個或多個類別索引標籤。 每個 [類別] 索引標籤包含一或多個作為功能區按鈕和控制項容器的面板。 下列程式顯示如何建立功能區資源，然後自訂 **應用程式** 按鈕。

### <a name="to-add-a-ribbon-resource-to-the-project"></a>將功能區資源新增至專案

1. 在 **方案總管**中選取 [自由曲線] 專案時，按一下 [ **專案** ] 功能表中的 [ **新增資源**]。

1. 在 [ **新增資源** ] 對話方塊中，選取 [ **功能區** ]，然後按一下 [ **新增**]。

   Visual Studio 會建立功能區資源，並在設計檢視中開啟它。 功能區資源識別碼是 `IDR_RIBBON1` 在 **資源檢視**中顯示。 功能區包含一個類別和一個面板。

1. 您可以藉由修改應用程式的屬性來自訂 **應用程式** 按鈕。 這段程式碼中使用的訊息識別碼已經在 [塗抹 1.0] 的功能表中定義。

1. 在設計檢視中，按一下 [ **應用程式** ] 按鈕以顯示其屬性。 變更屬性值，如下所示： **影像** 到 `IDB_RIBBON_MAIN` 、 **提示** `File` 、索引 **鍵** `f` 、 **大型影像** 至 `IDB_RIBBON_FILELARGE` 和 **小型影像** `IDB_RIBBON_FILESMALL` 。

1. 下列修改會建立當使用者按一下 **應用程式** 按鈕時所顯示的功能表。 按一下 [**主要專案**] 旁的省略號 (**...**) 以開啟 [**專案編輯器**]。

   1. 選取 **專案** 類型 **按鈕** 後，按一下 [ **新增** ] 以加入按鈕。 將 [**標題**] 變更為，並將 [識別碼] 變更為 [影像 `&New` **ID** `ID_FILE_NEW` **Image** `0` **大小**] `0` 。

   1. 按一下 [ **新增** ] 以加入按鈕。 將**標題**變更為、將識別碼變更為，並將影像的大小變更為 `&Save` **ID** `ID_FILE_SAVE` **Image** `2` **Image Large** `2` 。

   1. 按一下 [ **新增** ] 以加入按鈕。 將**標題**變更為、將識別碼變更為，並將影像的大小變更為 `Save &As` **ID** `ID_FILE_SAVE_AS` **Image** `3` **Image Large** `3` 。

   1. 按一下 [ **新增** ] 以加入按鈕。 將**標題**變更為、將識別碼變更為，並將影像的大小變更為 `&Print` **ID** `ID_FILE_PRINT` **Image** `4` **Image Large** `4` 。

   1. 將 [ **專案** 類型] 變更為 [ **分隔符號** ]，然後按一下 [ **加入**]。

   1. 將 [ **專案** 類型] 變更為 **按鈕**。 按一下 [ **新增** ] 以加入第五個按鈕。 將**標題**變更為、將識別碼變更為，並將影像的大小變更為 `&Close` **ID** `ID_FILE_CLOSE` **Image** `5` **Image Large** `5` 。

1. 下列修改會在您于上一個步驟中建立的 [ **列印** ] 按鈕底下建立子功能表。

   1. 按一下 [ **列印** ] 按鈕，將 [ **專案** 類型] 變更為 [ **標籤**]，然後按一下 [ **插入**]。 將 **標題** 變更為 `Preview and print the document` 。

   1. 按一下 [ **列印** ] 按鈕，將 [ **專案** 類型] 變更為 [ **按鈕**]，然後按一下 [ **插入**]。 將**標題**變更為、將識別碼變更為，並將影像的大小變更為 `&Print` **ID** `ID_FILE_PRINT` **Image** `4` **Image Large** `4` 。

   1. 按一下 [ **列印** ] 按鈕，然後按一下 [ **插入** ] 以加入按鈕。 將**標題**變更為、將識別碼變更為，並將影像的大小變更為 `&Quick Print` **ID** `ID_FILE_PRINT_DIRECT` **Image** `7` **Image Large** `7` 。

   1. 按一下 [ **列印** ] 按鈕，然後按一下 [ **插入** ] 以新增另一個按鈕。 將**標題**變更為、將識別碼變更為，並將影像的大小變更為 `Print Pre&view` **ID** `ID_FILE_PRINT_PREVIEW` **Image** `6` **Image Large** `6` 。

   1. 您現在已修改 **主要專案**。 按一下 [關閉] 以 **結束** [ **專案編輯器**]。

1. 下列修改會建立一個出現在 [ **應用程式** ] 按鈕功能表底部的 [結束] 按鈕。

   1. 選擇**方案總管**中的 [**資源檢視**] 索引標籤。
   1. 在 [**屬性**] 視窗中，按一下**按鈕**旁的省略號 (**...**) 以開啟 [**專案編輯器**]。

   1. 選取 **專案** 類型 **按鈕** 後，按一下 [ **新增** ] 以加入按鈕。 將**標題**變更為，並將 `E&xit` 影像的**識別碼**變更為 `ID_APP_EXIT` **Image** `8` 。

   1. 您已修改 **按鈕**。 按一下 [關閉] 以 **結束** [ **專案編輯器**]。

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a> 建立功能區列的實例

下列步驟說明如何在應用程式啟動時建立功能區列的實例。 若要將功能區列加入至應用程式，請在 mainfrm.cpp .h 檔案中宣告功能區列。 然後，在 mainfrm.cpp .cpp 檔案中，撰寫程式碼以載入功能區資源。

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>若要建立功能區列的實例

1. 在 mainfrm.cpp 檔案中，將資料成員加入至主框架的類別定義的受保護區段 `CMainFrame` 。 此成員適用于功能區列。

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. 在 mainfrm.cpp .cpp 檔案中，將下列程式碼新增至函式結尾的最後一個 **`return`** 語句之前 `CMainFrame::OnCreate` 。 它會建立功能區列的實例。

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a> 自訂功能區資源

現在您已建立 **應用程式** 按鈕，您可以將元素加入至功能區。

> [!NOTE]
> 本逐步解說會針對所有面板使用相同的面板圖示。 不過，您可以使用其他影像清單索引來顯示其他圖示。

### <a name="to-add-a-home-category-and-edit-panel"></a>新增首頁分類和編輯面板

1. 自由曲線程式只需要一個類別。 在設計檢視的 [ **工具箱**] 中，按兩下 [ **類別** ] 以新增一個，並顯示其屬性。 變更屬性值，如下所示： **標題** 為 `&Home` 、 **大型影像** 至 `IDB_RIBBON_HOMELARGE` 、 **小型** 影像至 `IDB_RIBBON_HOMESMALL` 。

1. 每個功能區類別都會組織成命名面板。 每個面板都包含一組完成相關作業的控制項。 此類別有一個面板。 按一下 [ **面板**]，然後將 [ **標題** ] 變更為 `Edit` 。

1. 在 [ **編輯** ] 面板中，新增負責清除檔內容的按鈕。 此按鈕的訊息識別碼已在 `IDR_SCRIBBTYPE` 功能表資源中定義。 指定 `Clear All` 做為按鈕文字，以及裝飾按鈕的點陣圖索引。 開啟 [ **工具箱**]，然後將 **按鈕** 拖曳至 [ **編輯** ] 面板。 按一下該按鈕，然後將 [**標題**為]、[識別碼]、[影像索引] 變更為 [ `Clear All` **ID** `ID_EDIT_CLEAR_ALL` **Image Index** `0` **大型影像索引**] `0` 。

1. 儲存變更，然後建立並執行應用程式。 此時應該會顯示自由顯示應用程式，而且視窗頂端應該會有一個功能區列，而不是功能表列。 功能區列應該有一個類別、 **首頁**和 **首頁** 應該有一個面板，請 **編輯**。 您加入的功能區按鈕應與現有的事件處理常式相關聯，而 **開啟**、 **關閉**、 **儲存**、 **列印**和 **清除所有** 按鈕應如預期般運作。

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a> 設定應用程式的外觀

*視覺化管理員*是控制應用程式所有繪圖的全域物件。 由於原始的自由曲線應用程式會使用 Office 2000 使用者介面 (UI) 樣式，因此應用程式可能看起來很舊。 您可以重設應用程式以使用 Office 2007 視覺管理員，使其類似于 Office 2007 應用程式。

### <a name="to-set-the-look-of-the-application"></a>若要設定應用程式的外觀

1. 在 `CMainFrame::OnCreate` 函數中，于語句之前輸入下列程式碼， `return 0;` 以變更預設的視覺化管理員和樣式。

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. 儲存變更，然後建立並執行應用程式。 應用程式 UI 應該與 Office 2007 UI 類似。

## <a name="next-steps"></a>後續步驟

您已修改傳統的塗抹 1.0 MFC 範例，以使用 **功能區設計**工具。 現在請移至 [第2部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)<br/>
[逐步解說：更新 MFC 自由曲線應用程式 (第2部分) ](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
