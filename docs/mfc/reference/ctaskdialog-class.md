---
title: CTaskDialog Class
ms.date: 11/19/2018
f1_keywords:
- CTaskDialog
- AFXTASKDIALOG/CTaskDialog
- AFXTASKDIALOG/CTaskDialog::CTaskDialog
- AFXTASKDIALOG/CTaskDialog::AddCommandControl
- AFXTASKDIALOG/CTaskDialog::AddRadioButton
- AFXTASKDIALOG/CTaskDialog::ClickCommandControl
- AFXTASKDIALOG/CTaskDialog::ClickRadioButton
- AFXTASKDIALOG/CTaskDialog::DoModal
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonCount
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonFlag
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonId
- AFXTASKDIALOG/CTaskDialog::GetOptions
- AFXTASKDIALOG/CTaskDialog::GetSelectedCommandControlID
- AFXTASKDIALOG/CTaskDialog::GetSelectedRadioButtonID
- AFXTASKDIALOG/CTaskDialog::GetVerificationCheckboxState
- AFXTASKDIALOG/CTaskDialog::IsCommandControlEnabled
- AFXTASKDIALOG/CTaskDialog::IsRadioButtonEnabled
- AFXTASKDIALOG/CTaskDialog::IsSupported
- AFXTASKDIALOG/CTaskDialog::LoadCommandControls
- AFXTASKDIALOG/CTaskDialog::LoadRadioButtons
- AFXTASKDIALOG/CTaskDialog::NavigateTo
- AFXTASKDIALOG/CTaskDialog::OnCommandControlClick
- AFXTASKDIALOG/CTaskDialog::OnCreate
- AFXTASKDIALOG/CTaskDialog::OnDestroy
- AFXTASKDIALOG/CTaskDialog::OnExpandButtonClick
- AFXTASKDIALOG/CTaskDialog::OnHelp
- AFXTASKDIALOG/CTaskDialog::OnHyperlinkClick
- AFXTASKDIALOG/CTaskDialog::OnInit
- AFXTASKDIALOG/CTaskDialog::OnNavigatePage
- AFXTASKDIALOG/CTaskDialog::OnRadioButtonClick
- AFXTASKDIALOG/CTaskDialog::OnTimer
- AFXTASKDIALOG/CTaskDialog::OnVerificationCheckboxClick
- AFXTASKDIALOG/CTaskDialog::RemoveAllCommandControls
- AFXTASKDIALOG/CTaskDialog::RemoveAllRadioButtons
- AFXTASKDIALOG/CTaskDialog::SetCommandControlOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtons
- AFXTASKDIALOG/CTaskDialog::SetContent
- AFXTASKDIALOG/CTaskDialog::SetDefaultCommandControl
- AFXTASKDIALOG/CTaskDialog::SetDefaultRadioButton
- AFXTASKDIALOG/CTaskDialog::SetDialogWidth
- AFXTASKDIALOG/CTaskDialog::SetExpansionArea
- AFXTASKDIALOG/CTaskDialog::SetFooterIcon
- AFXTASKDIALOG/CTaskDialog::SetFooterText
- AFXTASKDIALOG/CTaskDialog::SetMainIcon
- AFXTASKDIALOG/CTaskDialog::SetMainInstruction
- AFXTASKDIALOG/CTaskDialog::SetOptions
- AFXTASKDIALOG/CTaskDialog::SetProgressBarMarquee
- AFXTASKDIALOG/CTaskDialog::SetProgressBarPosition
- AFXTASKDIALOG/CTaskDialog::SetProgressBarRange
- AFXTASKDIALOG/CTaskDialog::SetProgressBarState
- AFXTASKDIALOG/CTaskDialog::SetRadioButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckbox
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckboxText
- AFXTASKDIALOG/CTaskDialog::SetWindowTitle
- AFXTASKDIALOG/CTaskDialog::ShowDialog
- AFXTASKDIALOG/CTaskDialog::TaskDialogCallback
helpviewer_keywords:
- CTaskDialog [MFC], CTaskDialog
- CTaskDialog [MFC], AddCommandControl
- CTaskDialog [MFC], AddRadioButton
- CTaskDialog [MFC], ClickCommandControl
- CTaskDialog [MFC], ClickRadioButton
- CTaskDialog [MFC], DoModal
- CTaskDialog [MFC], GetCommonButtonCount
- CTaskDialog [MFC], GetCommonButtonFlag
- CTaskDialog [MFC], GetCommonButtonId
- CTaskDialog [MFC], GetOptions
- CTaskDialog [MFC], GetSelectedCommandControlID
- CTaskDialog [MFC], GetSelectedRadioButtonID
- CTaskDialog [MFC], GetVerificationCheckboxState
- CTaskDialog [MFC], IsCommandControlEnabled
- CTaskDialog [MFC], IsRadioButtonEnabled
- CTaskDialog [MFC], IsSupported
- CTaskDialog [MFC], LoadCommandControls
- CTaskDialog [MFC], LoadRadioButtons
- CTaskDialog [MFC], NavigateTo
- CTaskDialog [MFC], OnCommandControlClick
- CTaskDialog [MFC], OnCreate
- CTaskDialog [MFC], OnDestroy
- CTaskDialog [MFC], OnExpandButtonClick
- CTaskDialog [MFC], OnHelp
- CTaskDialog [MFC], OnHyperlinkClick
- CTaskDialog [MFC], OnInit
- CTaskDialog [MFC], OnNavigatePage
- CTaskDialog [MFC], OnRadioButtonClick
- CTaskDialog [MFC], OnTimer
- CTaskDialog [MFC], OnVerificationCheckboxClick
- CTaskDialog [MFC], RemoveAllCommandControls
- CTaskDialog [MFC], RemoveAllRadioButtons
- CTaskDialog [MFC], SetCommandControlOptions
- CTaskDialog [MFC], SetCommonButtonOptions
- CTaskDialog [MFC], SetCommonButtons
- CTaskDialog [MFC], SetContent
- CTaskDialog [MFC], SetDefaultCommandControl
- CTaskDialog [MFC], SetDefaultRadioButton
- CTaskDialog [MFC], SetDialogWidth
- CTaskDialog [MFC], SetExpansionArea
- CTaskDialog [MFC], SetFooterIcon
- CTaskDialog [MFC], SetFooterText
- CTaskDialog [MFC], SetMainIcon
- CTaskDialog [MFC], SetMainInstruction
- CTaskDialog [MFC], SetOptions
- CTaskDialog [MFC], SetProgressBarMarquee
- CTaskDialog [MFC], SetProgressBarPosition
- CTaskDialog [MFC], SetProgressBarRange
- CTaskDialog [MFC], SetProgressBarState
- CTaskDialog [MFC], SetRadioButtonOptions
- CTaskDialog [MFC], SetVerificationCheckbox
- CTaskDialog [MFC], SetVerificationCheckboxText
- CTaskDialog [MFC], SetWindowTitle
- CTaskDialog [MFC], ShowDialog
- CTaskDialog [MFC], TaskDialogCallback
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
ms.openlocfilehash: 3fd67eed7e80a2e594710df8ae8bc6fd13f0e96c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837667"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

