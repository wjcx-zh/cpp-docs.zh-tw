---
title: "CToolBarCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CToolBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class
- Windows common controls [C++], CToolBarCtrl
- toolbar controls [MFC], CToolBarCtrl class
- tool tips [C++], notifications
ms.assetid: 8f2f8ad2-05d7-4975-8715-3f2eed795248
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2d3ec23d6147299d9a615e9edb0d3f90680bbfac
ms.lasthandoff: 02/24/2017

---
# <a name="ctoolbarctrl-class"></a>CToolBarCtrl 類別
提供 Windows 工具列通用控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CToolBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CToolBarCtrl::CToolBarCtrl](#ctoolbarctrl)|建構 `CToolBarCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CToolBarCtrl::AddBitmap](#addbitmap)|將一或多個點陣圖按鈕影像加入至工具列控制項可用的按鈕影像清單。|  
|[CToolBarCtrl::AddButtons](#addbuttons)|將一或多個按鈕加入至 toolbar 控制項。|  
|[CToolBarCtrl::AddString](#addstring)|加入新的字串，傳遞做為資源識別碼，工具列的內部清單的字串。|  
|[CToolBarCtrl::AddStrings](#addstrings)|新增新的字串或 null 分隔的字串，字串工具列的內部清單之緩衝區的指標傳遞的字串。|  
|[CToolBarCtrl::AutoSize](#autosize)|調整工具列控制項的大小。|  
|[CToolBarCtrl::ChangeBitmap](#changebitmap)|變更目前的工具列控制項中的按鈕的點陣圖。|  
|[CToolBarCtrl::CheckButton](#checkbutton)|檢查或清除 在工具列控制項中指定的按鈕。|  
|[CToolBarCtrl::CommandToIndex](#commandtoindex)|擷取與指定的命令識別項相關聯的按鈕以零為起始的索引。|  
|[CToolBarCtrl::Create](#create)|建立工具列控制項並將它附加`CToolBarCtrl`物件。|  
|[CToolBarCtrl::CreateEx](#createex)|建立具有指定的 Windows 延伸樣式工具列控制項，並將它附加`CToolBarCtrl`物件。|  
|[CToolBarCtrl::Customize](#customize)|顯示 [自訂工具列] 對話方塊。|  
|[CToolBarCtrl::DeleteButton](#deletebutton)|刪除工具列控制項中的按鈕。|  
|[CToolBarCtrl::EnableButton](#enablebutton)|啟用或停用工具列控制項中指定的按鈕。|  
|[CToolBarCtrl::GetAnchorHighlight](#getanchorhighlight)|擷取錨點反白顯示的工具列設定。|  
|[CToolBarCtrl::GetBitmap](#getbitmap)|擷取點陣圖中的工具列按鈕相關聯的索引。|  
|[CToolBarCtrl::GetBitmapFlags](#getbitmapflags)|取得相關聯的工具列點陣圖的旗標。|  
|[CToolBarCtrl::GetButton](#getbutton)|擷取指定的按鈕，在工具列控制項中的相關資訊。|  
|[CToolBarCtrl::GetButtonCount](#getbuttoncount)|擷取目前在工具列控制項中的按鈕的計數。|  
|[CToolBarCtrl::GetButtonInfo](#getbuttoninfo)|擷取在工具列中按鈕的資訊。|  
|[CToolBarCtrl::GetButtonSize](#getbuttonsize)|擷取目前的寬度和高度，單位為像素的工具列按鈕。|  
|[CToolBarCtrl::GetColorScheme](#getcolorscheme)|擷取目前的工具列控制項的色彩配置。|  
|[CToolBarCtrl::GetDisabledImageList](#getdisabledimagelist)|擷取映像清單工具列控制項用來顯示停用按鈕。|  
|[CToolBarCtrl::GetDropTarget](#getdroptarget)|擷取[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)工具列控制項的介面。|  
|[CToolBarCtrl::GetExtendedStyle](#getextendedstyle)|擷取在工具列控制項的延伸的樣式。|  
|[CToolBarCtrl::GetHotImageList](#gethotimagelist)|擷取映像清單工具列控制項用來顯示 「 熱門 」 按鈕。 當滑鼠指標位於其上方時，會反白顯示作用中的按鈕。|  
|[CToolBarCtrl::GetHotItem](#gethotitem)|擷取在工具列中作用的項目索引。|  
|[CToolBarCtrl::GetImageList](#getimagelist)|擷取映像清單工具列控制項用來顯示按鈕為預設狀態。|  
|[CToolBarCtrl::GetInsertMark](#getinsertmark)|擷取目前的插入標記的工具列。|  
|[CToolBarCtrl::GetInsertMarkColor](#getinsertmarkcolor)|擷取用來繪製工具列插入標記的色彩。|  
|[CToolBarCtrl::GetItemRect](#getitemrect)|擷取控制項中的工具列按鈕的周框矩形。|  
|[CToolBarCtrl::GetMaxSize](#getmaxsize)|擷取所有可見的按鈕和工具列中的分隔線的總大小。|  
|[CToolBarCtrl::GetMaxTextRows](#getmaxtextrows)|擷取工具列按鈕上顯示的文字資料列的數目上限。|  
|[CToolBarCtrl::GetMetrics](#getmetrics)|擷取工具列控制項的度量。|  
|[CToolBarCtrl::GetPadding](#getpadding)|擷取目前的工具列控制項的水平和垂直邊框距離。|  
|[CToolBarCtrl::GetPressedImageList](#getpressedimagelist)|擷取映像清單目前的工具列控制項用來代表按下狀態的按鈕。|  
|[CToolBarCtrl::GetRect](#getrect)|擷取指定的工具列按鈕，這個周框。|  
|[CToolBarCtrl::GetRows](#getrows)|擷取目前顯示在工具列中按鈕的資料列數目。|  
|[CToolBarCtrl::GetState](#getstate)|擷取指定的按鈕，在工具列控制項中，例如它、 按下，是否啟用檢查狀態相關資訊。|  
|[CToolBarCtrl::GetString](#getstring)|擷取工具列字串。|  
|[CToolBarCtrl::GetStyle](#getstyle)|擷取目前在使用工具列控制項的樣式。|  
|[CToolBarCtrl::GetToolTips](#gettooltips)|擷取工具提示控制項的控制代碼，如果有的話與工具列控制項產生關聯。|  
|[CToolBarCtrl::HideButton](#hidebutton)|隱藏或顯示工具列控制項中指定的按鈕。|  
|[CToolBarCtrl::HitTest](#hittest)|決定工具列控制項中的點所在位置。|  
|[CToolBarCtrl::Indeterminate](#indeterminate)|設定或清除指定的按鈕，在工具列控制項中的不定 （灰色） 狀態。|  
|[CToolBarCtrl::InsertButton](#insertbutton)|在工具列控制項中插入按鈕。|  
|[CToolBarCtrl::InsertMarkHitTest](#insertmarkhittest)|擷取在工具列中的點插入標記資訊。|  
|[CToolBarCtrl::IsButtonChecked](#isbuttonchecked)|會指示是否已選取工具列控制項中指定的按鈕。|  
|[CToolBarCtrl::IsButtonEnabled](#isbuttonenabled)|會指示是否已啟用工具列控制項中指定的按鈕。|  
|[CToolBarCtrl::IsButtonHidden](#isbuttonhidden)|會指示是否要隱藏工具列控制項中指定的按鈕。|  
|[CToolBarCtrl::IsButtonHighlighted](#isbuttonhighlighted)|檢查反白顯示狀態的工具列按鈕。|  
|[CToolBarCtrl::IsButtonIndeterminate](#isbuttonindeterminate)|會告知工具列控制項中指定的按鍵的狀態是否為不定 （灰色）。|  
|[CToolBarCtrl::IsButtonPressed](#isbuttonpressed)|會指示是否要按下工具列控制項中指定的按鈕。|  
|[CToolBarCtrl::LoadImages](#loadimages)|將點陣圖載入到工具列控制項的影像清單。|  
|[CToolBarCtrl::MapAccelerator](#mapaccelerator)|工具列按鈕對應的對應字元。|  
|[CToolBarCtrl::MarkButton](#markbutton)|在工具列控制項中設定按鈕的反白顯示狀態。|  
|[CToolBarCtrl::MoveButton](#movebutton)|將按鈕從一個索引移到另一個。|  
|[CToolBarCtrl::PressButton](#pressbutton)|按下或釋放工具列控制項中指定的按鈕。|  
|[CToolBarCtrl::ReplaceBitmap](#replacebitmap)|新的點陣圖，取代目前的工具列控制項中現有的點陣圖。|  
|[CToolBarCtrl::RestoreState](#restorestate)|還原工具列控制項的狀態。|  
|[CToolBarCtrl::SaveState](#savestate)|儲存工具列控制項的狀態。|  
|[CToolBarCtrl::SetAnchorHighlight](#setanchorhighlight)|設定錨點反白顯示的工具列設定。|  
|[CToolBarCtrl::SetBitmapSize](#setbitmapsize)|設定點陣圖的影像加入至 toolbar 控制項的大小。|  
|[CToolBarCtrl::SetButtonInfo](#setbuttoninfo)|在工具列中設定現有的按鈕的資訊。|  
|[CToolBarCtrl::SetButtonSize](#setbuttonsize)|設定要加入至 toolbar 控制項按鈕的大小。|  
|[CToolBarCtrl::SetButtonStructSize](#setbuttonstructsize)|指定的大小`TBBUTTON`結構。|  
|[CToolBarCtrl::SetButtonWidth](#setbuttonwidth)|設定工具列控制項中的最小和最大按鈕的寬度。|  
|[CToolBarCtrl::SetCmdID](#setcmdid)|設定指定的按鈕按下時，傳送至主控視窗的命令識別項。|  
|[CToolBarCtrl::SetColorScheme](#setcolorscheme)|設定目前的工具列控制項的色彩配置。|  
|[CToolBarCtrl::SetDisabledImageList](#setdisabledimagelist)|設定工具列控制項將會使用影像清單來顯示停用按鈕。|  
|[CToolBarCtrl::SetDrawTextFlags](#setdrawtextflags)|Win32 函式中設定的旗標[DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)，用來繪製在指定的矩形，根據旗標的設定方式格式化文字。|  
|[CToolBarCtrl::SetExtendedStyle](#setextendedstyle)|設定工具列控制項的延伸的樣式。|  
|[CToolBarCtrl::SetHotImageList](#sethotimagelist)|設定工具列控制項用來顯示 「 熱門 」 按鈕的影像清單。|  
|[CToolBarCtrl::SetHotItem](#sethotitem)|在工具列中設定的作用的項目。|  
|[CToolBarCtrl::SetImageList](#setimagelist)|設定影像清單工具列將用來顯示按鈕為預設狀態中。|  
|[CToolBarCtrl::SetIndent](#setindent)|在工具列控制項中設定第一個按鈕的縮排。|  
|[CToolBarCtrl::SetInsertMark](#setinsertmark)|設定目前的插入標記的工具列。|  
|[CToolBarCtrl::SetInsertMarkColor](#setinsertmarkcolor)|設定用來繪製工具列插入標記的色彩。|  
|[CToolBarCtrl::SetMaxTextRows](#setmaxtextrows)|設定顯示的工具列按鈕的文字資料列的數目上限。|  
|[CToolBarCtrl::SetMetrics](#setmetrics)|設定工具列控制項的度量。|  
|[CToolBarCtrl::SetOwner](#setowner)|設定工具列控制項中接收通知訊息的視窗。|  
|[CToolBarCtrl::SetPadding](#setpadding)|設定目前的工具列控制項的水平和垂直邊框距離。|  
|[CToolBarCtrl::SetPressedImageList](#setpressedimagelist)|設定目前的工具列控制項用來代表按下狀態的按鈕影像清單。|  
|[CToolBarCtrl::SetRows](#setrows)|設定顯示在工具列中按鈕的資料列數目。|  
|[CToolBarCtrl::SetState](#setstate)|在工具列控制項中設定指定的按鈕的狀態。|  
|[CToolBarCtrl::SetStyle](#setstyle)|設定工具列控制項的樣式。|  
|[CToolBarCtrl::SetToolTips](#settooltips)|將工具提示控制項與工具列控制項產生關聯。|  
|[CToolBarCtrl::SetWindowTheme](#setwindowtheme)|設定工具列控制項的視覺化樣式。|  
  
## <a name="remarks"></a>備註  
 這個控制項 (並因此`CToolBarCtrl`類別) 僅適用於執行 Windows 95/98 和 Windows NT 版本 3.51 下的程式和更新版本。  
  
 Windows 工具列通用控制項是包含一或多個按鈕的矩形的子視窗。 這些按鈕可以顯示點陣圖影像、 字串或兩者。 當使用者選擇按鈕時，它會傳送至工具列的擁有者視窗的命令訊息。 通常，工具列中的按鈕對應於應用程式 功能表中的項目它們提供更直接的方式，讓使用者存取應用程式的命令。  
  
 `CToolBarCtrl`物件包含數個重要的內部資料結構︰ 一份按鈕影像的點陣圖或影像清單、 清單的按鈕標籤字串和一份`TBBUTTON`結構關聯一個影像，及/或字串取代為所在位置的樣式，而狀態，以及命令按鈕的 ID。 每種資料結構的項目都有以零為起始的索引。 您可以使用之前`CToolBarCtrl`物件時，您必須設定這些資料結構。 字串清單只可以用於按鈕標籤。您無法從工具列擷取字串。  
  
 若要使用 `CToolBarCtrl` 物件，您通常會執行下列步驟：  
  
1.  建構 `CToolBarCtrl` 物件。  
  
2.  呼叫[建立](#create)建立 Windows 工具列通用控制項並將其附加至`CToolBarCtrl`物件。 使用樣式，例如指出工具列的樣式**TBSTYLE_TRANSPARENT**透明工具列或**TBSTYLE_DROPDOWN**支援樣式下拉式按鈕的工具列。  
  
3.  找出您要如何顯示在工具列上的按鈕︰  
  
    -   若要使用按鈕點陣圖影像，將按鈕點陣圖加入工具列藉由呼叫[AddBitmap](#addbitmap)。  
  
    -   若要使用按鈕在影像清單中顯示的影像，請呼叫，影像清單指定[SetImageList](#setimagelist)， [SetHotImageList](#sethotimagelist)，或[SetDisabledImageList](#setdisabledimagelist)。  
  
    -   若要使用字串標籤 按鈕，將字串加入至工具列藉由呼叫[AddString](#addstring)及/或[AddStrings](#addstrings)。  
  
4.  新增至工具列按鈕的結構，藉由呼叫[AddButtons](#addbuttons)。  
  
5.  如果您想在不是主控視窗的工具列按鈕的工具提示`CFrameWnd`，您需要處理**TTN_NEEDTEXT**工具列的主控視窗中的訊息中所述[處理工具提示通知](../../mfc/handling-tool-tip-notifications.md)。 如果父視窗的工具列衍生自`CFrameWnd`，而不需要任何額外的介入，從您會顯示工具提示，因為`CFrameWnd`提供的預設處理常式。  
  
6.  如果您想讓使用者可以自訂工具列，處理是主控視窗中的自訂通知訊息中所述[處理自訂告知](../../mfc/handling-customization-notifications.md)。  
  
 您可以使用[SaveState](#savestate)工具列控制項的目前狀態儲存在登錄中與[RestoreState](#restorestate)以還原先前儲存在登錄中的資訊為基礎的狀態。 除了儲存工具列狀態之間的應用程式使用，應用程式通常儲存狀態之前使用者開始自訂工具列，以防使用者稍後想要將工具列還原為其原始狀態。  
  
## <a name="support-for-internet-explorer-version-40-and-later"></a>Internet Explorer 版本 4.0 及更新版本的支援  
 若要支援功能導入在 Internet Explorer 版本 4.0 及更新版本，MFC 使用工具列控制項提供影像清單的支援和透明及一般樣式。  
  
 透明工具列可讓工具列底下的用戶端，透過顯示。 若要建立透明工具列，同時使用**TBSTYLE_FLAT**和**TBSTYLE_TRANSPARENT**樣式。 透明工具列功能的熱追蹤。也就是說，當滑鼠指標移工具列上的作用中的按鈕，按鈕的外觀會變更。 建立工具列只**TBSTYLE_FLAT**樣式將包含不透明的按鈕。  
  
 影像清單的支援可讓控制項更大彈性的預設行為，作用中影像，且已停用映像。 使用[GetImageList](#getimagelist)， [GetHotImageList](#gethotimagelist)，和[GetDisabledImageList](#getdisabledimagelist)與操作根據其狀態影像的透明工具列︰  
  
 如需有關使用`CToolBarCtrl`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CToolBarCtrl](../../mfc/using-ctoolbarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolBarCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="a-nameaddbitmapa--ctoolbarctrladdbitmap"></a><a name="addbitmap"></a>CToolBarCtrl::AddBitmap  
 將一或多個按鈕的影像加入至按鈕影像儲存在工具列控制項的清單。  
  
```  
int AddBitmap(
    int nNumButtons,  
    UINT nBitmapID);

 
int AddBitmap(
    int nNumButtons,  
    CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>參數  
 `nNumButtons`  
 按鈕影像的點陣圖中的數目。  
  
 `nBitmapID`  
 包含按鈕的映像或映像以新增點陣圖資源識別元。  
  
 `pBitmap`  
 指標`CBitmap`包含按鈕的映像或映像以新增的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功，第一個新影像的以零起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
 您可以使用 Windows API [CreateMappedBitmap](http://msdn.microsoft.com/library/windows/desktop/bb787467)對應之前加入至工具列點陣圖的色彩。 如果您將指標傳遞至**CBitMap**物件時，您必須確定，點陣圖不會損毀之前終結工具列。  
  
##  <a name="a-nameaddbuttonsa--ctoolbarctrladdbuttons"></a><a name="addbuttons"></a>CToolBarCtrl::AddButtons  
 將一或多個按鈕加入至 toolbar 控制項。  
  
```  
BOOL AddButtons(
    int nNumButtons,  
    LPTBBUTTON lpButtons);
```  
  
### <a name="parameters"></a>參數  
 `nNumButtons`  
 若要新增的按鈕數目。  
  
 `lpButtons`  
 陣列中的位址`TBBUTTON`結構，其中包含要加入按鈕的相關資訊。 必須有相同數目的陣列中的項目，以所指定的按鈕`nNumButtons`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 `lpButtons`指標會指向陣列`TBBUTTON`結構。 每個`TBBUTTON`結構將按鈕加入按鈕的樣式、 影像和/或命令 ID 的字串，狀態和使用者自訂資料與相關聯︰  
  
 `typedef struct _TBBUTTON {`  
  
 `int iBitmap;// zero-based index of button image`  
  
 `int idCommand;  // command to be sent when button pressed`  
  
 `BYTE fsState;   // button state--see below`  
  
 `BYTE fsStyle;   // button style--see below`  
  
 `DWORD dwData;   // application-defined value`  
  
 `int iString;// zero-based index of button label string`  
  
 `} TBBUTTON;`  
  
 成員如下所示︰  
  
 **iBitmap**  
 按鈕影像，-1，如果沒有這個按鈕影像的以零為起始的索引。  
  
 **idCommand**  
 命令與按鈕關聯的識別項。 此識別碼會傳送**WM_COMMAND**則選擇該按鈕時，訊息。 如果**fsStyle**成員都有`TBSTYLE_SEP`值，這個成員必須為零。  
  
 **fsState**  
 按鈕狀態旗標。 它可以是下列值的組合︰  
  
- `TBSTATE_CHECKED`按鈕的**TBSTYLE_CHECKED**樣式，按下。  
  
- `TBSTATE_ENABLED`按鈕接受使用者輸入。 沒有此狀態的按鈕不接受使用者輸入，並呈現灰色。  
  
- `TBSTATE_HIDDEN`按鈕看不到，而無法接收使用者輸入。  
  
- `TBSTATE_INDETERMINATE`按鈕會呈現灰色。  
  
- `TBSTATE_PRESSED`按下按鈕。  
  
- `TBSTATE_WRAP`換行符號後面的按鈕。 按鈕也必須`TBSTATE_ENABLED`狀態。  
  
 **fsStyle**  
 按鈕樣式。 它可以是下列值的組合︰  
  
- `TBSTYLE_BUTTON`建立標準按鈕。  
  
- `TBSTYLE_CHECK`建立的按鈕會在每次使用者按一下它的已按下和未按下狀態之間切換。 處於已按下狀態時，按鈕會有不同的背景色彩。  
  
- `TBSTYLE_CHECKGROUP`會建立處於已按下，直到群組中的另一個按鈕按下核取按鈕。  
  
- `TBSTYLE_GROUP`會建立處於已按下，直到群組中的另一個按鈕按下按鈕。  
  
- `TBSTYLE_SEP`建立提供小的缺口按鈕群組之間的分隔符號。 具有此樣式的按鈕不會接收使用者輸入。  
  
 `dwData`  
 使用者定義的資料。  
  
 **iString**  
 要做為按鈕的標籤，-1，如果沒有這個按鈕字串的字串以零為起始的索引。  
  
 映像及/或您提供的索引必須先前已加入至工具列控制項的字串清單使用[AddBitmap](#addbitmap)， [AddString](#addstring)，和/或[AddStrings](#addstrings)。  
  
##  <a name="a-nameaddstringa--ctoolbarctrladdstring"></a><a name="addstring"></a>CToolBarCtrl::AddString  
 加入新的字串，傳遞做為資源識別碼，工具列的內部清單的字串。  
  
```  
int AddString(UINT nStringID);
```  
  
### <a name="parameters"></a>參數  
 *nStringID*  
 若要加入工具列控制項的字串清單的字串資源的資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，加入第一個新的字串以零起始的索引否則為-1。  
  
##  <a name="a-nameaddstringsa--ctoolbarctrladdstrings"></a><a name="addstrings"></a>CToolBarCtrl::AddStrings  
 將可供工具列控制項的字串清單的新字串。  
  
```  
int AddStrings(LPCTSTR lpszStrings);
```  
  
### <a name="parameters"></a>參數  
 *lpszStrings*  
 包含要加入工具列的字串清單的一個或多個 null 結尾字串的緩衝區位址。 最後一個字串必須以兩個 null 字元結束。  
  
### <a name="return-value"></a>傳回值  
 如果成功，加入第一個新的字串以零起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
 緩衝區中的字串必須以 null 字元分隔。 您必須確定的最後一個字串有兩個 null 結束字元。 若要正確地格式化常數字串，您可能寫成︰  
  
 [!code-cpp[NVC_MFCControlLadenDialog #&72;](../../mfc/codesnippet/cpp/ctoolbarctrl-class_1.cpp)]  
  
 或：  
  
 [!code-cpp[NVC_MFCControlLadenDialog #&73;](../../mfc/codesnippet/cpp/ctoolbarctrl-class_2.cpp)]  
  
 您不應該傳遞`CString`物件，這個函式，因為它不可以在一個以上的 null 字元`CString`。  
  
##  <a name="a-nameautosizea--ctoolbarctrlautosize"></a><a name="autosize"></a>CToolBarCtrl::AutoSize  
 調整整個工具列控制項的大小。  
  
```  
void AutoSize();
```  
  
### <a name="remarks"></a>備註  
 父視窗的大小變更時，或在工具列的大小變更 （例如，當您設定的按鈕或點陣圖的大小，或將字串） 時，您應該呼叫此函式。  
  
##  <a name="a-namechangebitmapa--ctoolbarctrlchangebitmap"></a><a name="changebitmap"></a>CToolBarCtrl::ChangeBitmap  
 變更目前的工具列控制項中的按鈕的點陣圖。  
  
```  
BOOL ChangeBitmap(
    int idButton,   
    int iBitmap);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `idButton`|命令識別項會收到新的點陣圖按鈕。|  
|[in] `iBitmap`|目前的工具列控制項影像清單中的影像以零為起始的索引。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 如果此方法成功，則系統會顯示指定的映像中指定的按鈕。  
  
 這個方法會傳送[TB_CHANGEBITMAP](http://msdn.microsoft.com/library/windows/desktop/bb787301)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會變更的點陣圖**檔案儲存**按鈕點陣圖，**有關** 按鈕。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_3.cpp)]  
  
##  <a name="a-namecheckbuttona--ctoolbarctrlcheckbutton"></a><a name="checkbutton"></a>CToolBarCtrl::CheckButton  
 檢查或清除 在工具列控制項中指定的按鈕。  
  
```  
BOOL CheckButton(
    int nID,  
    BOOL bCheck = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 命令按鈕的核取或清除的識別項。  
  
 *bCheck*  
 **TRUE**檢查 按鈕， **FALSE**時清除它。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 當已核取按鈕時，它會顯示已按下。 如果您想要變更多個按鈕的狀態，請考慮呼叫[SetState](#setstate)改。  
  
##  <a name="a-namecommandtoindexa--ctoolbarctrlcommandtoindex"></a><a name="commandtoindex"></a>CToolBarCtrl::CommandToIndex  
 擷取與指定的命令識別項相關聯的按鈕以零為起始的索引。  
  
```  
UINT CommandToIndex(UINT nID) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 命令 ID 的按鈕索引您想要尋找。  
  
### <a name="return-value"></a>傳回值  
 以零為起始的索引按鈕相關聯的命令 id。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecreatea--ctoolbarctrlcreate"></a><a name="create"></a>CToolBarCtrl::Create  
 建立工具列控制項並將它附加`CToolBarCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定工具列控制項的樣式。 工具列永遠必須**WS_CHILD**樣式。 此外，指定 toolbar 樣式和視窗樣式的任意組合，如底下所述**註解**。  
  
 `rect`  
 選擇性地指定工具列控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 `pParentWnd`  
 指定工具列控制項的父視窗。 它不得為**NULL**。  
  
 `nID`  
 指定工具列控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 您建構`CToolBarCtrl`兩個步驟。 首先，呼叫建構函式，並接著呼叫**建立**，其建立工具列控制項，並將它附加`CToolBarCtrl`物件。 將下列視窗樣式套用至 toolbar 控制項。  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
 請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]視窗樣式的說明。  
  
 選擇性地套用[常用的控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775498)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 套用至控制項或按鈕本身的 toolbar 樣式的組合。 本主題會說明樣式[工具列控制項和按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb760439)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 若要使用延伸的工具列的樣式，呼叫[SetExtendedStyle](#setextendedstyle)呼叫之後**建立**。 若要建立具有延伸的視窗樣式的工具列，呼叫[CToolBarCtrl::CreateEx](#createex)而不是**建立**。  
  
 工具列控制項將會自動設定的大小和位置的 [工具列] 視窗。 高度為基礎的工具列中按鈕的高度。 寬度是與父視窗的用戶端區域的寬度相同。 `CCS_TOP`和`CCS_BOTTOM`樣式會判斷是否沿著頂端或底部的用戶端區域位於工具列。 根據預設，工具列上有`CCS_TOP`樣式。  
  
##  <a name="a-namecreateexa--ctoolbarctrlcreateex"></a><a name="createex"></a>CToolBarCtrl::CreateEx  
 建立控制項 （子視窗），並將它與相關聯`CToolBarCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定工具列控制項的樣式。 工具列永遠必須**WS_CHILD**樣式。 此外，您可以指定 toolbar 樣式和視窗樣式的任意組合中所述**備註**區段[建立](#create)。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立、 用戶端座標中的視窗的`pParentWnd`。  
  
 `pParentWnd`  
 是控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，指定 Windows 延伸的樣式序言**WS_EX_**。 **CreateEx**建立具有所指定的延伸視窗樣式控制項`dwExStyle`。 設定擴充特定控制項使用的樣式[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`設為這類樣式**WS_EX_CONTEXTHELP**，但使用`SetExtendedStyle`設為這類樣式**TBSTYLE_EX_DRAWDDARROWS**。 如需詳細資訊，請參閱說明中的樣式[工具列延伸樣式](http://msdn.microsoft.com/library/windows/desktop/bb760430)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namectoolbarctrla--ctoolbarctrlctoolbarctrl"></a><a name="ctoolbarctrl"></a>CToolBarCtrl::CToolBarCtrl  
 建構 `CToolBarCtrl` 物件。  
  
```  
CToolBarCtrl();
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫[建立](#create)讓工具列成為可用。  
  
##  <a name="a-namecustomizea--ctoolbarctrlcustomize"></a><a name="customize"></a>CToolBarCtrl::Customize  
 顯示 [自訂工具列] 對話方塊。  
  
```  
void Customize();
```  
  
### <a name="remarks"></a>備註  
 這個對話方塊可讓使用者自訂工具列加入和刪除按鈕。 若要支援自訂，工具列的父視窗必須處理的自訂通知訊息中所述[處理自訂告知](../../mfc/handling-customization-notifications.md)。 將工具列必須也已經建立與`CCS_ADJUSTABLE`樣式中所述[CToolBarCtrl::Create](#create)。  
  
 如需詳細資訊，請參閱知識庫文件 Q241850: PRB︰ 呼叫 CToolBarCtrl::Customize 不會保留自訂的對話方塊中顯示。  
  
##  <a name="a-namedeletebuttona--ctoolbarctrldeletebutton"></a><a name="deletebutton"></a>CToolBarCtrl::DeleteButton  
 刪除工具列控制項中的按鈕。  
  
```  
BOOL DeleteButton(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 [刪除] 按鈕以零為起始索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenablebuttona--ctoolbarctrlenablebutton"></a><a name="enablebutton"></a>CToolBarCtrl::EnableButton  
 啟用或停用工具列控制項中指定的按鈕。  
  
```  
BOOL EnableButton(
    int nID,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 若要啟用或停用按鈕的命令識別碼。  
  
 `bEnable`  
 **TRUE**啟用該按鈕。**FALSE**來停用按鈕。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 在已啟用 按鈕，它可以按下並檢查。 如果您想要變更多個按鈕的狀態，請考慮呼叫[SetState](#setstate)改。  
  
##  <a name="a-namegetanchorhighlighta--ctoolbarctrlgetanchorhighlight"></a><a name="getanchorhighlight"></a>CToolBarCtrl::GetAnchorHighlight  
 擷取錨點反白顯示的工具列設定。  
  
```  
BOOL GetAnchorHighlight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果是非零值，錨點反白顯示已啟用。 如果為零，會停用反白顯示錨點。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETANCHORHIGHLIGHT](http://msdn.microsoft.com/library/windows/desktop/bb787313)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetbitmapa--ctoolbarctrlgetbitmap"></a><a name="getbitmap"></a>CToolBarCtrl::GetBitmap  
 擷取點陣圖中的工具列按鈕相關聯的索引。  
  
```  
int GetBitmap(int nID) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 命令按鈕點陣圖索引是要擷取的識別碼。  
  
### <a name="return-value"></a>傳回值  
 傳回的點陣圖，如果成功，否則為零的索引。  
  
### <a name="remarks"></a>備註  
 實作功能[TB_GETBITMAP](http://msdn.microsoft.com/library/windows/desktop/bb787315)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetbitmapflagsa--ctoolbarctrlgetbitmapflags"></a><a name="getbitmapflags"></a>CToolBarCtrl::GetBitmapFlags  
 從工具列中擷取的點陣圖旗標。  
  
```  
UINT GetBitmapFlags() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **UINT**具有**TBBF_LARGE**如果顯示可支援大型的工具列點陣圖，否則清除設定旗標。  
  
### <a name="remarks"></a>備註  
 您應該呼叫它之後建立的工具列，但之前加入至工具列點陣圖。 傳回值表示是否顯示是否支援大型點陣圖。 若顯示器支援大型點陣圖，而且如果您選擇使用它們，請呼叫[SetBitmapSize](#setbitmapsize)和[SetButtonSize](#setbuttonsize)之前加入程式大型點陣圖，請使用[AddBitmap](#addbitmap)。  
  
##  <a name="a-namegetbuttona--ctoolbarctrlgetbutton"></a><a name="getbutton"></a>CToolBarCtrl::GetButton  
 擷取指定的按鈕，在工具列控制項中的相關資訊。  
  
```  
BOOL GetButton(
    int nIndex,  
    LPTBBUTTON lpButton) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取資訊的按鈕以零為起始索引。  
  
 `lpButton`  
 位址`TBBUTTON`會收到一份按鈕資訊的結構。 請參閱[CToolBarCtrl::AddButtons](#addbuttons)有關`TBBUTTON`結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="a-namegetbuttoncounta--ctoolbarctrlgetbuttoncount"></a><a name="getbuttoncount"></a>CToolBarCtrl::GetButtonCount  
 擷取目前在工具列控制項中的按鈕的計數。  
  
```  
int GetButtonCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 按鈕的計數。  
  
##  <a name="a-namegetbuttoninfoa--ctoolbarctrlgetbuttoninfo"></a><a name="getbuttoninfo"></a>CToolBarCtrl::GetButtonInfo  
 擷取在工具列中按鈕的資訊。  
  
```  
int GetButtonInfo(
    int nID,  
    TBBUTTONINFO* ptbbi) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 按鈕的識別項。  
  
 `ptbbi`  
 指標[TBBUTTONINFO](http://msdn.microsoft.com/library/windows/desktop/bb760478)接收按鈕資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則 按鈕的以零起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETBUTTONINFO](http://msdn.microsoft.com/library/windows/desktop/bb787321)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetbuttonsizea--ctoolbarctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CToolBarCtrl::GetButtonSize  
 取得工具列按鈕的大小。  
  
```  
DWORD GetButtonSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`DWORD`值，分別包含在 LOWORD 和 HIWORD，寬度和高度值。  
  
##  <a name="a-namegetbuttontexta--ctoolbarctrlgetbuttontext"></a><a name="getbuttontext"></a>CToolBarCtrl::GetButtonText  
 擷取指定之目前工具列控制項上按鈕的顯示文字。  
  
```  
CString GetButtonText(int idButton) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `idButton`|擷取其顯示文字的按鈕識別項。|  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/using-cstring.md) ，其中包含指定的按鈕的顯示文字。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TB_GETBUTTONTEXT](http://msdn.microsoft.com/library/windows/desktop/bb787325)訊息，說明 Windows SDK 中。  
  
##  <a name="a-namegetcolorschemea--ctoolbarctrlgetcolorscheme"></a><a name="getcolorscheme"></a>CToolBarCtrl::GetColorScheme  
 擷取目前的工具列控制項的色彩配置。  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpColorScheme) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸出] `lpColorScheme`|指標[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)接收色彩配置資訊的結構。 此方法傳回時，結構描述的醒目提示色彩和工具列控制項的陰影色彩。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TB_GETCOLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb787327)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdisabledimagelista--ctoolbarctrlgetdisabledimagelist"></a><a name="getdisabledimagelist"></a>CToolBarCtrl::GetDisabledImageList  
 擷取映像清單工具列控制項用來顯示停用按鈕。  
  
```  
CImageList* GetDisabledImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件，或**NULL**如果沒有停用映像清單設定。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETDISABLEDIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787329)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 實作 MFC`GetDisabledImageList`使用`CImageList`物件，其中包含工具列控制項的按鈕映像，而不是影像清單的控制代碼。  
  
##  <a name="a-namegetdroptargeta--ctoolbarctrlgetdroptarget"></a><a name="getdroptarget"></a>CToolBarCtrl::GetDropTarget  
 擷取[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)工具列控制項的介面。  
  
```  
HRESULT GetDropTarget(IDropTarget** ppDropTarget) const;  
```  
  
### <a name="parameters"></a>參數  
 `ppDropTarget`  
 指標[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)介面指標。 如果發生錯誤， **NULL**指標放在這個位址。  
  
### <a name="return-value"></a>傳回值  
 傳回`HRESULT`值，指出成功或失敗的作業。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787343)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetextendedstylea--ctoolbarctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CToolBarCtrl::GetExtendedStyle  
 擷取在工具列控制項的延伸的樣式。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A `DWORD` ，代表目前使用工具列控制項中的延伸的樣式。 如需樣式的清單，請參閱[工具列延伸樣式](http://msdn.microsoft.com/library/windows/desktop/bb760430)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb787331)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegethotimagelista--ctoolbarctrlgethotimagelist"></a><a name="gethotimagelist"></a>CToolBarCtrl::GetHotImageList  
 擷取映像清單工具列控制項用來顯示 「 熱門 」 按鈕。 當滑鼠指標位於其上方時，會反白顯示作用中的按鈕。  
  
```  
CImageList* GetHotImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件，或**NULL**如果沒有停用映像清單設定。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETHOTIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787334)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 當滑鼠指標位於其上方時，會反白顯示作用中的按鈕。  
  
##  <a name="a-namegethotitema--ctoolbarctrlgethotitem"></a><a name="gethotitem"></a>CToolBarCtrl::GetHotItem  
 擷取在工具列中作用的項目索引。  
  
```  
int GetHotItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在工具列中作用的項目以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETHOTITEM](http://msdn.microsoft.com/library/windows/desktop/bb787336)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetimagelista--ctoolbarctrlgetimagelist"></a><a name="getimagelist"></a>CToolBarCtrl::GetImageList  
 擷取映像清單工具列控制項用來顯示按鈕為預設狀態。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件，或**NULL**如果沒有映像清單設定。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787337)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetinsertmarka--ctoolbarctrlgetinsertmark"></a><a name="getinsertmark"></a>CToolBarCtrl::GetInsertMark  
 擷取目前的插入標記的工具列。  
  
```  
void GetInsertMark(TBINSERTMARK* ptbim) const;  
```  
  
### <a name="parameters"></a>參數  
 `ptbim`  
 指標[TBINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb760480)接收插入標記的結構。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb787338)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetinsertmarkcolora--ctoolbarctrlgetinsertmarkcolor"></a><a name="getinsertmarkcolor"></a>CToolBarCtrl::GetInsertMarkColor  
 擷取用來繪製工具列插入標記的色彩。  
  
```  
COLORREF GetInsertMarkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，其中包含目前的插入標記色彩。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb787339)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetitemrecta--ctoolbarctrlgetitemrect"></a><a name="getitemrect"></a>CToolBarCtrl::GetItemRect  
 擷取控制項中的工具列按鈕的周框矩形。  
  
```  
BOOL GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取資訊的按鈕以零為起始索引。  
  
 `lpRect`  
 位址[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)接收週框的座標的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此函式不會擷取其狀態設定為按鈕，這個周框`TBSTATE_HIDDEN`。  
  
##  <a name="a-namegetmaxsizea--ctoolbarctrlgetmaxsize"></a><a name="getmaxsize"></a>CToolBarCtrl::GetMaxSize  
 擷取所有可見的按鈕和工具列中的分隔線的總大小。  
  
```  
BOOL GetMaxSize(LPSIZE pSize) const;  
```  
  
### <a name="parameters"></a>參數  
 `pSize`  
 指標[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)接收項目的大小的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETMAXSIZE](http://msdn.microsoft.com/library/windows/desktop/bb787341)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetmaxtextrowsa--ctoolbarctrlgetmaxtextrows"></a><a name="getmaxtextrows"></a>CToolBarCtrl::GetMaxTextRows  
 擷取工具列按鈕上顯示的文字資料列的數目上限。  
  
```  
int GetMaxTextRows() const;  
```  
  
### <a name="return-value"></a>傳回值  
 工具列按鈕上顯示的文字資料列的數目上限。  
  
##  <a name="a-namegetmetricsa--ctoolbarctrlgetmetrics"></a><a name="getmetrics"></a>CToolBarCtrl::GetMetrics  
 擷取的度量`CToolBarCtrl`物件。  
  
```  
void GetMetrics(LPTBMETRICS ptbm) const;  
```  
  
### <a name="parameters"></a>參數  
 `ptbm`  
 指標[TBMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb760482)結構`CToolBarCtrl`物件。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[TB_GETMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb787342)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetpaddinga--ctoolbarctrlgetpadding"></a><a name="getpadding"></a>CToolBarCtrl::GetPadding  
 擷取目前的工具列控制項的水平和垂直邊框距離。  
  
```  
BOOL GetPadding(
    int* pnHorzPadding,   
    int* pnVertPadding) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸出] `pnHorzPadding`|整數，接收水平工具列控制項的邊框距離，單位為像素。|  
|[輸出] `pnVertPadding`|整數，接收工具列控制項的垂直邊框距離，單位為像素。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TB_GETPADDING](http://msdn.microsoft.com/library/windows/desktop/bb787344)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetpressedimagelista--ctoolbarctrlgetpressedimagelist"></a><a name="getpressedimagelist"></a>CToolBarCtrl::GetPressedImageList  
 擷取映像清單目前的工具列控制項用來代表按下狀態的按鈕。  
  
```  
CImageList* GetPressedImageList();
```  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md) ，其中包含目前的控制項影像清單或`NULL`如果沒有這類映像清單設定。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TB_GETPRESSEDIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787345)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetrecta--ctoolbarctrlgetrect"></a><a name="getrect"></a>CToolBarCtrl::GetRect  
 擷取指定的工具列按鈕，這個周框。  
  
```  
BOOL GetRect(
    int nID,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 按鈕的識別項。  
  
 `lpRect`  
 指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收週框矩形資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果成功，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb787346)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetrowsa--ctoolbarctrlgetrows"></a><a name="getrows"></a>CToolBarCtrl::GetRows  
 擷取資料列的目前顯示的工具列控制項的按鈕的數目。  
  
```  
int GetRows() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前顯示在工具列上的按鈕的資料列數目。  
  
### <a name="remarks"></a>備註  
 請注意，資料列數目一律一個工具列所建立，除非`TBSTYLE_WRAPABLE`樣式。  
  
##  <a name="a-namegetstatea--ctoolbarctrlgetstate"></a><a name="getstate"></a>CToolBarCtrl::GetState  
 擷取指定的按鈕，在工具列控制項中，例如它、 按下，是否啟用檢查狀態相關資訊。  
  
```  
int GetState(int nID) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 要擷取資訊的按鈕命令識別項。  
  
### <a name="return-value"></a>傳回值  
 如果成功時，按鈕狀態資訊或者-1，否則為。 按鈕狀態資訊可以是所列的值的組合[CToolBarCtrl::AddButtons](#addbuttons)。  
  
### <a name="remarks"></a>備註  
 此函式是特別有用，如果您想要擷取一個以上的按鈕狀態。 若要只擷取其中一種狀態，請使用下列成員函式的其中一個︰ [IsButtonEnabled](#isbuttonenabled)， [IsButtonChecked](#isbuttonchecked)， [IsButtonPressed](#isbuttonpressed)， [IsButtonHidden](#isbuttonhidden)，或[IsButtonIndeterminate](#isbuttonindeterminate)。 不過，`GetState`成員函式是唯一的方法，可偵測`TBSTATE_WRAP`按鈕的狀態。  
  
##  <a name="a-namegetstringa--ctoolbarctrlgetstring"></a><a name="getstring"></a>CToolBarCtrl::GetString  
 擷取工具列字串。  
  
```  
int GetString(
    int nString,  
    LPTSTR lpstrString,  
    int cchMaxLen) const;  
  
int GetString(
    int nString,  
    CString& str) const;  
```  
  
### <a name="parameters"></a>參數  
 *nString*  
 字串的索引。  
  
 *lpstrString*  
 用來傳回字串緩衝區的指標。  
  
 *cchMaxLen*  
 以位元組為單位的緩衝區長度。  
  
 `str`  
 字串。  
  
### <a name="return-value"></a>傳回值  
 如果成功，字串的長度為-1，如果不是。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_GETSTRING](http://msdn.microsoft.com/library/windows/desktop/bb787349)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetstylea--ctoolbarctrlgetstyle"></a><a name="getstyle"></a>CToolBarCtrl::GetStyle  
 取得目前套用至工具列控制項的樣式。  
  
```  
DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`DWORD`包含的組合[toolbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760439)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettooltipsa--ctoolbarctrlgettooltips"></a><a name="gettooltips"></a>CToolBarCtrl::GetToolTips  
 擷取工具提示控制項的控制代碼，如果有的話與工具列控制項產生關聯。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)與工具列相關聯的物件或**NULL**工具列有沒有相關聯的工具提示控制項。  
  
### <a name="remarks"></a>備註  
 Toolbar 控制項通常會建立並維護它自己的工具提示控制項，因為大部分的程式不需要呼叫此函式。  
  
##  <a name="a-namehittesta--ctoolbarctrlhittest"></a><a name="hittest"></a>CToolBarCtrl::HitTest  
 決定工具列控制項中的點所在位置。  
  
```  
int HitTest(LPPOINT ppt) const;  
```  
  
### <a name="parameters"></a>參數  
 `ppt`  
 指標[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構，包含點擊測試中的 x 座標**x**成員和 y 座標的點擊測試中**y**成員。 座標是相對於工具列的用戶端區域。  
  
### <a name="return-value"></a>傳回值  
 整數值，指出工具列上的點的位置。 如果值為零或正值，則此傳回值是點在於 nonseparator 項目的以零為起始的索引。  
  
 如果傳回值為負數，點不位於按鈕。 傳回值的絕對值是分隔符號項目或最接近的 nonseparator 項目索引。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb787360)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namehidebuttona--ctoolbarctrlhidebutton"></a><a name="hidebutton"></a>CToolBarCtrl::HideButton  
 隱藏或顯示工具列控制項中指定的按鈕。  
  
```  
BOOL HideButton(
    int nID,  
    BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 若要隱藏或顯示的按鈕命令識別項。  
  
 `bHide`  
 **TRUE**若要隱藏按鈕， **FALSE**顯示它。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 如果您想要變更多個按鈕的狀態，請考慮呼叫[SetState](#setstate)改。  
  
##  <a name="a-nameindeterminatea--ctoolbarctrlindeterminate"></a><a name="indeterminate"></a>CToolBarCtrl::Indeterminate  
 設定或清除指定的按鈕，在工具列控制項中的不定狀態。  
  
```  
BOOL Indeterminate(
    int nID,  
    BOOL bIndeterminate = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 不定狀態是要設定或清除的按鈕的命令識別碼。  
  
 *bIndeterminate*  
 **TRUE**不定狀態指定的按鈕，設定**FALSE**時清除它。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 不確定的按鈕會顯示呈現灰色，例如，文書處理器的方式在工具列上的 [粗體] 按鈕看起來時選取的文字包含粗體及一般字元。 如果您想要變更多個按鈕的狀態，請考慮呼叫[SetState](#setstate)改。  
  
##  <a name="a-nameinsertbuttona--ctoolbarctrlinsertbutton"></a><a name="insertbutton"></a>CToolBarCtrl::InsertButton  
 在工具列控制項中插入按鈕。  
  
```  
BOOL InsertButton(
    int nIndex,  
    LPTBBUTTON lpButton);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 按鈕的以零為起始的索引。 此函式插入此按鈕左邊的 [新增] 按鈕。  
  
 `lpButton`  
 位址`TBBUTTON`結構，其中包含要插入按鈕的相關資訊。 請參閱[CToolBarCtrl::AddButtons](#addbuttons)的說明`TBBUTTON`結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 映像及/或您提供的索引必須先前已加入至工具列控制項的字串清單使用[AddBitmap](#addbitmap)， [AddString](#addstring)，和/或[AddStrings](#addstrings)。  
  
##  <a name="a-nameinsertmarkhittesta--ctoolbarctrlinsertmarkhittest"></a><a name="insertmarkhittest"></a>CToolBarCtrl::InsertMarkHitTest  
 擷取在工具列中的點插入標記資訊。  
  
```  
BOOL InsertMarkHitTest(
    LPPOINT ppt,  
    LPTBINSERTMARK ptbim) const;  
```  
  
### <a name="parameters"></a>參數  
 `ppt`  
 指標[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構，包含點擊的測試的座標，相對於用戶端區域的工具列。  
  
 `ptbim`  
 指標[TBINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb760480)接收插入標記資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_INSERTMARKHITTEST](http://msdn.microsoft.com/library/windows/desktop/bb787367)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisbuttoncheckeda--ctoolbarctrlisbuttonchecked"></a><a name="isbuttonchecked"></a>CToolBarCtrl::IsButtonChecked  
 決定是否要檢查在工具列控制項中指定的按鈕。  
  
```  
BOOL IsButtonChecked(int nID) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 在工具列中按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 非零，如果核取按鈕。否則為零。  
  
### <a name="remarks"></a>備註  
 請考慮呼叫[GetState](#getstate)如果您想要擷取多個按鈕的狀態。  
  
##  <a name="a-nameisbuttonenableda--ctoolbarctrlisbuttonenabled"></a><a name="isbuttonenabled"></a>CToolBarCtrl::IsButtonEnabled  
 判斷是否已啟用工具列控制項中指定的按鈕。  
  
```  
BOOL IsButtonEnabled(int nID) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 在工具列中按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已啟用 按鈕。否則為零。  
  
### <a name="remarks"></a>備註  
 請考慮呼叫[GetState](#getstate)如果您想要擷取多個按鈕的狀態。  
  
##  <a name="a-nameisbuttonhiddena--ctoolbarctrlisbuttonhidden"></a><a name="isbuttonhidden"></a>CToolBarCtrl::IsButtonHidden  
 決定是否要隱藏工具列控制項中指定的按鈕。  
  
```  
BOOL IsButtonHidden(int nID) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 在工具列中按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果會隱藏按鈕，為非零否則為零。  
  
### <a name="remarks"></a>備註  
 請考慮呼叫[GetState](#getstate)如果您想要擷取多個按鈕的狀態。  
  
##  <a name="a-nameisbuttonhighlighteda--ctoolbarctrlisbuttonhighlighted"></a><a name="isbuttonhighlighted"></a>CToolBarCtrl::IsButtonHighlighted  
 檢查反白顯示狀態的工具列按鈕。  
  
```  
BOOL IsButtonHighlighted(int nID) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 工具列按鈕的命令 ID。  
  
### <a name="return-value"></a>傳回值  
 如果按鈕會反白顯示的正整數值，0，表示不反白顯示的按鈕或-1 表示錯誤發生。  
  
##  <a name="a-nameisbuttonindeterminatea--ctoolbarctrlisbuttonindeterminate"></a><a name="isbuttonindeterminate"></a>CToolBarCtrl::IsButtonIndeterminate  
 決定工具列控制項中指定的按鈕為不定。  
  
```  
BOOL IsButtonIndeterminate(int nID) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 在工具列中按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 正整數如果按鈕是不確定零; 如果不確定按鈕或-1 表示錯誤發生。  
  
### <a name="remarks"></a>備註  
 不確定顯示按鈕呈現暗灰色，例如，文書處理器的方式在工具列上的 [粗體] 按鈕看起來時選取的文字包含粗體及一般字元。 請考慮呼叫[GetState](#getstate)如果您想要擷取多個按鈕的狀態。  
  
##  <a name="a-nameisbuttonpresseda--ctoolbarctrlisbuttonpressed"></a><a name="isbuttonpressed"></a>CToolBarCtrl::IsButtonPressed  
 決定是否要按下工具列控制項中指定的按鈕。  
  
```  
BOOL IsButtonPressed(int nID) const;  
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 在工具列中按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 非零，如果按下按鈕，否則為零。  
  
### <a name="remarks"></a>備註  
 請考慮呼叫[GetState](#getstate)如果您想要擷取多個按鈕的狀態。  
  
##  <a name="a-nameloadimagesa--ctoolbarctrlloadimages"></a><a name="loadimages"></a>CToolBarCtrl::LoadImages  
 將點陣圖載入到工具列控制項的影像清單。  
  
```  
void LoadImages(
    int iBitmapID,  
    HINSTANCE hinst);
```  
  
### <a name="parameters"></a>參數  
 *iBitmapID*  
 包含要載入的影像之點陣圖的 ID。 若要指定您自己的點陣圖資源，將此參數設定為點陣圖資源的識別碼，並設定`hInst`至**NULL**。 點陣圖資源將影像清單的單一映像。 您可以藉由設定加入標準的系統定義的點陣圖*hinst*至**HINST_COMMCTRL**並將此參數設定為下列識別碼的其中一個︰  
  
|點陣圖的 ID|描述|  
|---------------|-----------------|  
|IDB_HIST_LARGE_COLOR|大總管點陣圖|  
|IDB_HIST_SMALL_COLOR|在較小的總管點陣圖|  
|IDB_STD_LARGE_COLOR|在大型的標準點陣圖|  
|IDB_STD_SMALL_COLOR|在較小的標準點陣圖|  
|IDB_VIEW_LARGE_COLOR|檢視大的點陣圖|  
|IDB_VIEW_SMALL_COLOR|在較小的檢視點陣圖|  
  
 *hinst*  
 呼叫的應用程式的程式執行個體控制代碼。 這個參數可以是**HINST_COMMCTRL**載入標準映像清單。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_LOADIMAGES](http://msdn.microsoft.com/library/windows/desktop/bb787381)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemapacceleratora--ctoolbarctrlmapaccelerator"></a><a name="mapaccelerator"></a>CToolBarCtrl::MapAccelerator  
 工具列按鈕對應的對應字元。  
  
```  
BOOL MapAccelerator(
    TCHAR chAccel,  
    UINT* pIDBtn);
```  
  
### <a name="parameters"></a>參數  
 `chAccel`  
 要對應的對應字元。 此字元是相同按鈕的文字中加上底線的字元。  
  
 *pIDBtn*  
 指標**UINT**接收對應中指定的快速鍵按鈕的命令識別項的`chAccel`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_MAPACCELERATOR](http://msdn.microsoft.com/library/windows/desktop/bb787383)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemarkbuttona--ctoolbarctrlmarkbutton"></a><a name="markbutton"></a>CToolBarCtrl::MarkButton  
 在工具列控制項中設定按鈕的反白顯示狀態。  
  
```  
BOOL MarkButton(
    int nID,  
    BOOL fHighlight = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 按鈕的識別項。  
  
 `fHighlight`  
 指定要設定的反白顯示狀態。 根據預設， **TRUE**。 如果設定為**FALSE**，按鈕設為其預設狀態。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_MARKBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb787385)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemovebuttona--ctoolbarctrlmovebutton"></a><a name="movebutton"></a>CToolBarCtrl::MoveButton  
 將按鈕從一個索引移到另一個。  
  
```  
BOOL MoveButton(
    UINT nOldPos,  
    UINT nNewPos);
```  
  
### <a name="parameters"></a>參數  
 *nOldPos*  
 要移動的按鈕以零為起始的索引。  
  
 *nNewPos*  
 按鈕的目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_MOVEBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb787387)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namepressbuttona--ctoolbarctrlpressbutton"></a><a name="pressbutton"></a>CToolBarCtrl::PressButton  
 按下或釋放工具列控制項中指定的按鈕。  
  
```  
BOOL PressButton(int nID, BOOL bPress = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 命令按鈕的按下或放開的識別項。  
  
 [in] `bPress`  
 `true`按下指定的按鈕。`false`釋放指定的按鈕。 預設值是 `true`。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 如果您想要變更多個按鈕的狀態，請考慮呼叫[SetState](#setstate)改。  
  
 這個方法會傳送[TB_PRESSBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb787389)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namereplacebitmapa--ctoolbarctrlreplacebitmap"></a><a name="replacebitmap"></a>CToolBarCtrl::ReplaceBitmap  
 新的點陣圖，取代目前的工具列控制項中現有的點陣圖。  
  
```  
BOOL ReplaceBitmap(LPTBREPLACEBITMAP pReplaceBitmap);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pReplaceBitmap`|指標[TBREPLACEBITMAP](http://msdn.microsoft.com/library/windows/desktop/bb760484)該結構描述取代點陣圖和新的點陣圖。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TB_REPLACEBITMAP](http://msdn.microsoft.com/library/windows/desktop/bb787391)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例不同的點陣圖，取代標準工具列的點陣圖。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_4.cpp)]  
  
##  <a name="a-namerestorestatea--ctoolbarctrlrestorestate"></a><a name="restorestate"></a>CToolBarCtrl::RestoreState  
 還原工具列控制項的狀態參數所指定的登錄中的位置。  
  
```  
void RestoreState(
    HKEY hKeyRoot,  
    LPCTSTR lpszSubKey,  
    LPCTSTR lpszValueName);
```  
  
### <a name="parameters"></a>參數  
 `hKeyRoot`  
 識別目前開啟的索引鍵，或任何下列預先定義保留的控制代碼值的登錄中︰  
  
- **HKEY_CLASSES_ROOT**  
  
- **HKEY_CURRENT_USER**  
  
- **HKEY_LOCAL_MACHINE**  
  
- **HKEY_USERS**  
  
 `lpszSubKey`  
 指向以 null 結束的字串，其中包含的值所關聯的子機碼名稱。 這個參數可以是 null 或空字串的指標。 如果參數是**NULL**，值會加入至所識別的索引鍵`hKeyRoot`參數。  
  
 `lpszValueName`  
 指向字串，包含要擷取之值的名稱。 如果具有此名稱的值已不存在於索引鍵中，函式會將它加入至索引鍵。  
  
##  <a name="a-namesavestatea--ctoolbarctrlsavestate"></a><a name="savestate"></a>CToolBarCtrl::SaveState  
 將工具列控制項的狀態儲存在登錄中參數所指定的位置中。  
  
```  
void SaveState(
    HKEY hKeyRoot,  
    LPCTSTR lpszSubKey,  
    LPCTSTR lpszValueName);
```  
  
### <a name="parameters"></a>參數  
 `hKeyRoot`  
 識別目前開啟的索引鍵，或任何下列預先定義保留的控制代碼值的登錄中︰  
  
- **HKEY_CLASSES_ROOT**  
  
- **HKEY_CURRENT_USER**  
  
- **HKEY_LOCAL_MACHINE**  
  
- **HKEY_USERS**  
  
 `lpszSubKey`  
 指向以 null 結束的字串，其中包含的值所關聯的子機碼名稱。 這個參數可以是 null 或空字串的指標。 如果參數是**NULL**，值會加入至所識別的索引鍵`hKeyRoot`參數。  
  
 `lpszValueName`  
 指向包含要設定的值名稱的字串。 如果具有此名稱的值已不存在於索引鍵中，函式會將它加入至索引鍵。  
  
##  <a name="a-namesetanchorhighlighta--ctoolbarctrlsetanchorhighlight"></a><a name="setanchorhighlight"></a>CToolBarCtrl::SetAnchorHighlight  
 設定錨點反白顯示的工具列設定。  
  
```  
BOOL SetAnchorHighlight(BOOL fAnchor = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `fAnchor`  
 指定是否錨點反白顯示已啟用或停用。 如果這個值是零，將會啟用反白顯示錨點。 如果此值為零，反白顯示錨點將會停用  
  
### <a name="return-value"></a>傳回值  
 先前的錨點設定。 如果反白顯示已啟用，這個值不是零。 如果未啟用反白顯示，這個值會是零。  
  
### <a name="remarks"></a>備註  
 這個方法會實作的 Win32 訊息的行為[TB_SETANCHORHIGHLIGHT](http://msdn.microsoft.com/library/windows/desktop/bb787396)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetbitmapsizea--ctoolbarctrlsetbitmapsize"></a><a name="setbitmapsize"></a>CToolBarCtrl::SetBitmapSize  
 設定要加入至 toolbar 控制項的實際點陣圖影像的大小。  
  
```  
BOOL SetBitmapSize(CSize size);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 寬度和高度，單位為像素點陣圖影像。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 只會在工具列中加入任何點陣圖之前，必須呼叫此函數。 如果應用程式未明確設定點陣圖大小，則預設為 16 x 15 像素。  
  
##  <a name="a-namesetbuttoninfoa--ctoolbarctrlsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBarCtrl::SetButtonInfo  
 在工具列中設定現有的按鈕的資訊。  
  
```  
BOOL SetButtonInfo(
    int nID,  
    TBBUTTONINFO* ptbbi);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 按鈕的識別項。  
  
 `ptbbi`  
 指標[TBBUTTONINFO](http://msdn.microsoft.com/library/windows/desktop/bb760478)接收按鈕資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 成員函式實作的 Win32 訊息的行為[TB_SETBUTTONINFO](http://msdn.microsoft.com/library/windows/desktop/bb787413)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetbuttonsizea--ctoolbarctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CToolBarCtrl::SetButtonSize  
 在工具列控制項中設定按鈕的大小。  
  
```  
BOOL SetButtonSize(CSize size);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 寬度和高度，單位為像素的按鈕。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 按鈕的大小永遠必須至少為其所包圍的點陣圖大小一樣大。 只會在工具列中加入任何點陣圖之前，必須呼叫此函數。 如果應用程式未明確設定按鈕的大小，則預設為 24 x 22 像素。  
  
### <a name="example"></a>範例  
  請參閱範例[CToolBar::GetToolBarCtrl](../../mfc/reference/ctoolbar-class.md#gettoolbarctrl)。  
  
##  <a name="a-namesetbuttonstructsizea--ctoolbarctrlsetbuttonstructsize"></a><a name="setbuttonstructsize"></a>CToolBarCtrl::SetButtonStructSize  
 指定的大小`TBBUTTON`結構。  
  
```  
void SetButtonStructSize(int nSize);
```  
  
### <a name="parameters"></a>參數  
 `nSize`  
 大小，以位元組為單位的`TBBUTTON`結構。  
  
### <a name="remarks"></a>備註  
 如果您想要儲存在額外資料`TBBUTTON`結構，您無法衍生新的結構從`TBBUTTON`，將成員加入您需要使用，或建立新的結構，其中包含`TBBUTTON`做為其第一個成員的結構。 然後，您會呼叫此函式來得知工具列控制項的新的結構大小。  
  
 請參閱[CToolBarCtrl::AddButtons](#addbuttons)如需有關`TBBUTTON`結構。  
  
##  <a name="a-namesetbuttonwidtha--ctoolbarctrlsetbuttonwidth"></a><a name="setbuttonwidth"></a>CToolBarCtrl::SetButtonWidth  
 設定工具列控制項中的最小和最大按鈕的寬度。  
  
```  
BOOL SetButtonWidth(
    int cxMin,  
    int cxMax);
```  
  
### <a name="parameters"></a>參數  
 `cxMin`  
 最小按鈕寬度，單位為像素。 工具列按鈕絕對不會比這個值。  
  
 *cxMax*  
 最大按鈕寬度，單位為像素。 如果按鈕文字太長，控制項會顯示它的省略符號點。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_SETBUTTONWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb787417)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetcmdida--ctoolbarctrlsetcmdid"></a><a name="setcmdid"></a>CToolBarCtrl::SetCmdID  
 設定指定的按鈕按下時，會傳送至主控視窗的命令識別項。  
  
```  
BOOL SetCmdID(
    int nIndex,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 按鈕的命令 ID 是要設定的以零為起始的索引。  
  
 `nID`  
 若要設定為所選的按鈕命令 ID。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零傳回否則為零。  
  
##  <a name="a-namesetcolorschemea--ctoolbarctrlsetcolorscheme"></a><a name="setcolorscheme"></a>CToolBarCtrl::SetColorScheme  
 設定目前的工具列控制項的色彩配置。  
  
```  
void SetColorScheme(const COLORSCHEME* lpColorScheme);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `lpColorScheme`|指標[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)該結構描述的醒目提示色彩和工具列控制項的陰影色彩。|  
  
### <a name="remarks"></a>備註  
 如果這個方法會有任何作用[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]視覺化佈景主題設定。  
  
 這個方法會傳送[TB_SETCOLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb787421)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定目前的工具列控制項的色彩配置。 程式碼範例將紅色的每個工具 按鈕的左側和頂端邊緣和右邊緣和下邊緣藍色。 當使用者按下按鈕時，會變成藍色按鈕的紅色邊緣和其藍色邊緣會變成紅色。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&3;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_5.cpp)]  
  
##  <a name="a-namesetdisabledimagelista--ctoolbarctrlsetdisabledimagelist"></a><a name="setdisabledimagelist"></a>CToolBarCtrl::SetDisabledImageList  
 設定工具列控制項將會使用影像清單來顯示停用按鈕。  
  
```  
CImageList* SetDisabledImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
 `pImageList`  
 指標`CImageList`物件，其中包含工具列控制項來顯示停用按鈕影像所使用的映像。  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)以前使用工具列控制項來顯示停用按鈕影像的物件。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_SETDISABLEDIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787423)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 實作 MFC`SetDisabledImageList`使用`CImageList`物件，其中包含工具列控制項的已停用的按鈕的影像，而不是影像清單的控制代碼。  
  
##  <a name="a-namesetdrawtextflagsa--ctoolbarctrlsetdrawtextflags"></a><a name="setdrawtextflags"></a>CToolBarCtrl::SetDrawTextFlags  
 Win32 函式中設定的旗標[DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)，用來繪製在指定的矩形，根據旗標的設定方式格式化文字。  
  
```  
DWORD SetDrawTextFlags(
    DWORD dwMask,  
    DWORD dwDTFlags);
```  
  
### <a name="parameters"></a>參數  
 `dwMask`  
 一或多個 Win32 函式中指定的 DT_ 旗標的組合[DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)，表示中的位元`dwDTFlags`繪製文字時使用。  
  
 `dwDTFlags`  
 一或多個 Win32 函式中指定的 DT_ 旗標的組合`DrawText`，指示如何繪製按鈕文字。 這個值會傳遞至`DrawText`繪製按鈕的文字時。  
  
### <a name="return-value"></a>傳回值  
 A`DWORD`包含先前的文字繪製旗標。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_SETDRAWTEXTFLAGS](http://msdn.microsoft.com/library/windows/desktop/bb787425)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 此成員函式的 Win32 函式中設定的旗標`DrawText`，以便在指定的矩形，根據旗標的設定方式格式化繪製文字。  
  
##  <a name="a-namesetextendedstylea--ctoolbarctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CToolBarCtrl::SetExtendedStyle  
 設定工具列控制項的延伸的樣式。  
  
```  
DWORD SetExtendedStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 值，指定新的延伸的樣式。 這個參數可以是工具列的擴充樣式的組合。  
  
### <a name="return-value"></a>傳回值  
 A `DWORD` ，代表上一個延伸樣式。 如需樣式的清單，請參閱[工具列延伸樣式](http://msdn.microsoft.com/library/windows/desktop/bb760430)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb787427)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesethotimagelista--ctoolbarctrlsethotimagelist"></a><a name="sethotimagelist"></a>CToolBarCtrl::SetHotImageList  
 設定工具列控制項用來顯示 「 熱門 」 按鈕的影像清單。  
  
```  
CImageList* SetHotImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
 `pImageList`  
 指標`CImageList`物件，其中包含要供工具列控制項來顯示作用中的按鈕影像的影像。  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)以前使用工具列控制項來顯示作用中的按鈕影像的物件。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_SETHOTIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787429)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 實作 MFC`SetHotImageList`使用`CImageList`物件，其中包含工具列控制項的作用中的按鈕映像，而不是影像清單的控制代碼。 當指標位於其上方，作用中的按鈕會反白顯示。  
  
##  <a name="a-namesethotitema--ctoolbarctrlsethotitem"></a><a name="sethotitem"></a>CToolBarCtrl::SetHotItem  
 在工具列中設定的作用的項目。  
  
```  
int SetHotItem(int nHot);
```  
  
### <a name="parameters"></a>參數  
 *nHot*  
 將成為作用的項目以零為起始的索引編號。 如果此值為-1，項目都不會作用。  
  
### <a name="return-value"></a>傳回值  
 上一個作用的項目，則為-1 時沒有作用的項目索引。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_SETHOTITEM](http://msdn.microsoft.com/library/windows/desktop/bb787431)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetimagelista--ctoolbarctrlsetimagelist"></a><a name="setimagelist"></a>CToolBarCtrl::SetImageList  
 設定影像清單工具列將用來顯示按鈕為預設狀態中。  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
 `pImageList`  
 指標`CImageList`物件，其中包含可用來透過 toolbar 控制項，其預設狀態顯示按鈕影像的影像。  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)以前使用工具列控制項來顯示按鈕影像預設狀態中的物件。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787433)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 實作 MFC`SetImageList`使用`CImageList`物件，其中包含工具列控制項的按鈕映像，而不是影像清單的控制代碼。  
  
##  <a name="a-namesetindenta--ctoolbarctrlsetindent"></a><a name="setindent"></a>CToolBarCtrl::SetIndent  
 在工具列控制項中設定第一個按鈕的縮排。  
  
```  
BOOL SetIndent(int iIndent);
```  
  
### <a name="parameters"></a>參數  
 *iIndent*  
 指定像素為單位的縮排 的值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="a-namesetinsertmarka--ctoolbarctrlsetinsertmark"></a><a name="setinsertmark"></a>CToolBarCtrl::SetInsertMark  
 設定目前的插入標記的工具列。  
  
```  
void SetInsertMark(TBINSERTMARK* ptbim);
```  
  
### <a name="parameters"></a>參數  
 `ptbim`  
 指標[TBINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb760480)結構，其中包含插入標記。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_SETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb787437)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetinsertmarkcolora--ctoolbarctrlsetinsertmarkcolor"></a><a name="setinsertmarkcolor"></a>CToolBarCtrl::SetInsertMarkColor  
 設定用來繪製工具列插入標記的色彩。  
  
```  
COLORREF SetInsertMarkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>參數  
 `clrNew`  
 A **COLORREF**值，其中包含新的插入標記色彩。  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**包含前一個插入標記色彩值。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TB_SETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb787439)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetmaxtextrowsa--ctoolbarctrlsetmaxtextrows"></a><a name="setmaxtextrows"></a>CToolBarCtrl::SetMaxTextRows  
 設定顯示的工具列按鈕的文字資料列的數目上限。  
  
```  
BOOL SetMaxTextRows(int iMaxRows);
```  
  
### <a name="parameters"></a>參數  
 *iMaxRows*  
 若要設定的資料列的數目上限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="a-namesetmetricsa--ctoolbarctrlsetmetrics"></a><a name="setmetrics"></a>CToolBarCtrl::SetMetrics  
 設定度量的`CToolBarCtrl`物件。  
  
```  
void SetMetrics(LPTBMETRICS ptbm);
```  
  
### <a name="parameters"></a>參數  
 `ptbm`  
 指標[TBMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb760482)結構`CToolBarCtrl`物件。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[TB_SETMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb787446)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetownera--ctoolbarctrlsetowner"></a><a name="setowner"></a>CToolBarCtrl::SetOwner  
 設定工具列控制項中的主控視窗。  
  
```  
void SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指標`CWnd`或`CWnd`-衍生物件，將會在工具列控制項的新擁有者視窗。  
  
### <a name="remarks"></a>備註  
 主控視窗是從工具列中接收通知的視窗。  
  
##  <a name="a-namesetpaddinga--ctoolbarctrlsetpadding"></a><a name="setpadding"></a>CToolBarCtrl::SetPadding  
 設定目前的工具列控制項的水平和垂直邊框距離。  
  
```  
DWORD SetPadding(
    int nHorzPadding,   
    int nVertPadding);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `nHorzPadding`|指定水平工具列控制項的邊框距離，單位為像素。|  
|[in] `nVertPadding`|指定垂直工具列控制項的邊框距離，單位為像素。|  
  
### <a name="return-value"></a>傳回值  
 A`DWORD`其低字包含先前的水平填補值，而其高位文字包含先前的垂直填補值。 填補值會以像素為單位測量。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TB_SETPADDING](http://msdn.microsoft.com/library/windows/desktop/bb787448)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定目前工具列控制項的水平和垂直邊框距離 20 像素。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&4;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_6.cpp)]  
  
##  <a name="a-namesetpressedimagelista--ctoolbarctrlsetpressedimagelist"></a><a name="setpressedimagelist"></a>CToolBarCtrl::SetPressedImageList  
 設定目前的工具列控制項用來代表按下狀態的按鈕影像清單。  
  
```  
CImagelist* SetPressedImageList(
    int iImageID,   
    CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iImageID`|影像清單的以零為起始的索引。 如果您使用只有一個映像清單，請將這個參數設定為零。|  
|[in] `pImageList`|指標[CImageList](../../mfc/reference/cimagelist-class.md) ，其中包含新的映像清單。|  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md) ，其中包含目前的控制項，先前的映像清單或`NULL`如果設定了這類的影像清單。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TB_SETPRESSEDIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb787453)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定預設影像清單與相同的已按下的影像清單。  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;&5;](../../mfc/reference/codesnippet/cpp/ctoolbarctrl-class_7.cpp)]  
  
##  <a name="a-namesetrowsa--ctoolbarctrlsetrows"></a><a name="setrows"></a>CToolBarCtrl::SetRows  
 會要求工具列控制項調整大小，以要求的資料列數目。  
  
```  
void SetRows(
    int nRows,  
    BOOL bLarger,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `nRows`  
 要求的資料列數。  
  
 `bLarger`  
 會指示是否要使用多個資料列或較少的資料列，如果無法調整大小工具列，以要求的資料列數目。  
  
 `lpRect`  
 指向[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，將會收到新週框的工具列。  
  
### <a name="remarks"></a>備註  
 如果工具列無法調整本身大小為要求的數目或資料列，它會自行調整大小為下一個較大或下一個較小有效大小，根據的值`bLarger`。 如果`bLarger`是**TRUE**，新的資料列數目將會大於要求的號碼。 如果`bLarger`是**FALSE**，新的資料列數目將會小於要求的號碼。  
  
 如果按鈕，所有資料列具有相同數目的按鈕 （除了可能是最後一個資料列） 都可以排列工具列正確給定的資料列數目。 例如，包含四個按鈕的工具列，可以不重新調整大小以三個資料列因為最後兩個資料列必須短。 如果您嘗試要變成三個資料列，您會收到四個資料列，如果`bLarger`已**TRUE**和兩個資料列，如果`bLarger`已**FALSE**。  
  
 如果在工具列中的分隔符號，給定的資料列數目時有效的規則會更為複雜。 版面配置，除非群組無法容納一個資料列上數個資料列會永遠不會中斷 （使用分隔符號，以在第一個按鈕） 和群組中的最後一個按鈕的按鈕群組計算。  
  
 如果群組不符合在一個資料列上下, 一個群組會啟動下一個資料列上，即使它可容納大型群組結束之處的資料列。 此規則的目的是要更值得注意的大型群組之間的分隔。 產生的垂直分隔符號會視為資料列。  
  
 也請注意，`SetRows`成員函式一律會選擇版面配置，而產生的最小的工具列大小。 建立與工具列`TBSTYLE_WRAPABLE`樣式，然後重新調整控制項只會套用指定的控制項的寬度，上面所述的方法。  
  
 此函式只能呼叫所建立的工具列`TBSTYLE_WRAPABLE`樣式。  
  
##  <a name="a-namesetstatea--ctoolbarctrlsetstate"></a><a name="setstate"></a>CToolBarCtrl::SetState  
 在工具列控制項中設定指定的按鈕的狀態。  
  
```  
BOOL SetState(
    int nID,  
    UINT nState);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 命令按鈕的識別碼。  
  
 `nState`  
 狀態旗標。 它可以是按鈕狀態中所列的值的組合[CToolBarCtrl::AddButtons](#addbuttons)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此函式是特別有用，如果您想要設定一個以上的按鈕狀態。 若要只設定一個狀態，使用下列成員函式的其中一個︰ [EnableButton](#enablebutton)， [CheckButton](#checkbutton)， [HideButton](#hidebutton)，[未決](#indeterminate)，或[PressButton](#pressbutton)。  
  
##  <a name="a-namesetstylea--ctoolbarctrlsetstyle"></a><a name="setstyle"></a>CToolBarCtrl::SetStyle  
 設定工具列控制項的樣式。  
  
```  
void SetStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 A`DWORD`包含的組合[toolbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760439)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesettooltipsa--ctoolbarctrlsettooltips"></a><a name="settooltips"></a>CToolBarCtrl::SetToolTips  
 將工具提示控制項與工具列控制項產生關聯。  
  
```  
void SetToolTips(CToolTipCtrl* pTip);
```  
  
### <a name="parameters"></a>參數  
 *pTip*  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件。  
  
##  <a name="a-namesetwindowthemea--ctoolbarctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CToolBarCtrl::SetWindowTheme  
 設定的視覺化樣式`CToolBarCtrl`物件。  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>參數  
 `pszSubAppName`  
 包含要設定之工具列視覺化樣式的 Unicode 字串指標。  
  
### <a name="return-value"></a>傳回值  
 不使用傳回的值。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[TB_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb787465)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC 範例 MFCIE](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBar 類別](../../mfc/reference/ctoolbar-class.md)

