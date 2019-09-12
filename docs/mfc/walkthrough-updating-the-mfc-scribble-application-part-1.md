---
title: 逐步解說：更新 MFC 塗抹應用程式（第1部分）
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 23ddf92514674c32e28c259c4c7aa8f742302485
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907413"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>逐步解說：更新 MFC 塗抹應用程式（第1部分）

本逐步解說示範如何修改現有的 MFC 應用程式，以使用功能區使用者介面。 Visual Studio 同時支援 Office 2007 功能區和 Windows 7 Scenic 功能區。 如需功能區使用者介面的詳細資訊，請參閱[功能區](/windows/win32/uxguide/cmd-ribbons)。

此逐步解說會修改傳統的塗抹 1.0 MFC 範例，讓您可以使用滑鼠來建立線條繪圖。 本逐步解說的這個部分會示範如何修改「塗抹」範例，使其顯示功能區列。 [第2部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)會在功能區列中加入更多按鈕。

## <a name="prerequisites"></a>必要條件

「[塗抹」 1.0 MFC 範例](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe)。 如需轉換為 Visual Studio 2017 或更新版本的協助[，請參閱移植指南：MFC 自由](../porting/porting-guide-mfc-scribble.md)繪製。

##  <a name="top"></a> 章節

本逐步解說的這個部分包含下列各節：