功能像訊息方塊，但是可向使用者顯示其他資訊的快顯對話方塊。 `CTaskDialog` 也包含從使用者收集資訊的功能。

## <a name="syntax"></a>語法

```
class CTaskDialog : public CObject
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[CTaskDialog：： CTaskDialog](#ctaskdialog)|建構 `CTaskDialog` 物件。|

### <a name="methods"></a>方法

|名稱|描述|
|-|-|
|[CTaskDialog：： AddCommandControl](#addcommandcontrol)|將命令按鈕控制項新增至 `CTaskDialog` 。|
|[CTaskDialog：： AddRadioButton](#addradiobutton)|將選項按鈕加入至 `CTaskDialog` 。|
|[CTaskDialog：： ClickCommandControl](#clickcommandcontrol)|以程式設計方式按一下命令按鈕控制項或一般按鈕。|
|[CTaskDialog：： ClickRadioButton](#clickradiobutton)|以程式設計方式按一下選項按鈕。|
|[CTaskDialog：:D oModal](#domodal)|顯示`CTaskDialog`。|
|[CTaskDialog：： GetCommonButtonCount](#getcommonbuttoncount)|抓取可用的常見按鈕數目。|
|[CTaskDialog：： GetCommonButtonFlag](#getcommonbuttonflag)|將標準 Windows 按鈕轉換成與類別相關聯的一般按鈕類型 `CTaskDialog` 。|
|[CTaskDialog：： GetCommonButtonId](#getcommonbuttonid)|將與類別相關聯的其中一個一般按鈕類型轉換 `CTaskDialog` 成標準的 Windows 按鈕。|
|[CTaskDialog：： GetOptions](#getoptions)|傳回這個的選項旗標 `CTaskDialog` 。|
|[CTaskDialog：： GetSelectedCommandControlID](#getselectedcommandcontrolid)|傳回選取的命令按鈕控制項。|
|[CTaskDialog：： GetSelectedRadioButtonID](#getselectedradiobuttonid)|傳回選取的選項按鈕。|
|[CTaskDialog：： GetVerificationCheckboxState](#getverificationcheckboxstate)|捕獲驗證核取方塊的狀態。|
|[CTaskDialog：： IsCommandControlEnabled](#iscommandcontrolenabled)|決定是否啟用命令按鈕控制項或一般按鈕。|
|[CTaskDialog：： IsRadioButtonEnabled](#isradiobuttonenabled)|決定是否啟用選項按鈕。|
|[CTaskDialog：： IsSupported](#issupported)|判斷正在執行應用程式的電腦是否支援 `CTaskDialog` 。|
|[CTaskDialog：： LoadCommandControls](#loadcommandcontrols)|使用字串資料表中的資料，加入命令按鈕控制項。|
|[CTaskDialog：： LoadRadioButtons](#loadradiobuttons)|使用字串資料表中的資料來加入選項按鈕。|
|[CTaskDialog：： NavigateTo](#navigateto)|將焦點轉移到另一個 `CTaskDialog` 。|
|[CTaskDialog：： OnCommandControlClick](#oncommandcontrolclick)|當使用者按一下命令按鈕控制項時，架構會呼叫這個方法。|
|[CTaskDialog：： >oncreate](#oncreate)|架構會在建立之後呼叫這個方法 `CTaskDialog` 。|
|[CTaskDialog：： OnDestroy](#ondestroy)|架構會在終結之前立即呼叫這個方法 `CTaskDialog` 。|
|[CTaskDialog：： OnExpandButtonClick](#onexpandbuttonclick)|當使用者按一下展開按鈕時，架構會呼叫這個方法。|
|[CTaskDialog：： OnHelp](#onhelp)|當使用者要求協助時，架構會呼叫這個方法。|
|[CTaskDialog：： OnHyperlinkClick](#onhyperlinkclick)|當使用者按一下超連結時，架構會呼叫這個方法。|
|[CTaskDialog：： OnInit](#oninit)|當初始化時，架構會呼叫這個方法 `CTaskDialog` 。|
|[CTaskDialog：： OnNavigatePage](#onnavigatepage)|當使用者將焦點移至上的控制項時，架構會呼叫這個方法 `CTaskDialog` 。|
|[CTaskDialog：： OnRadioButtonClick](#onradiobuttonclick)|當使用者選取選項按鈕控制項時，架構會呼叫這個方法。|
|[CTaskDialog：： OnTimer](#ontimer)|當計時器到期時，架構會呼叫這個方法。|
|[CTaskDialog：： OnVerificationCheckboxClick](#onverificationcheckboxclick)|當使用者按一下 [驗證] 核取方塊時，架構會呼叫這個方法。|
|[CTaskDialog：： RemoveAllCommandControls](#removeallcommandcontrols)|從移除所有的命令控制項 `CTaskDialog` 。|
|[CTaskDialog：： RemoveAllRadioButtons](#removeallradiobuttons)|從移除所有的選項按鈕 `CTaskDialog` 。|
|[CTaskDialog：： SetCommandControlOptions](#setcommandcontroloptions)|更新上的命令按鈕控制項 `CTaskDialog` 。|
|[CTaskDialog：： SetCommonButtonOptions](#setcommonbuttonoptions)|更新要啟用的一般按鈕子集，並要求 UAC 提高許可權。|
|[CTaskDialog：： SetCommonButtons](#setcommonbuttons)|將一般按鈕新增至 `CTaskDialog` 。|
|[CTaskDialog：： SetContent](#setcontent)|更新的內容 `CTaskDialog` 。|
|[CTaskDialog：： SetDefaultCommandControl](#setdefaultcommandcontrol)|指定預設的命令按鈕控制項。|
|[CTaskDialog：： SetDefaultRadioButton](#setdefaultradiobutton)|指定預設選項按鈕。|
|[CTaskDialog：： SetDialogWidth](#setdialogwidth)|調整的寬度 `CTaskDialog` 。|
|[CTaskDialog：： SetExpansionArea](#setexpansionarea)|更新的展開區域 `CTaskDialog` 。|
|[CTaskDialog：： SetFooterIcon](#setfootericon)|更新的頁尾圖示 `CTaskDialog` 。|
|[CTaskDialog：： SetFooterText](#setfootertext)|更新頁尾的文字 `CTaskDialog` 。|
|[CTaskDialog：： SetMainIcon](#setmainicon)|更新的主要圖示 `CTaskDialog` 。|
|[CTaskDialog：： SetMainInstruction](#setmaininstruction)|更新的主要指令 `CTaskDialog` 。|
|[CTaskDialog：： >setoptions](#setoptions)|設定的選項 `CTaskDialog` 。|
|[CTaskDialog：： SetProgressBarMarquee](#setprogressbarmarquee)|設定的滾動 `CTaskDialog` 盒列，並將它加入至對話方塊。|
|[CTaskDialog：： SetProgressBarPosition](#setprogressbarposition)|調整進度列的位置。|
|[CTaskDialog：： SetProgressBarRange](#setprogressbarrange)|調整進度列的範圍。|
|[CTaskDialog：： SetProgressBarState](#setprogressbarstate)|設定進度列的狀態，並將其顯示在上 `CTaskDialog` 。|
|[CTaskDialog：： SetRadioButtonOptions](#setradiobuttonoptions)|啟用或停用選項按鈕。|
|[CTaskDialog：： SetVerificationCheckbox](#setverificationcheckbox)|設定驗證核取方塊的核取狀態。|
|[CTaskDialog：： SetVerificationCheckboxText](#setverificationcheckboxtext)|設定 [驗證] 核取方塊右邊的文字。|
|[CTaskDialog：： SetWindowTitle](#setwindowtitle)|設定的標題 `CTaskDialog` 。|
|[CTaskDialog：： ShowDialog](#showdialog)|建立並顯示 `CTaskDialog` 。|
|[CTaskDialog：： TaskDialogCallback](#taskdialogcallback)|架構會呼叫此來回應各種不同的 Windows 訊息。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|-|-|
|`m_aButtons`|的命令按鈕控制項陣列 `CTaskDialog` 。|
|`m_aRadioButtons`|選項按鈕控制項的陣列 `CTaskDialog` 。|
|`m_bVerified`|`TRUE` 表示已核取 [驗證] 核取方塊; `FALSE` 指出它不是。|
|`m_footerIcon`|頁尾中的圖示 `CTaskDialog` 。|
|`m_hWnd`|的視窗控制碼 `CTaskDialog` 。|
|`m_mainIcon`|的主要圖示 `CTaskDialog` 。|
|`m_nButtonDisabled`|指出哪些一般按鈕已停用的遮罩。|
|`m_nButtonElevation`|遮罩，指出哪些一般按鈕需要 UAC 提高許可權。|
|`m_nButtonId`|所選命令按鈕控制項的識別碼。|
|`m_nCommonButton`|表示顯示在上之一般按鈕的遮罩 `CTaskDialog` 。|
|`m_nDefaultCommandControl`|顯示時選取的命令按鈕控制項識別碼 `CTaskDialog` 。|
|`m_nDefaultRadioButton`|顯示時所選取之選項按鈕控制項的識別碼 `CTaskDialog` 。|
|`m_nFlags`|表示選項的遮罩 `CTaskDialog` 。|
|`m_nProgressPos`|進度列的目前位置。  這個值必須介於 `m_nProgressRangeMin` 和 `m_nProgressRangeMax` 之間。|
|`m_nProgressRangeMax`|進度列的最大值。|
|`m_nProgressRangeMin`|進度列的最小值。|
|`m_nProgressState`|進度列的狀態。 如需詳細資訊，請參閱 [CTaskDialog：： SetProgressBarState](#setprogressbarstate)。|
|`m_nRadioId`|選取之選項按鈕控制項的識別碼。|
|`m_nWidth`|`CTaskDialog` 的寬度 (以像素為單位)。|
|`m_strCollapse`|`CTaskDialog`隱藏展開的資訊時，顯示在展開方塊右邊的字串。|
|`m_strContent`|的內容字串 `CTaskDialog` 。|
|`m_strExpand`|`CTaskDialog`顯示展開的資訊時，顯示在展開方塊右邊的字串。|
|`m_strFooter`|的頁尾 `CTaskDialog` 。|
|`m_strInformation`|的展開資訊 `CTaskDialog` 。|
|`m_strMainInstruction`|的主要指示 `CTaskDialog` 。|
|`m_strTitle`|`CTaskDialog` 的標題。|
|`m_strVerification`|`CTaskDialog`顯示在 [驗證] 核取方塊右邊的字串。|

## <a name="remarks"></a>備註

`CTaskDialog`類別會取代標準 Windows 訊息方塊，並具有其他功能，例如從使用者收集資訊的新控制項。 此類別位於 Visual Studio 2010 和更新版本的 MFC 程式庫中。 `CTaskDialog`從 Windows Vista 開始提供。 舊版 Windows 無法顯示 `CTaskDialog` 物件。 用 `CTaskDialog::IsSupported` 來在執行時間判斷目前的使用者是否可以顯示工作對話方塊。 仍支援標準 Windows 訊息方塊。

`CTaskDialog`只有當您使用 Unicode 程式庫建立您的應用程式時，才能使用。

`CTaskDialog`有兩個不同的函式。 其中一個函式可讓您指定兩個命令按鈕，以及最多六個一般按鈕控制項。 建立之後，您可以新增更多命令按鈕 `CTaskDialog` 。 第二個函式不支援任何命令按鈕，但您可以加入無限數量的一般按鈕控制項。 如需有關這些函數的詳細資訊，請參閱 [CTaskDialog：： CTaskDialog](#ctaskdialog)。

下圖顯示的範例 `CTaskDialog` 說明一些控制項的位置。

![CTaskDialog 範例](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialog 範例") <br/>
CTaskDialog 範例

## <a name="requirements"></a>規格需求

**最低需求作業系統：** Windows Vista

**標頭：** afxtaskdialog。h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a> CTaskDialog：： AddCommandControl

將新的命令按鈕控制項新增至 `CTaskDialog` 。

```cpp
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在命令控制項識別碼。