- [取代基類](#replaceclass)

- [將點陣圖新增至專案](#addbitmap)

- [將功能區資源加入至專案](#addribbon)

- [建立功能區列的實例](#createinstance)

- [加入功能區分類](#addcategory)

- [設定應用程式的外觀](#setlook)

##  <a name="replaceclass"></a>取代基類

若要將支援功能表的應用程式轉換為支援功能區的應用程式，您必須從更新的基類衍生應用程式、框架視窗和工具列類別。 （建議您不要修改原始的自由曲線範例。 相反地，請清除 [塗抹] 專案，將它複製到另一個目錄，然後修改複本）。

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>取代塗抹應用程式中的基類

1. 在 [塗抹] .cpp 中， `CScribbleApp::InitInstance`確認包含對[AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)的呼叫。

1. 將下列程式碼新增至*pch*檔案（Visual Studio 2017 和更早版本中的*stdafx.h* ）：

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. 在自由的 .h 中，修改`CScribbleApp`類別的定義，使其衍生自[CWinAppEx 類別](../mfc/reference/cwinappex-class.md)。

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. 當 Windows 應用程式使用初始化（.ini）檔案來儲存使用者喜好設定資料時，會寫入「塗抹1.0」。 請修改「塗抹」，而不是初始化檔，以將使用者喜好設定儲存在登錄中。 若要設定登錄機碼和基底，請在`CScribbleApp::InitInstance` `LoadStdProfileSettings()`語句後面輸入下列程式碼。

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. 多重文件介面（MDI）應用程式的主框架不再衍生自`CMDIFrameWnd`類別。 相反地，它是衍生自[CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)類別。

    在 mainfrm.cpp 和 mainfrm.cpp .cpp 檔案中，將的`CMDIFrameWnd` `CMDIFrameWndEx`所有參考取代為。

1. 在 childfrm 和 childfrm .cpp 檔案中，將取代`CMDIChildWnd`為。 `CMDIChildWndEx`

    在 childfrm 中。 h 檔案，請`CSplitterWnd`將`CSplitterWndEx`取代為。

1. 修改工具列和狀態列，以使用新的 MFC 類別。

    在 mainfrm.cpp .h 檔案中：

    1. 將 `CToolBar` 取代為 `CMFCToolBar`。

    1. 將 `CStatusBar` 取代為 `CMFCStatusBar`。

1. 在 mainfrm.cpp .cpp 檔案中：

    1. 取代`m_wndToolBar.SetBarStyle`為`m_wndToolBar.SetPaneStyle`

    1. 取代`m_wndToolBar.GetBarStyle`為`m_wndToolBar.GetPaneStyle`

    1. 取代`DockControlBar(&m_wndToolBar)`為`DockPane(&m_wndToolBar)`

1. 在 ipframe .cpp 檔案中，將下列三行程式碼標記為批註。

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. 儲存變更，然後建立並執行應用程式。

##  <a name="addbitmap"></a>將點陣圖新增至專案

本逐步解說的接下來四個步驟需要點陣圖資源。 您可以透過各種方式取得適當的點陣圖：

- 使用[資源編輯器](../windows/resource-editors.md)來創造您自己的點陣圖。 或者，您可以使用資源編輯器，從包含在 Visual Studio 中的可移植網狀圖形（.png）影像組合點陣圖，並從[Visual Studio 影像庫](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library)下載。

    不過，**功能區**使用者介面需要某些點陣圖支援透明影像。 透明點陣圖使用32位圖元，其中24位會指定色彩的紅色、綠色和藍色元件，而8位則定義指定色彩透明度的*Alpha*色板。 目前的資源編輯器可以查看，但不能修改具有32位圖元的點陣圖。 因此，請使用外部影像編輯器，而不是資源編輯器來操作透明點陣圖。

- 將適當的資源檔從另一個應用程式複製到您的專案，然後從該檔案匯入點陣圖。

本逐步解說會從[逐步解說：使用 MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)建立功能區應用程式。

### <a name="to-add-bitmaps-to-the-project"></a>若要將點陣圖新增至專案

1. 使用 [檔案瀏覽器] 將下列 .bmp 檔案從功能區範例的`res`resources 目錄（）複製到自由曲線專案的`res`資原始目錄（）：

   1. 將主要 .bmp 複製到您的塗抹專案。

   1. 將 filesmall 複製到您的塗抹專案。

   1. 建立 filelarge 的新複本和 filesmall 檔案，但將複本儲存在功能區範例中。 將複本重新命名為 homesmall 和 homelarge，然後將複本移至您的自由繪製專案。

   1. 建立 toolbar 檔案的複本，但將複本儲存在功能區範例中。 將複製 panelicons 重新命名，然後將複本移至您的自由曲線專案。

1. 匯入 MFC 應用程式的點陣圖。 在**資源檢視**中，按兩下 [塗抹] [ **.rc** ] 節點，按兩下 [**點陣圖**] 節點，然後按一下 [**新增資源**]。 在出現的對話方塊上，按一下 [匯**入**]。 流覽至`res`目錄，選取主要的 .bmp 檔案，然後按一下 [**開啟**]。

   主要 .bmp 點陣圖包含26x26 影像。 將點陣圖的識別碼變更為`IDB_RIBBON_MAIN`。

1. 匯入附加至 [**應用程式**] 按鈕之 [檔案] 功能表的點陣圖。

   1. 匯入包含11個16x16 （16x176）影像的 filesmall .bmp 檔案。 將點陣圖的識別碼變更為`IDB_RIBBON_FILESMALL`。

   > [!NOTE]
   > 因為我們只需要前八個16x16 影像（16x128），所以您可以選擇性地將此點陣圖的右端寬度從176裁剪為128。

   1. 匯入 filelarge，其中包含9個32x32 （32x288）影像。 將點陣圖的識別碼變更為`IDB_RIBBON_FILELARGE`。

1. 匯入功能區分類和麵板的點陣圖。 功能區列上的每個索引標籤都是分類，而且是由文字標籤和選擇性影像所組成。

   1. 匯入 homesmall，其中包含小型按鈕點陣圖的11個16x16 影像。 將點陣圖的識別碼變更為`IDB_RIBBON_HOMESMALL`。

   1. 匯入 homelarge，其中包含九個適用于大型按鈕點陣圖的32x32 影像。 將點陣圖的識別碼變更為`IDB_RIBBON_HOMELARGE`。

1. 匯入已調整大小之功能區面板的點陣圖。 如果功能區太小而無法顯示整個面板，則在調整大小作業之後，會使用這些點陣圖或面板圖示。

   1. 匯入 panelicons，其中包含八個16x16 影像。 在 [**點陣圖編輯器**] 的 [**屬性**] 視窗中，將點陣圖的寬度調整為64（16x64）。 將點陣圖的識別碼變更為`IDB_PANEL_ICONS`。

   > [!NOTE]
   > 因為我們只需要前四個16x16 影像（16x64），所以您可以選擇性地將此點陣圖的右端寬度從128裁剪為64。

##  <a name="addribbon"></a>將功能區資源加入至專案

當您將使用功能表的應用程式轉換為使用功能區的應用程式時，您不需要移除或停用現有的功能表。 只需建立功能區資源、加入功能區按鈕，然後將新按鈕與現有的功能表項目建立關聯。 雖然不會再看到功能表，但來自功能區列的訊息會透過功能表和功能表快捷方式來路由傳送。

功能區包含 [**應用程式**] 按鈕，也就是功能區左上方的大型按鈕，以及一或多個類別目錄索引標籤。 每個 [類別] 索引標籤都包含一個或多個面板，做為功能區按鈕和控制項的容器。 下列程式說明如何建立功能區資源，然後自訂**應用程式**按鈕。

### <a name="to-add-a-ribbon-resource-to-the-project"></a>若要將功能區資源加入至專案

1. 在**方案總管**中選取 [塗抹] 專案後，按一下 [**專案**] 功能表中的 [**新增資源**]。

1. 在 [**新增資源**] 對話方塊中，選取 [**功能區**]，然後按一下 [**新增**]。

   Visual Studio 會建立功能區資源，並在設計檢視中開啟它。 功能區資源識別碼是`IDR_RIBBON1`，會顯示在**資源檢視**中。 功能區包含一個類別和一個面板。

1. 您可以藉由修改**應用程式**按鈕的屬性來自訂它。 這段程式碼中所使用的訊息識別碼已在 [曲線 1.0] 的功能表中定義。

1. 在設計檢視中，按一下 [**應用程式**] 按鈕以顯示其屬性。 變更屬性值，如下所示：**影像**至`IDB_RIBBON_MAIN` `File`、**提示輸入**、**索引鍵** `IDB_RIBBON_FILESMALL` `IDB_RIBBON_FILELARGE` 、大型影像至，以及小型影像至。 `f`

1. 下列修改會建立使用者按一下**應用程式**按鈕時所顯示的功能表。 按一下 [**主要專案**] 旁的省略號（ **...** ），以開啟 [**專案編輯器**]。

   1. 選取 [**專案**類型]**按鈕**後，按一下 [**新增**] 以新增按鈕。 將 [標題`&New`]變更為`ID_FILE_NEW`，將 [ `0`識別碼]**變更為，** 影像 [**大**至`0`]。

   1. 按一下 [**新增**] 以新增按鈕。 將**標題**變更`&Save`為 、ID `ID_FILE_SAVE`為 、影像`2`為，並將**影像大**到`2`。

   1. 按一下 [**新增**] 以新增按鈕。 將**標題**變更`Save &As`為 、ID `ID_FILE_SAVE_AS`為 、影像`3`為，並將**影像大**到`3`。

   1. 按一下 [**新增**] 以新增按鈕。 將**標題**變更`&Print`為 、ID `ID_FILE_PRINT`為 、影像`4`為，並將**影像大**到`4`。

   1. 變更 **項目** 類型 **分隔符號**，然後按一下 **新增**。

   1. 變更 **項目** 類型 **按鈕**。 按一下 [**新增**] 以新增第五個按鈕。 將**標題**變更`&Close`為 、ID `ID_FILE_CLOSE`為 、影像`5`為，並將**影像大**到`5`。

1. 下列修改會在您于上一個步驟中建立的 [**列印**] 按鈕底下建立子功能表。

   1. 按一下 [**列印**] 按鈕，將**專案**類型變更為 [**標籤**]，然後按一下 [**插入**]。 將**標題**變更`Preview and print the document`為。

   1. 按一下 **列印** 按鈕，變更 **項目** 類型 **按鈕**，然後按一下**插入**。 將**標題**變更`&Print`為 、ID `ID_FILE_PRINT`為 、影像`4`為，並將**影像大**到`4`。

   1. 按一下 [**列印**] 按鈕，然後按一下 [**插入**] 來新增按鈕。 將**標題**變更`&Quick Print`為 、ID `ID_FILE_PRINT_DIRECT`為 、影像`7`為，並將**影像大**到`7`。

   1. 按一下 [**列印**] 按鈕，然後按一下 [**插入**] 以加入另一個按鈕。 將**標題**變更`Print Pre&view`為 、ID `ID_FILE_PRINT_PREVIEW`為 、影像`6`為，並將**影像大**到`6`。

   1. 您現在已修改**主要專案**。 按一下 [關閉] 以**結束**[**專案編輯器**]。

1. 下列修改會建立出現在**應用程式**按鈕功能表底部的 [結束] 按鈕。

   1. 選擇**方案總管**中的 [**資源檢視**] 索引標籤。
   1. 在 **屬性** 視窗中，按一下省略符號 ( **...** ) 旁 **按鈕** 以開啟 **項目編輯器** 。

   1. 選取 [**專案**類型]**按鈕**後，按一下 [**新增**] 以新增按鈕。 將 [標題`E&xit`] 變更為`ID_APP_EXIT`，並將`8`[**識別碼**]**變更為。**

   1. 您已修改**按鈕**。 按一下 [關閉] 以**結束**[**專案編輯器**]。

##  <a name="createinstance"></a>建立功能區列的實例

下列步驟示範如何在應用程式啟動時建立功能區列的實例。 若要將功能區列新增至應用程式，請在 mainfrm.cpp 檔案中宣告功能區列。 然後，在 mainfrm.cpp .cpp 檔案中，撰寫程式碼來載入功能區資源。

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>建立功能區列的實例

1. 在 mainfrm.cpp 檔案中，將資料成員加入至的 protected 區段`CMainFrame`（主要框架的類別定義）。 這個成員適用于功能區列。

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. 在 mainfrm.cpp .cpp 檔案中，將下列程式碼新增至函式`return`結尾`CMainFrame::OnCreate`的最後一個語句前面。 它會建立功能區列的實例。

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

##  <a name="addcategory"></a>自訂功能區資源

既然您已建立**應用程式**按鈕，就可以將專案加入至功能區。

> [!NOTE]
> 本逐步解說會針對所有面板使用相同的面板圖示。 不過，您可以使用其他影像清單索引來顯示其他圖示。

### <a name="to-add-a-home-category-and-edit-panel"></a>新增主類別和編輯面板

1. 自由曲線程式只需要一個類別。 在設計檢視的 [**工具箱**] 中，按兩下 [**類別**] 以加入一個，並顯示其屬性。 變更屬性值，如下所示：**標題**為`&Home` **，大型影像**至`IDB_RIBBON_HOMESMALL` ，小型影像至。 `IDB_RIBBON_HOMELARGE`

1. 每個功能區分類都會組織成命名面板。 每個面板都包含一組可完成相關作業的控制項。 這個類別有一個面板。 按一下 [**面板**]，然後將 [ `Edit`**標題**] 變更為。

1. 在 [**編輯**] 面板中，新增負責清除檔內容的按鈕。 此按鈕的訊息識別碼已在`IDR_SCRIBBTYPE`功能表資源中定義。 指定`Clear All`做為按鈕文字，以及裝飾按鈕的點陣圖索引。 開啟 **工具箱** ，然後將拖曳 **按鈕** 來 **編輯** 面板。 按一下 [] 按鈕，然後將 [ `Clear All`標題 `ID_EDIT_CLEAR_ALL`] 變更為 [將**影像索引**設`0`為]， `0`將 [**大型影像索引**] 變更為。

1. 儲存變更，然後建立並執行應用程式。 應該會顯示「塗抹應用程式」，而視窗頂端應該會有一個功能區列，而不是功能表列。 功能區列應該有一個 [類別]、[**首頁**] 和 [**首頁**] 應該有一個面板 [**編輯**]。 您所加入的功能區按鈕應該與現有的事件處理常式相關聯，而且 [**開啟**]、[**關閉**]、[**儲存**]、[**列印**] 和 [**全部清除**] 按鈕應該會如預期般運作。

##  <a name="setlook"></a>設定應用程式的外觀

*視覺化管理員*是一個全域物件，可控制應用程式的所有繪圖。 由於原始的塗抹應用程式會使用 Office 2000 使用者介面（UI）樣式，因此應用程式可能看起來很舊。 您可以將應用程式重設為使用 Office 2007 視覺效果管理員，使其類似于 Office 2007 應用程式。

### <a name="to-set-the-look-of-the-application"></a>若要設定應用程式的外觀

1. 在函式中，于`return 0;`語句之前輸入下列程式碼，以變更預設的視覺效果管理員和樣式。 `CMainFrame::OnCreate`

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. 儲存變更，然後建立並執行應用程式。 應用程式 UI 應該與 Office 2007 UI 類似。

## <a name="next-steps"></a>後續步驟

您已修改傳統的塗抹 1.0 MFC 範例，以使用**功能區設計**工具。 現在請移至[第2部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)<br/>
[逐步解說：更新 MFC Scribble 應用程式 (第 2 部分)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