*strCaption*<br/>
在 `CTaskDialog` 顯示給使用者的字串。 使用這個字串來說明命令的用途。

*bEnabled*<br/>
在布林值參數，指出新按鈕為啟用或停用。

*bRequiresElevation*<br/>
在布林值參數，指出命令是否需要提高許可權。

### <a name="remarks"></a>備註

`CTaskDialog Class`可以顯示不限數目的命令按鈕控制項。 但是，如果 `CTaskDialog` 顯示任何命令按鈕控制項，最多可顯示六個按鈕。 如果沒有 `CTaskDialog` 任何命令按鈕控制項，它可以顯示不限數目的按鈕。

當使用者選取命令按鈕控制項時，會 `CTaskDialog` 關閉。 如果您的應用程式使用 [CTaskDialog：:D omodal](#domodal)來顯示對話方塊，則會傳回所 `DoModal` 選命令按鈕控制項的 *nCommandControlID* 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a> CTaskDialog：： AddRadioButton

將選項按鈕加入至 `CTaskDialog` 。

```cpp
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在選項按鈕的識別碼。

*strCaption*<br/>
在在 `CTaskDialog` 選項按鈕旁邊顯示的字串。

*bEnabled*<br/>
在指出是否已啟用選項按鈕的布林值參數。

### <a name="remarks"></a>備註

[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的選項按鈕可讓您收集使用者的資訊。 使用函式 [CTaskDialog：： GetSelectedRadioButtonID](#getselectedradiobuttonid) 來判斷選取的選項按鈕。

不 `CTaskDialog` 需要每個選項按鈕的 *nRadioButtonID* 參數都是唯一的。 但是，如果您不使用每個選項按鈕的相異識別碼，您可能會遇到非預期的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a> CTaskDialog：： ClickCommandControl

以程式設計方式按一下命令按鈕控制項或一般按鈕。

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在要按一下之控制項的命令 ID。

### <a name="remarks"></a>備註

這個方法會產生 windows 訊息 TDM_CLICK_BUTTON。

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a> CTaskDialog：： ClickRadioButton

以程式設計方式按一下選項按鈕。

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在要按一下之選項按鈕的識別碼。

### <a name="remarks"></a>備註

這個方法會產生 windows 訊息 TDM_CLICK_RADIO_BUTTON。

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a> CTaskDialog：： CTaskDialog

建立 [CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的實例。

```
CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nCommonButtons = TDCBF_OK_BUTTON | TDCBF_CANCEL_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));

CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>參數

*strContent*<br/>
在要用於內容的字串 `CTaskDialog` 。

*strMainInstruction*<br/>
在的主要指示 `CTaskDialog` 。

*strTitle*<br/>
在的標題 `CTaskDialog` 。

*nCommonButtons*<br/>
在要加入之一般按鈕的遮罩 `CTaskDialog` 。

*nTaskDialogOptions*<br/>
在要用於的選項組 `CTaskDialog` 。

*strFooter*<br/>
在要作為頁尾使用的字串。

*nIDCommandControlsFirst*<br/>
在第一個命令的字串識別碼。

*nIDCommandControlsLast*<br/>
在最後一個命令的字串識別碼。

### <a name="remarks"></a>備註

有兩種方式可將加入 `CTaskDialog` 至您的應用程式。 第一種方式是使用其中一個函式來建立 `CTaskDialog` ，並使用 [CTaskDialog：:D omodal](#domodal)來顯示它。 第二種方式是使用 static function [CTaskDialog：： ShowDialog](#showdialog)，這可讓您在 `CTaskDialog` 不明確建立物件的情況下顯示 `CTaskDialog` 。

第二個函式會使用來自您應用程式資源檔的資料，建立命令按鈕控制項。 資源檔中的字串資料表有數個具有相關聯字串識別碼的字串。 這個方法會在 *nIDCommandControlsFirst* 和 *nCommandControlsLast*（含）之間的字串資料表中，為每個有效的專案新增一個命令按鈕控制項。 針對這些命令按鈕控制項，字串資料表中的字串是控制項的標題，而字串識別碼是控制項的識別碼。

如需有效選項的清單，請參閱 [CTaskDialog：： >setoptions](#setoptions) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a> CTaskDialog：:D oModal

顯示 `CTaskDialog` 並使其成為強制回應。

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>參數

*hParent*<br/>
在的父視窗 `CTaskDialog` 。

### <a name="return-value"></a>傳回值

對應到使用者所做選擇的整數。

### <a name="remarks"></a>備註

顯示此 [CTaskDialog](../../mfc/reference/ctaskdialog-class.md)的實例。 然後，應用程式會等待使用者關閉對話方塊。

`CTaskDialog`當使用者選取通用按鈕、命令連結控制項或關閉時，就會關閉 `CTaskDialog` 。 傳回值是指出使用者關閉對話方塊之方式的識別碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a> CTaskDialog：： GetCommonButtonCount

捕獲一般按鈕的數目。

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>傳回值

可用的常見按鈕數目。

### <a name="remarks"></a>備註

一般按鈕是您提供給 [CTaskDialog：： CTaskDialog](#ctaskdialog)的預設按鈕。 [CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)會顯示對話方塊底部的按鈕。

CommCtrl 中會提供按鈕的列舉清單。

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a> CTaskDialog：： GetCommonButtonFlag

將標準 Windows 按鈕轉換成與 [CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)相關聯的一般按鈕類型。

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>參數

*nButtonId*<br/>
在標準 Windows 按鈕的值。

### <a name="return-value"></a>傳回值

對應之 `CTaskDialog` 一般按鈕的值。 如果沒有對應的一般按鈕，這個方法會傳回0。

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a> CTaskDialog：： GetCommonButtonId

將與 [CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md) 相關聯的其中一個常見按鈕類型轉換成標準的 Windows 按鈕。

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>參數

*nFlag*<br/>
在與類別相關聯的一般按鈕類型 `CTaskDialog` 。

### <a name="return-value"></a>傳回值

對應標準 Windows 按鈕的值。 如果沒有對應的 Windows 按鈕，此方法會傳回0。

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a> CTaskDialog：： GetOptions

傳回這個的選項旗標 `CTaskDialog` 。

```
int GetOptions() const;
```

### <a name="return-value"></a>傳回值

的旗標 `CTaskDialog` 。

### <a name="remarks"></a>備註

如需 [CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)可用選項的詳細資訊，請參閱 [CTaskDialog：： >setoptions](#setoptions)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a> CTaskDialog：： GetSelectedCommandControlID

傳回選取的命令按鈕控制項。

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>傳回值

目前選取的命令按鈕控制項的識別碼。

### <a name="remarks"></a>備註

您不需要使用這個方法來取得使用者選取之命令按鈕的識別碼。 [CTaskDialog：:D omodal](#domodal)或[CTaskDialog：： ShowDialog](#showdialog)會傳回該識別碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a> CTaskDialog：： GetSelectedRadioButtonID

傳回選取的選項按鈕。

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>傳回值

選取之選項按鈕的識別碼。

### <a name="remarks"></a>備註

您可以在使用者關閉對話方塊來取出選取的選項按鈕之後，使用這個方法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a> CTaskDialog：： GetVerificationCheckboxState

捕獲驗證核取方塊的狀態。

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>傳回值

如果核取核取方塊，則為 TRUE，否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a> CTaskDialog：： IsCommandControlEnabled

決定是否啟用命令按鈕控制項或按鈕。

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在要測試之命令按鈕控制項或按鈕的識別碼。

### <a name="return-value"></a>傳回值

如果已啟用控制項，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

您可以使用這個方法來判斷命令按鈕控制項和類別的一般按鈕的可用性 `CTaskDialog` *。

如果 *nCommandControlID* 不是一般 `CTaskDialog` 按鈕或命令按鈕控制項的有效識別碼，這個方法會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a> CTaskDialog：： IsRadioButtonEnabled

決定是否啟用選項按鈕。

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在要測試之選項按鈕的識別碼。

### <a name="return-value"></a>傳回值

如果已啟用選項按鈕則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

如果 *nRadioButtonID* 不是選項按鈕的有效識別碼，這個方法會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a> CTaskDialog：： IsSupported

判斷正在執行應用程式的電腦是否支援 `CTaskDialog` 。

```
static BOOL IsSupported();
```

### <a name="return-value"></a>傳回值

如果電腦支援，則為 TRUE `CTaskDialog` 。否則為 FALSE。

### <a name="remarks"></a>備註

如果執行您應用程式的電腦支援類別，請使用此函式來判斷執行時間 `CTaskDialog` 。 如果電腦不支援 `CTaskDialog` ，您應該提供另一種方式來與使用者通訊資訊。 如果應用程式嘗試 `CTaskDialog` 在不支援類別的電腦上使用，您的應用程式將會損毀 `CTaskDialog` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a> CTaskDialog：： LoadCommandControls

使用字串資料表中的資料，加入命令按鈕控制項。

```cpp
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>參數

*nIDCommandControlsFirst*<br/>
在第一個命令的字串識別碼。

*nIDCommandControlsLast*<br/>
在最後一個命令的字串識別碼。

### <a name="remarks"></a>備註

這個方法會使用來自您應用程式資源檔的資料，建立命令按鈕控制項。 資源檔中的字串資料表有數個具有相關聯字串識別碼的字串。 使用這個方法新增的新命令按鈕控制項，會使用控制項標題的字串和控制項識別碼的字串識別碼。 選取的字串範圍是由 *nIDCommandControlsFirst* 和 *nCommandControlsLast*（含）所提供。 如果範圍中有空白專案，此方法不會加入該專案的命令按鈕控制項。

預設會啟用新的命令按鈕控制項，而且不需要提高許可權。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a> CTaskDialog：： LoadRadioButtons

使用字串資料表中的資料，加入選項按鈕控制項。

```cpp
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>參數

*nIDRadioButtonsFirst*<br/>
在第一個選項按鈕的字串識別碼。

*nIDRadioButtonsLast*<br/>
在最後一個選項按鈕的字串識別碼。

### <a name="remarks"></a>備註

這個方法會使用來自您應用程式資源檔的資料來建立選項按鈕。 資源檔中的字串資料表有數個具有相關聯字串識別碼的字串。 使用這個方法新增的選項按鈕會使用選項按鈕標題的字串，以及選項按鈕識別碼的字串識別碼。 選取的字串範圍是由 *nIDRadioButtonsFirst* 和 *nRadioButtonsLast*（含）所提供。 如果範圍中有空白專案，此方法不會為該專案加入選項按鈕。

預設會啟用新的選項按鈕。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a> CTaskDialog：： NavigateTo

將焦點轉移到另一個 `CTaskDialog` 。

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>參數

*oTaskDialog*<br/>
在 `CTaskDialog` 接收焦點的。

### <a name="remarks"></a>備註

這個方法 `CTaskDialog` 會在顯示 *oTaskDialog*時隱藏目前的。 *OTaskDialog*會顯示在與目前相同的位置 `CTaskDialog` 。

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a> CTaskDialog：： OnCommandControlClick

當使用者按一下命令按鈕控制項時，架構會呼叫這個方法。

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在使用者選取的命令按鈕控制項識別碼。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a> CTaskDialog：： >oncreate

架構會在建立之後呼叫這個方法 `CTaskDialog` 。

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a> CTaskDialog：： OnDestroy

架構會在終結之前立即呼叫這個方法 `CTaskDialog` 。

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a> CTaskDialog：： OnExpandButtonClick

當使用者按一下展開按鈕時，架構會呼叫這個方法。

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>參數

*bExpanded*<br/>
在非零值表示顯示額外的資訊;0表示隱藏額外的資訊。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a> CTaskDialog：： OnHelp

當使用者要求協助時，架構會呼叫這個方法。

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a> CTaskDialog：： OnHyperlinkClick

當使用者按一下超連結時，架構會呼叫這個方法。

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>參數

*strHref*<br/>
在表示超連結的字串。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

這個方法會先呼叫 [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) ，然後再傳回 S_OK。

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogoninit"></a><a name="oninit"></a> CTaskDialog：： OnInit

當初始化時，架構會呼叫這個方法 `CTaskDialog` 。

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a> CTaskDialog：： OnNavigatePage

架構會呼叫這個方法來回應 [CTaskDialog：： NavigateTo](#navigateto) 方法。

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a> CTaskDialog：： OnRadioButtonClick

當使用者選取選項按鈕控制項時，架構會呼叫這個方法。

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在使用者所按之選項按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a> CTaskDialog：： OnTimer

當計時器到期時，架構會呼叫這個方法。

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>參數

*lTime*<br/>
在自 `CTaskDialog` 建立或重設計時器之後的時間（以毫秒為單位）。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a> CTaskDialog：： OnVerificationCheckboxClick

當使用者按一下 [驗證] 核取方塊時，架構會呼叫這個方法。

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>參數

*bChecked*<br/>
在TRUE 表示已選取 [驗證] 核取方塊;FALSE 表示它不是。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法，以執行自訂行為。

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a> CTaskDialog：： RemoveAllCommandControls

從移除所有的命令按鈕控制項 `CTaskDialog` 。

```cpp
void RemoveAllCommandControls();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a> CTaskDialog：： RemoveAllRadioButtons

從移除所有的選項按鈕 `CTaskDialog` 。

```cpp
void RemoveAllRadioButtons();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a> CTaskDialog：： SetCommandControlOptions

更新上的命令按鈕控制項 `CTaskDialog` 。

```cpp
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在要更新之命令控制項的識別碼。

*bEnabled*<br/>
在布林值參數，指出指定的命令按鈕控制項為啟用或停用。

*bRequiresElevation*<br/>
在布林值參數，指出指定的命令按鈕控制項是否需要提高許可權。

### <a name="remarks"></a>備註

您可以使用這個方法來變更命令按鈕控制項是否已啟用，或在加入至類別之後需要提高許可權 `CTaskDialog` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a> CTaskDialog：： SetCommonButtonOptions

更新要啟用的一般按鈕子集，並要求 UAC 提高許可權。

```cpp
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>參數

*nDisabledButtonMask*<br/>
在要停用之一般按鈕的遮罩。

*nElevationButtonMask*<br/>
在需要提高許可權之一般按鈕的遮罩。

### <a name="remarks"></a>備註

您可以使用[CTaskDialog：： CTaskDialog](#ctaskdialog)和方法[CTaskDialog：： SetCommonButtons](#setcommonbuttons)，將可用的一般按鈕設定為[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的實例。 `CTaskDialog::SetCommonButtonOptions` 不支援加入新的一般按鈕。

如果您使用這個方法來停用或提高無法使用的一般按鈕 `CTaskDialog` ，這個方法會使用「 [確定](diagnostic-services.md#ensure) 」宏擲回例外狀況。

這個方法會啟用任何可用的按鈕， `CTaskDialog` 但不在 *nDisabledButtonMask*中，即使先前已停用也一樣。 此方法會以類似的方式來處理提高許可權：如果一般按鈕可用但未包含在 *nElevationButtonMask*中，則會將一般按鈕記錄為不需要提高許可權。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a> CTaskDialog：： SetCommonButtons

將一般按鈕新增至 `CTaskDialog` 。

```cpp
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>參數

*nButtonMask*<br/>
在要加入之按鈕的遮罩 `CTaskDialog` 。

*nDisabledButtonMask*<br/>
在要停用之按鈕的遮罩。

*nElevationButtonMask*<br/>
在需要提高許可權之按鈕的遮罩。

### <a name="remarks"></a>備註

建立這個類別實例的顯示視窗之後，您就無法呼叫這個方法 `CTaskDialog` 。 如果您這樣做，這個方法會擲回例外狀況。

*NButtonMask*所指出的按鈕會覆寫先前新增至的任何一般按鈕 `CTaskDialog` 。 只有 *nButtonMask* 中指出的按鈕可供使用。

如果 *nDisabledButtonMask* 或 *nElevationButtonMask* 包含不在 *nButtonMask*中的按鈕，這個方法會使用「 [確定](diagnostic-services.md#ensure) 」宏擲回例外狀況。

依預設，所有一般按鈕都會啟用，而且不需要提高許可權。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a> CTaskDialog：： SetContent

更新的內容 `CTaskDialog` 。

```cpp
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>參數

*strContent*<br/>
在要對使用者顯示的字串。

### <a name="remarks"></a>備註

類別的內容 `CTaskDialog` 是在對話方塊的主要區段中，向使用者顯示的文字。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a> CTaskDialog：： SetDefaultCommandControl

指定預設的命令按鈕控制項。

```cpp
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在要做為預設值之命令按鈕控制項的識別碼。

### <a name="remarks"></a>備註

預設的命令按鈕控制項是在 `CTaskDialog` 第一次向使用者顯示時選取的控制項。

如果這個方法找不到 *nCommandControlID*所指定的命令按鈕控制項，則會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a> CTaskDialog：： SetDefaultRadioButton

指定預設選項按鈕。

```cpp
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在要做為預設值之選項按鈕的識別碼。

### <a name="remarks"></a>備註

預設選項按鈕是在 `CTaskDialog` 第一次向使用者顯示時選取的按鈕。

如果找不到 *nRadioButtonID*所指定的選項按鈕，這個方法會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a> CTaskDialog：： SetDialogWidth

調整的寬度 `CTaskDialog` 。

```cpp
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
在對話方塊的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

參數 *nWidth* 必須大於或等於0。 否則，這個方法會擲回例外狀況。

如果 *nWidth* 設為0，則這個方法會將對話方塊設定為預設大小。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a> CTaskDialog：： SetExpansionArea

更新的展開區域 `CTaskDialog` 。

```cpp
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>參數

*strExpandedInformation*<br/>
在 `CTaskDialog` 當使用者按一下展開按鈕時，顯示在對話方塊的主要主體中的字串。

*strCollapsedLabel*<br/>
在折迭 `CTaskDialog` 展開區域時，顯示在展開按鈕旁的字串。

*strExpandedLabel*<br/>
在 `CTaskDialog` 顯示展開區域時，展開按鈕旁邊顯示的字串。

### <a name="remarks"></a>備註

類別的展開區域可 `CTaskDialog` 讓您提供其他資訊給使用者。 展開區域位於的主要部分 `CTaskDialog` ，位於標題和內容字串的正下方。

當 `CTaskDialog` 第一次顯示時，不會顯示展開的資訊並放在 `strCollapsedLabel` 展開按鈕的旁邊。 當使用者按一下 [展開] 按鈕時，會 `CTaskDialog` 顯示 [ *strExpandedInformation* ]，並將標籤變更為 [ *strExpandedLabel*]。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a> CTaskDialog：： SetFooterIcon

更新的頁尾圖示 `CTaskDialog` 。

```cpp
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>參數

*hFooterIcon*<br/>
在的新圖示 `CTaskDialog` 。

*lpszFooterIcon*<br/>
在的新圖示 `CTaskDialog` 。

### <a name="remarks"></a>備註

頁尾圖示會顯示在 [CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的底部。 它可以有相關聯的頁尾文字。 您可以使用 [CTaskDialog：： SetFooterText](#setfootertext)來變更頁尾文字。

如果[ENSURE](diagnostic-services.md#ensure) `CTaskDialog` 顯示或輸入參數為 Null，這個方法會擲回具有確定宏的例外狀況。

只能 `CTaskDialog` 接受 `HICON` 或 `LPCWSTR` 作為頁尾圖示。 這是藉由在函式或 [CTaskDialog：： >setoptions](#setoptions)中設定選項 TDF_USE_HICON_FOOTER 來設定。 根據預設， `CTaskDialog` 會設定為使用做為頁尾 `LPCWSTR` 圖示的輸入類型。 如果您嘗試使用不適當的類型來設定圖示，這個方法會產生例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a> CTaskDialog：： SetFooterText

更新頁尾的文字 `CTaskDialog` 。

```cpp
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>參數

*strFooterText*<br/>
在頁尾的新文字。

### <a name="remarks"></a>備註

頁尾圖示會出現在底部頁尾文字的旁邊 `CTaskDialog` 。 您可以使用 [CTaskDialog：： SetFooterIcon](#setfootericon)來變更頁尾圖示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a> CTaskDialog：： SetMainIcon

更新的主要圖示 `CTaskDialog` 。

```cpp
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>參數

*hMainIcon*<br/>
在新圖示。

*lpszMainIcon*<br/>
在新圖示。

### <a name="remarks"></a>備註

如果[ENSURE](diagnostic-services.md#ensure) `CTaskDialog` 顯示或輸入參數為 Null，這個方法會擲回具有確定宏的例外狀況。

只能 `CTaskDialog` 接受 `HICON` 或 `LPCWSTR` 作為主要圖示。 您可以藉由在函式或 [CTaskDialog：： >setoptions](#setoptions) 方法中設定 TDF_USE_HICON_MAIN 選項來進行設定。 根據預設， `CTaskDialog` 會設定為使用 `LPCWSTR` 做為主要圖示的輸入類型。 如果您嘗試使用不適當的類型來設定圖示，這個方法會產生例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a> CTaskDialog：： SetMainInstruction

更新的主要指令 `CTaskDialog` 。

```cpp
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>參數

*strInstructions*<br/>
在新的主要指令。

### <a name="remarks"></a>備註

類別的主要指示 `CTaskDialog` 是以大型粗體字型顯示給使用者的文字。 它位於標題列下方的對話方塊中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a> CTaskDialog：： >setoptions

設定的選項 `CTaskDialog` 。

```cpp
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>參數

*nOptionFlag*<br/>
在要用於的旗標集合 `CTaskDialog` 。

### <a name="remarks"></a>備註

這個方法會清除的所有目前選項 `CTaskDialog` 。 若要保留目前的選項，您必須先使用 [CTaskDialog：： GetOptions](#getoptions) 取出它們，並將它們與您要設定的選項結合。

下表列出所有有效的選項。

|名稱|描述|
|-|-|
|TDF_ENABLE_HYPERLINKS|啟用中的超連結 `CTaskDialog` 。|
|TDF_USE_HICON_MAIN|將設定 `CTaskDialog` 為 `HICON` 針對主要圖示使用。 替代方法是使用 `LPCWSTR` 。|
|TDF_USE_HICON_FOOTER|將設定 `CTaskDialog` 為使用頁尾 `HICON` 圖示的。 替代方法是使用 `LPCWSTR` 。|
|TDF_ALLOW_DIALOG_CANCELLATION|可讓使用者 `CTaskDialog` 使用鍵盤或使用對話方塊右上角的圖示來關閉，即使未啟用 [ **取消** ] 按鈕也一樣。 如果未設定此旗標，而且未啟用 [ **取消** ] 按鈕，則使用者無法使用 Alt + F4、Escape 鍵或標題列的 [關閉] 按鈕來關閉對話方塊。|
|TDF_USE_COMMAND_LINKS|將設定 `CTaskDialog` 為使用命令按鈕控制項。|
|TDF_USE_COMMAND_LINKS_NO_ICON|將設定 `CTaskDialog` 為使用命令按鈕控制項，而不在控制項旁邊顯示圖示。 TDF_USE_COMMAND_LINKS 覆寫 TDF_USE_COMMAND_LINKS_NO_ICON。|
|TDF_EXPAND_FOOTER_AREA|表示擴充區域目前已展開。|
|TDF_EXPANDED_BY_DEFAULT|判斷展開區域是否預設為展開。|
|TDF_VERIFICATION_FLAG_CHECKED|指出目前已選取 [驗證] 核取方塊。|
|TDF_SHOW_PROGRESS_BAR|將設定 `CTaskDialog` 為顯示進度列。|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|將進度列設定為字幕進度列。 如果您啟用此選項，則必須將 TDF_SHOW_PROGRESS_BAR 設定為具有預期的行為。|
|TDF_CALLBACK_TIMER|指出 `CTaskDialog` 回呼間隔設定為大約200毫秒。|
|TDF_POSITION_RELATIVE_TO_WINDOW|將設定 `CTaskDialog` 為相對於父視窗的中心。 如果未啟用此旗標，則 `CTaskDialog` 會相對於監視器的中央。|
|TDF_RTL_LAYOUT|將設定 `CTaskDialog` 為從右至左的閱讀版面配置。|
|TDF_NO_DEFAULT_RADIO_BUTTON|指出當出現時，不會選取任何選項按鈕 `CTaskDialog` 。|
|TDF_CAN_BE_MINIMIZED|讓使用者可以最小化 `CTaskDialog` 。 若要支援這個選項，則 `CTaskDialog` 不能是強制回應。 MFC 不支援這個選項，因為 MFC 不支援非模式 `CTaskDialog` 。|

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a> CTaskDialog：： SetProgressBarMarquee

設定的滾動 `CTaskDialog` 盒列，並將它加入至對話方塊。

```cpp
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>參數

*bEnabled*<br/>
在TRUE 表示啟用字幕列;FALSE 表示停用字幕列，並將它從移除 `CTaskDialog` 。

*nMarqueeSpeed*<br/>
在整數，表示捲軸的速度。

### <a name="remarks"></a>備註

捲軸列會出現在類別的主要文字下方 `CTaskDialog` 。

使用 *nMarqueeSpeed* 設定捲軸列的速度;較大的值表示速度較慢。 *NMarqueeSpeed*的值為0時，會以 Windows 的預設速度移動捲軸。

如果*nMarqueeSpeed*小於0，則這個方法會擲回具有[確定](diagnostic-services.md#ensure)宏的例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a> CTaskDialog：： SetProgressBarPosition

調整進度列的位置。

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>參數

*nProgressPos*<br/>
在進度列的位置。

### <a name="remarks"></a>備註

如果*nProgressPos*不在進度列範圍內，這個方法會擲回例外狀況，並[確保](diagnostic-services.md#ensure)宏。 您可以使用 [CTaskDialog：： SetProgressBarRange](#setprogressbarrange)來變更進度列範圍。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a> CTaskDialog：： SetProgressBarRange

調整進度列的範圍。

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>參數

*nRangeMin*<br/>
在進度列的下限。

*nRangeMax*<br/>
在進度列的上限。

### <a name="remarks"></a>備註

進度列的位置是相對於 *nRangeMin* 和 *nRangeMax*。 例如，如果 *nRangeMin* 是50，而 *nRangeMax* 是100，則75的位置會是進度列的中間。 使用 [CTaskDialog：： SetProgressBarPosition](#setprogressbarposition) 來設定進度列的位置。

若要顯示進度列，必須啟用選項 TDF_SHOW_PROGRESS_BAR，而且 TDF_SHOW_MARQUEE_PROGRESS_BAR 不能啟用。 這個方法會自動設定 TDF_SHOW_PROGRESS_BAR，並清除 TDF_SHOW_MARQUEE_PROGRESS_BAR。 使用 [CTaskDialog：： >setoptions](#setoptions) 手動變更 [CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)實例的選項。

如果*nRangeMin*不小於*nRangeMax*，這個方法會擲回具有[確定](diagnostic-services.md#ensure)宏的例外狀況。 如果 `CTaskDialog` 已顯示，而且有一個「天棚」進度列，則這個方法也會擲回例外狀況（exception）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a> CTaskDialog：： SetProgressBarState

設定進度列的狀態，並將其顯示在上 `CTaskDialog` 。

```cpp
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>參數

*nState*<br/>
在進度列的狀態。 如需可能的值，請參閱「備註」一節。

### <a name="remarks"></a>備註

如果已[ENSURE](diagnostic-services.md#ensure) `CTaskDialog` 顯示並有一個「天棚」進度列，這個方法會擲回包含「確定」宏的例外狀況。

下表列出 *nState*的可能值。 在這些情況下，進度列會填滿一般色彩，直到到達指定的停止位置為止。 屆時，它會根據狀態變更色彩。

|名稱|描述|
|-|-|
|PBST_NORMAL|在進度列填滿之後，不 `CTaskDialog` 會變更橫條的色彩。 依預設，一般色彩為綠色。|
|PBST_ERROR|在進度列填滿之後，會將 `CTaskDialog` 橫條的色彩變更為錯誤色彩。 根據預設，這是紅色。|
|PBST_PAUSED|在進度列填滿之後，會將 `CTaskDialog` 橫條的色彩變更為暫停的色彩。 根據預設，這是黃色。|

您可以使用 [CTaskDialog：： SetProgressBarPosition](#setprogressbarposition)來設定進度列停止的位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a> CTaskDialog：： SetRadioButtonOptions

啟用或停用選項按鈕。

```cpp
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在選項按鈕控制項的識別碼。

*bEnabled*<br/>
在TRUE 表示啟用選項按鈕;FALSE 表示停用選項按鈕。

### <a name="remarks"></a>備註

如果*nRadioButtonID*不是選項按鈕的有效識別碼，這個方法會擲回具有[確定](diagnostic-services.md#ensure)宏的例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a> CTaskDialog：： SetVerificationCheckbox

設定驗證核取方塊的核取狀態。

```cpp
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>參數

*bChecked*<br/>
在TRUE 表示在顯示時選取 [驗證] 核取方塊 `CTaskDialog` ;FALSE 表示在顯示時，取消選取 [驗證] 核取方塊 `CTaskDialog` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a> CTaskDialog：： SetVerificationCheckboxText

設定在 [驗證] 核取方塊右邊顯示的文字。

```cpp
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>參數

*strVerificationText*<br/>
在此方法在 [驗證] 核取方塊旁邊顯示的文字。

### <a name="remarks"></a>備註

如果已顯示此類別的實例，這個方法會擲回例外狀況，並 [確保](diagnostic-services.md#ensure) 宏 `CTaskDialog` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a> CTaskDialog：： SetWindowTitle

設定的標題 `CTaskDialog` 。

```cpp
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>參數

*strWindowTitle*<br/>
在的新標題 `CTaskDialog` 。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a> CTaskDialog：： ShowDialog

建立並顯示 `CTaskDialog` 。

```
static INT_PTR ShowDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons = TDCBF_YES_BUTTON | TDCBF_NO_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>參數

*strContent*<br/>
在要用於內容的字串 `CTaskDialog` 。

*strMainInstruction*<br/>
在的主要指示 `CTaskDialog` 。

*strTitle*<br/>
在的標題 `CTaskDialog` 。

*nIDCommandControlsFirst*<br/>
在第一個命令的字串識別碼。

*nIDCommandControlsLast*<br/>
在最後一個命令的字串識別碼。

*nCommonButtons*<br/>
在要加入之按鈕的遮罩 `CTaskDialog` 。

*nTaskDialogOptions*<br/>
在要用於的選項組 `CTaskDialog` 。

*strFooter*<br/>
在要作為頁尾使用的字串。

### <a name="return-value"></a>傳回值

對應到使用者所做選擇的整數。

### <a name="remarks"></a>備註

這個靜態方法可讓您建立類別的實例， `CTaskDialog` 而不需要 `CTaskDialog` 在程式碼中明確建立物件。 因為沒有 `CTaskDialog` 物件，所以 `CTaskDialog` 如果您使用這個方法向使用者顯示，就無法呼叫的任何其他方法 `CTaskDialog` 。

這個方法會使用來自您應用程式資源檔的資料，建立命令按鈕控制項。 資源檔中的字串資料表有數個具有相關聯字串識別碼的字串。 這個方法會在 *nIDCommandControlsFirst* 和 *nCommandControlsLast*（含）之間的字串資料表中，為每個有效的專案新增一個命令按鈕控制項。 針對這些命令按鈕控制項，字串資料表中的字串是控制項的標題，而字串識別碼是控制項的識別碼。

如需有效選項的清單，請參閱 [CTaskDialog：： >setoptions](#setoptions) 。

`CTaskDialog`當使用者選取通用按鈕、命令連結控制項或關閉時，就會關閉 `CTaskDialog` 。 傳回值是指出使用者關閉對話方塊之方式的識別碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a> CTaskDialog：： TaskDialogCallback

架構會呼叫這個方法來回應各種 Windows 訊息。

```
friend:
HRESULT TaskDialogCallback(
    HWND hWnd,
    UINT uNotification,
    WPARAM wParam,
    LPARAM lParam,
    LONG_PTR dwRefData);
```

### <a name="parameters"></a>參數

*hwnd*<br/>
在結構的控制碼 `m_hWnd` `CTaskDialog` 。

*uNotification*<br/>
在指定所產生之訊息的通知碼。

*wParam*<br/>
在訊息的詳細資訊。

*lParam*<br/>
在訊息的詳細資訊。

*dwRefData*<br/>
在要 `CTaskDialog` 套用回呼訊息之物件的指標。

### <a name="return-value"></a>傳回值

取決於特定的通知碼。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

的預設執行會 `TaskDialogCallback` 處理特定訊息，然後呼叫 [CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的適當 On 方法。 例如，為了回應 TDN_BUTTON_CLICKED 訊息，會 `TaskDialogCallback` 呼叫 [CTaskDialog：： OnCommandControlClick](#oncommandcontrolclick)。

*WParam*和*lParam*的值取決於特定產生的訊息。 這兩個值的其中之一或兩者都可能是空的。 下表列出支援的預設通知，以及 *wParam* 和 *lParam* 的值代表哪些值。 如果您在衍生類別中覆寫這個方法，您應該針對下表中的每個訊息執行回呼程式碼。

|通知訊息|*wParam* 價值|*lParam* 價值|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|未使用。|未使用。|
|TDN_NAVIGATED|未使用。|未使用。|
|TDN_BUTTON_CLICKED|命令按鈕控制項識別碼。|未使用。|
|TDN_HYPERLINK_CLICKED|未使用。|包含連結的 [LPCWSTR](/windows/win32/WinProg/windows-data-types) 結構。|
|TDN_TIMER|自 `CTaskDialog` 建立或重設計時器之後的時間（以毫秒為單位）。|未使用。|
|TDN_DESTROYED|未使用。|未使用。|
|TDN_RADIO_BUTTON_CLICKED|選項按鈕的識別碼。|未使用。|
|TDN_DIALOG_CONSTRUCTED|未使用。|未使用。|
|TDN_VERIFICATION_CLICKED|如果勾選核取方塊，則為1，否則為0。|未使用。|
|TDN_HELP|未使用。|未使用。|
|TDN_EXPANDO_BUTTON_CLICKED|如果展開區域已折迭，則為0。如果顯示展開文字，則為非零。|未使用。|

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[逐步解說：將 CTaskDialog 新增至應用程式](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
