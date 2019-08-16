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
ms.openlocfilehash: e2f77a2eda4397ed368e477165e876f9b8fbf936
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502349"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

功能像訊息方塊，但是可向使用者顯示其他資訊的快顯對話方塊。 `CTaskDialog` 也包含從使用者收集資訊的功能。

## <a name="syntax"></a>語法

```
class CTaskDialog : public CObject
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[CTaskDialog:: CTaskDialog](#ctaskdialog)|建構 `CTaskDialog` 物件。|

### <a name="methods"></a>方法

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|將命令按鈕控制項加入至`CTaskDialog`。|
|[CTaskDialog::AddRadioButton](#addradiobutton)|將選項按鈕加入至`CTaskDialog`。|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|以程式設計方式按一下命令按鈕控制項或一般按鈕。|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|以程式設計方式按一下選項按鈕。|
|[CTaskDialog::DoModal](#domodal)|顯示`CTaskDialog`。|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|抓取可用的一般按鈕數目。|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|將標準 Windows 按鈕轉換成與`CTaskDialog`類別相關聯的一般按鈕類型。|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|將與`CTaskDialog`類別相關聯的其中一個通用按鈕類型轉換成標準 Windows 按鈕。|
|[CTaskDialog::GetOptions](#getoptions)|傳回這個`CTaskDialog`的選項旗標。|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|傳回選取的命令按鈕控制項。|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|傳回選取的選項按鈕。|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|抓取驗證核取方塊的狀態。|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|決定是否啟用 [命令按鈕控制項] 或 [一般] 按鈕。|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|決定是否啟用選項按鈕。|
|[CTaskDialog:: IsSupported](#issupported)|判斷正在執行應用程式的電腦是否支援`CTaskDialog`。|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|使用字串資料表中的資料加入命令按鈕控制項。|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|使用字串資料表中的資料加入選項按鈕。|
|[CTaskDialog::NavigateTo](#navigateto)|將焦點轉移至另`CTaskDialog`一個。|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|當使用者按一下命令按鈕控制項時, 架構會呼叫這個方法。|
|[CTaskDialog::OnCreate](#oncreate)|架構會在建立`CTaskDialog`之後呼叫這個方法。|
|[CTaskDialog::OnDestroy](#ondestroy)|架構會`CTaskDialog`在終結之前立即呼叫此方法。|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|當使用者按一下展開按鈕時, 架構會呼叫這個方法。|
|[CTaskDialog::OnHelp](#onhelp)|當使用者要求協助時, 架構會呼叫這個方法。|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|當使用者按一下超連結時, 架構會呼叫這個方法。|
|[CTaskDialog::OnInit](#oninit)|當初始化時`CTaskDialog` , 架構會呼叫這個方法。|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|當使用者將焦點移至上`CTaskDialog`的控制項時, 架構會呼叫這個方法。|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|當使用者選取選項按鈕控制項時, 架構會呼叫這個方法。|
|[CTaskDialog::OnTimer](#ontimer)|當計時器到期時, 架構會呼叫這個方法。|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|當使用者按一下 [驗證] 核取方塊時, 架構會呼叫這個方法。|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|從移除所有的命令控制項`CTaskDialog`。|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|從移除所有選項按鈕`CTaskDialog`。|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|更新上`CTaskDialog`的命令按鈕控制項。|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|更新要啟用的通用按鈕子集, 並要求 UAC 提升許可權。|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|將通用按鈕新增至`CTaskDialog`。|
|[CTaskDialog::SetContent](#setcontent)|更新的內容`CTaskDialog`。|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|指定預設的命令按鈕控制項。|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|指定預設的選項按鈕。|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|調整的寬度`CTaskDialog`。|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|更新的展開區域`CTaskDialog`。|
|[CTaskDialog::SetFooterIcon](#setfootericon)|更新的頁尾圖示`CTaskDialog`。|
|[CTaskDialog::SetFooterText](#setfootertext)|更新頁尾上`CTaskDialog`的文字。|
|[CTaskDialog::SetMainIcon](#setmainicon)|更新的主要圖示`CTaskDialog`。|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|更新的主要指令`CTaskDialog`。|
|[CTaskDialog::SetOptions](#setoptions)|設定的選項`CTaskDialog`。|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|設定的`CTaskDialog`捲軸列, 並將其新增至對話方塊。|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|調整進度列的位置。|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|調整進度列的範圍。|
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|設定進度列的狀態, 並將其顯示在上`CTaskDialog`。|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|啟用或停用選項按鈕。|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|設定 [驗證] 核取方塊的核取狀態。|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|設定 [驗證] 核取方塊右邊的文字。|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|設定的標題`CTaskDialog`。|
|[CTaskDialog::ShowDialog](#showdialog)|建立並顯示`CTaskDialog`。|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|架構會呼叫這個, 以回應各種 Windows 訊息。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|`m_aButtons`|的命令按鈕陣列控制項`CTaskDialog`。|
|`m_aRadioButtons`|的選項按鈕控制項`CTaskDialog`陣列。|
|`m_bVerified`|`TRUE`表示已核取 [驗證] 核取方塊;`FALSE`表示不是。|
|`m_footerIcon`|註腳中的圖示`CTaskDialog`。|
|`m_hWnd`|視窗的控制碼`CTaskDialog`。|
|`m_mainIcon`|的主要圖示`CTaskDialog`。|
|`m_nButtonDisabled`|遮罩, 指出哪些通用按鈕已停用。|
|`m_nButtonElevation`|遮罩, 表示哪些通用按鈕需要 UAC 提升許可權。|
|`m_nButtonId`|所選命令按鈕控制項的識別碼。|
|`m_nCommonButton`|表示在上`CTaskDialog`顯示哪些通用按鈕的遮罩。|
|`m_nDefaultCommandControl`|顯示時`CTaskDialog`所選取之命令按鈕控制項的識別碼。|
|`m_nDefaultRadioButton`|顯示時`CTaskDialog`所選取之選項按鈕控制項的識別碼。|
|`m_nFlags`|遮罩, 表示的選項`CTaskDialog`。|
|`m_nProgressPos`|進度列的目前位置。  這個值必須介於 `m_nProgressRangeMin` 和 `m_nProgressRangeMax` 之間。|
|`m_nProgressRangeMax`|進度列的最大值。|
|`m_nProgressRangeMin`|進度列的最小值。|
|`m_nProgressState`|進度列的狀態。 如需詳細資訊, 請參閱[CTaskDialog:: SetProgressBarState](#setprogressbarstate)。|
|`m_nRadioId`|選取之選項按鈕控制項的識別碼。|
|`m_nWidth`|的寬度`CTaskDialog` (以圖元為單位)。|
|`m_strCollapse`|當展開的`CTaskDialog`資訊隱藏時, 顯示在展開方塊右側的字串。|
|`m_strContent`|的內容字串`CTaskDialog`。|
|`m_strExpand`|顯示展開的`CTaskDialog`資訊時, 顯示在展開方塊右側的字串。|
|`m_strFooter`|的頁尾`CTaskDialog`。|
|`m_strInformation`|的擴充資訊`CTaskDialog`。|
|`m_strMainInstruction`|的主要指令`CTaskDialog`。|
|`m_strTitle`|的標題`CTaskDialog`。|
|`m_strVerification`|`CTaskDialog`顯示在 [驗證] 核取方塊右邊的字串。|

## <a name="remarks"></a>備註

`CTaskDialog`類別會取代標準 Windows 訊息方塊, 並具有額外的功能, 例如可從使用者收集資訊的新控制項。 這個類別是在 Visual Studio 2010 和更新版本的 MFC 程式庫中。 `CTaskDialog`從 Windows Vista 開始提供。 舊版的 Windows 無法顯示`CTaskDialog`物件。 使用`CTaskDialog::IsSupported`在執行時間判斷目前使用者是否可以顯示工作對話方塊。 標準 Windows 訊息方塊仍然受支援。

`CTaskDialog`只有當您使用 Unicode 程式庫來建立應用程式時, 才可以使用。

有`CTaskDialog`兩個不同的函式。 一個函式可讓您指定兩個命令按鈕和最多六個一般按鈕控制項。 建立之後, 您可以新增更多命令按鈕`CTaskDialog`。 第二個函式不支援任何命令按鈕, 但您可以新增不限數目的一般按鈕控制項。 如需有關此函數的詳細資訊, 請參閱[CTaskDialog:: CTaskDialog](#ctaskdialog)。

下圖顯示範例`CTaskDialog` , 說明部分控制項的位置。

![CTaskDialog 的範例](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialog 的範例") <br/>
CTaskDialog 範例

## <a name="requirements"></a>需求

**最低所需的作業系統:** Windows Vista

**標頭:** afxtaskdialog。h

##  <a name="addcommandcontrol"></a>CTaskDialog:: AddCommandControl

將新的命令按鈕控制項加入至`CTaskDialog`。

```
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
在向使用者`CTaskDialog`顯示的字串。 使用此字串來說明命令的用途。

*bEnabled*<br/>
在布林值參數, 指出是否已啟用或停用 [新增] 按鈕。

*bRequiresElevation*<br/>
在布林值參數, 指出命令是否需要提高許可權。

### <a name="remarks"></a>備註

`CTaskDialog Class`可以顯示不限數目的命令按鈕控制項。 不過, 如果`CTaskDialog`顯示任何命令按鈕控制項, 則最多可顯示六個按鈕。 `CTaskDialog`如果沒有命令按鈕控制項, 它可以顯示不限數目的按鈕。

當使用者選取命令按鈕控制項時, `CTaskDialog`就會關閉。 如果您的應用程式使用[CTaskDialog::D omodal](#domodal)顯示此對話方塊, `DoModal`則會傳回所選命令按鈕控制項的*nCommandControlID* 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="addradiobutton"></a>CTaskDialog:: AddRadioButton

將選項按鈕加入至`CTaskDialog`。

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在選項按鈕的識別碼。

*strCaption*<br/>
在`CTaskDialog`顯示在選項按鈕旁邊的字串。

*bEnabled*<br/>
在布林值參數, 指出是否已啟用選項按鈕。

### <a name="remarks"></a>備註

[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的選項按鈕可讓您從使用者收集資訊。 使用函數[CTaskDialog:: GetSelectedRadioButtonID](#getselectedradiobuttonid)來決定要選取哪一個選項按鈕。

不需要每個選項按鈕的 nRadioButtonID 參數都是唯一的。 `CTaskDialog` 不過, 如果您未對每個選項按鈕使用相異的識別碼, 可能會遇到未預期的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="clickcommandcontrol"></a>CTaskDialog:: ClickCommandControl

以程式設計方式按一下命令按鈕控制項或一般按鈕。

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在要按一下之控制項的命令 ID。

### <a name="remarks"></a>備註

這個方法會產生 windows message TDM_CLICK_BUTTON。

##  <a name="clickradiobutton"></a>CTaskDialog:: ClickRadioButton

以程式設計方式按一下選項按鈕。

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在要按一下之選項按鈕的識別碼。

### <a name="remarks"></a>備註

這個方法會產生 windows message TDM_CLICK_RADIO_BUTTON。

##  <a name="ctaskdialog"></a>CTaskDialog:: CTaskDialog

建立[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的實例。

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
在要用於內容`CTaskDialog`的字串。

*strMainInstruction*<br/>
在的主要指令`CTaskDialog`。

*strTitle*<br/>
在的標題`CTaskDialog`。

*nCommonButtons*<br/>
在要加入至`CTaskDialog`之一般按鈕的遮罩。

*nTaskDialogOptions*<br/>
在要用於的選項組`CTaskDialog`。

*strFooter*<br/>
在要當做頁尾使用的字串。

*nIDCommandControlsFirst*<br/>
在第一個命令的字串識別碼。

*nIDCommandControlsLast*<br/>
在最後一個命令的字串識別碼。

### <a name="remarks"></a>備註

有兩種方式可將新增`CTaskDialog`至您的應用程式。 第一種方式是使用其中一個函式來建立`CTaskDialog` , 並使用[CTaskDialog::D omodal](#domodal)來顯示它。 第二種方式是使用靜態函數[CTaskDialog:: ShowDialog](#showdialog), 這可讓您顯示`CTaskDialog` , `CTaskDialog`而不需要明確建立物件。

第二個函式會使用您應用程式資源檔中的資料來建立命令按鈕控制項。 資源檔中的字串資料表有數個具有相關聯字串識別碼的字串。 這個方法會在*nIDCommandControlsFirst*和*nCommandControlsLast*(含) 之間的字串資料表中, 為每個有效的專案加入一個命令按鈕控制項。 針對這些命令按鈕控制項, 字串資料表中的字串是控制項的標題, 而字串 ID 則是控制項的識別碼。

如需有效選項的清單, 請參閱[CTaskDialog:: SetOptions](#setoptions) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="domodal"></a>CTaskDialog::D oModal

`CTaskDialog`顯示並使其強制回應。

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>參數

*hParent*<br/>
在的父視窗`CTaskDialog`。

### <a name="return-value"></a>傳回值

對應至使用者所做選擇的整數。

### <a name="remarks"></a>備註

顯示此[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)的實例。 然後, 應用程式會等待使用者關閉對話方塊。

當`CTaskDialog`使用者選取通用按鈕、命令連結控制項或`CTaskDialog`關閉時, 就會關閉。 傳回值是指出使用者如何關閉對話方塊的識別碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getcommonbuttoncount"></a>CTaskDialog:: GetCommonButtonCount

抓取一般按鈕的數目。

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>傳回值

可用的一般按鈕數目。

### <a name="remarks"></a>備註

通用按鈕是您提供給[CTaskDialog:: CTaskDialog](#ctaskdialog)的預設按鈕。 [CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)會顯示對話方塊底部的按鈕。

CommCtrl 中會提供按鈕的列舉清單。

##  <a name="getcommonbuttonflag"></a>CTaskDialog:: GetCommonButtonFlag

將標準 Windows 按鈕轉換成與[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)相關聯的一般按鈕類型。

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>參數

*nButtonId*<br/>
在標準 Windows 按鈕的值。

### <a name="return-value"></a>傳回值

對應`CTaskDialog`一般按鈕的值。 如果沒有對應的一般按鈕, 這個方法會傳回0。

##  <a name="getcommonbuttonid"></a>CTaskDialog:: GetCommonButtonId

將與[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)相關聯的其中一個通用按鈕類型轉換成標準 Windows 按鈕。

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>參數

*nFlag*<br/>
在與`CTaskDialog`類別相關聯的一般按鈕類型。

### <a name="return-value"></a>傳回值

對應標準 Windows 按鈕的值。 如果沒有對應的 Windows 按鈕, 此方法會傳回0。

##  <a name="getoptions"></a>CTaskDialog:: GetOptions

傳回這個`CTaskDialog`的選項旗標。

```
int GetOptions() const;
```

### <a name="return-value"></a>傳回值

的旗標`CTaskDialog`。

### <a name="remarks"></a>備註

如需[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)可用選項的詳細資訊, 請參閱[CTaskDialog:: SetOptions](#setoptions)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getselectedcommandcontrolid"></a>CTaskDialog:: GetSelectedCommandControlID

傳回選取的命令按鈕控制項。

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>傳回值

目前選取的命令按鈕控制項的識別碼。

### <a name="remarks"></a>備註

您不需要使用這個方法來抓取使用者選取之命令按鈕的識別碼。 [CTaskDialog::D omodal](#domodal)或[CTaskDialog:: ShowDialog](#showdialog)會傳回該識別碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="getselectedradiobuttonid"></a>CTaskDialog:: GetSelectedRadioButtonID

傳回選取的選項按鈕。

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>傳回值

選取之選項按鈕的識別碼。

### <a name="remarks"></a>備註

使用者關閉對話方塊以抓取選取的選項按鈕之後, 您就可以使用這個方法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="getverificationcheckboxstate"></a>CTaskDialog:: GetVerificationCheckboxState

抓取驗證核取方塊的狀態。

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>傳回值

如果已核取此核取方塊, 則為 TRUE, 否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="iscommandcontrolenabled"></a>CTaskDialog:: IsCommandControlEnabled

決定命令按鈕控制項或按鈕是否已啟用。

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在要測試之命令按鈕控制項或按鈕的識別碼。

### <a name="return-value"></a>傳回值

如果已啟用控制項, 則為 TRUE, 否則為 FALSE。

### <a name="remarks"></a>備註

您可以使用這個方法來判斷命令按鈕控制項的可用性, 以及`CTaskDialog`類別 * 的一般按鈕。

如果*nCommandControlID*不是通用`CTaskDialog`按鈕或命令按鈕控制項的有效識別碼, 這個方法就會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="isradiobuttonenabled"></a>CTaskDialog:: IsRadioButtonEnabled

決定是否啟用選項按鈕。

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在要測試之選項按鈕的識別碼。

### <a name="return-value"></a>傳回值

如果選項按鈕已啟用, 則為 TRUE, 否則為 FALSE。

### <a name="remarks"></a>備註

如果*nRadioButtonID*不是選項按鈕的有效識別碼, 則這個方法會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="issupported"></a>CTaskDialog:: IsSupported

判斷正在執行應用程式的電腦是否支援`CTaskDialog`。

```
static BOOL IsSupported();
```

### <a name="return-value"></a>傳回值

如果電腦支援, `CTaskDialog`則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果執行應用程式的電腦支援`CTaskDialog`類別, 請使用此函式來判斷執行時間。 如果電腦不支援`CTaskDialog`, 您應該提供另一種將資訊傳達給使用者的方法。 如果您的應用程式嘗試`CTaskDialog`在不`CTaskDialog`支援類別的電腦上使用, 將會損毀。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="loadcommandcontrols"></a>CTaskDialog:: LoadCommandControls

使用字串資料表中的資料加入命令按鈕控制項。

```
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

這個方法會使用您應用程式資源檔中的資料來建立命令按鈕控制項。 資源檔中的字串資料表有數個具有相關聯字串識別碼的字串。 使用此方法加入的新命令按鈕控制項會使用控制項標題的字串, 以及控制項識別碼的字串識別碼。 所選取的字串範圍是由*nIDCommandControlsFirst*和*nCommandControlsLast*(含) 所提供。 如果範圍中有空白專案, 則方法不會為該專案新增命令按鈕控制項。

預設會啟用新的命令按鈕控制項, 而不需要提高許可權。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="loadradiobuttons"></a>CTaskDialog:: LoadRadioButtons

使用字串資料表中的資料加入選項按鈕控制項。

```
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

這個方法會使用您應用程式資源檔中的資料, 建立選項按鈕。 資源檔中的字串資料表有數個具有相關聯字串識別碼的字串。 使用此方法加入的新選項按鈕, 會使用該選項按鈕標題的字串和選項按鈕識別碼的字串識別碼。 所選取的字串範圍是由*nIDRadioButtonsFirst*和*nRadioButtonsLast*(含) 所提供。 如果範圍中有空白專案, 此方法不會為該專案加入選項按鈕。

預設會啟用新的選項按鈕。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="navigateto"></a>CTaskDialog:: NavigateTo

將焦點轉移至另`CTaskDialog`一個。

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>參數

*oTaskDialog*<br/>
在接收`CTaskDialog`焦點的。

### <a name="remarks"></a>備註

這個方法會在顯示`CTaskDialog` *oTaskDialog*時隱藏目前的。 *OTaskDialog*會顯示在與目前`CTaskDialog`相同的位置。

##  <a name="oncommandcontrolclick"></a>CTaskDialog:: OnCommandControlClick

當使用者按一下命令按鈕控制項時, 架構會呼叫這個方法。

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在使用者選取之命令按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="oncreate"></a>CTaskDialog:: OnCreate

架構會在建立`CTaskDialog`之後呼叫這個方法。

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="ondestroy"></a>CTaskDialog:: OnDestroy

架構會`CTaskDialog`在終結之前立即呼叫此方法。

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="onexpandbuttonclick"></a>CTaskDialog:: OnExpandButtonClick

當使用者按一下展開按鈕時, 架構會呼叫這個方法。

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>參數

*bExpanded*<br/>
在非零值表示會顯示額外的資訊;0表示隱藏額外的資訊。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="onhelp"></a>CTaskDialog:: OnHelp

當使用者要求協助時, 架構會呼叫這個方法。

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="onhyperlinkclick"></a>CTaskDialog:: OnHyperlinkClick

當使用者按一下超連結時, 架構會呼叫這個方法。

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>參數

*strHref*<br/>
在表示超連結的字串。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

這個方法會先呼叫[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) , 然後再傳回 S_OK。

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="oninit"></a>CTaskDialog:: OnInit

當初始化時`CTaskDialog` , 架構會呼叫這個方法。

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="onnavigatepage"></a>CTaskDialog:: OnNavigatePage

架構會呼叫這個方法來回應[CTaskDialog:: NavigateTo](#navigateto)方法。

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="onradiobuttonclick"></a>CTaskDialog:: OnRadioButtonClick

當使用者選取選項按鈕控制項時, 架構會呼叫這個方法。

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在使用者按一下的選項按鈕控制項識別碼。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="ontimer"></a>CTaskDialog:: OnTimer

當計時器到期時, 架構會呼叫這個方法。

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>參數

*lTime*<br/>
在自建立或重設`CTaskDialog`計時器後的時間 (以毫秒為單位)。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="onverificationcheckboxclick"></a>CTaskDialog:: OnVerificationCheckboxClick

當使用者按一下 [驗證] 核取方塊時, 架構會呼叫這個方法。

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>參數

*bChecked*<br/>
在TRUE 表示已選取 [驗證] 核取方塊;FALSE 表示不是。

### <a name="return-value"></a>傳回值

預設的實值會傳回 S_OK。

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂行為。

##  <a name="removeallcommandcontrols"></a>CTaskDialog:: RemoveAllCommandControls

從中`CTaskDialog`移除所有的命令按鈕控制項。

```
void RemoveAllCommandControls();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="removeallradiobuttons"></a>CTaskDialog:: RemoveAllRadioButtons

從移除所有選項按鈕`CTaskDialog`。

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setcommandcontroloptions"></a>CTaskDialog:: SetCommandControlOptions

更新上`CTaskDialog`的命令按鈕控制項。

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在要更新之命令控制項的識別碼。

*bEnabled*<br/>
在布林值參數, 指出指定的命令按鈕控制項是否已啟用或停用。

*bRequiresElevation*<br/>
在布林值參數, 指出指定的命令按鈕控制項是否需要提高許可權。

### <a name="remarks"></a>備註

使用此方法來變更命令按鈕控制項是否已啟用, 或在新增至`CTaskDialog`類別之後是否需要提高許可權。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setcommonbuttonoptions"></a>CTaskDialog:: SetCommonButtonOptions

更新要啟用的通用按鈕子集, 並要求 UAC 提升許可權。

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>參數

*nDisabledButtonMask*<br/>
在要停用之通用按鈕的遮罩。

*nElevationButtonMask*<br/>
在需要提高許可權之一般按鈕的遮罩。

### <a name="remarks"></a>備註

您可以使用[CTaskDialog:: CTaskDialog](#ctaskdialog)和方法[CTaskDialog:: SetCommonButtons](#setcommonbuttons), 將可用的一般按鈕設定為[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的實例。 `CTaskDialog::SetCommonButtonOptions`不支援加入新的一般按鈕。

如果您使用這個方法來停用或提高無法使用`CTaskDialog`的一般按鈕, 這個方法會使用 [[確定](diagnostic-services.md#ensure)] 宏來擲回例外狀況。

這個方法會啟用可供使用但不在`CTaskDialog` *nDisabledButtonMask*中的任何按鈕 (即使先前已停用)。 這個方法會以類似的方式來處理提高許可權: 如果 [一般] 按鈕可供使用但未包含在*nElevationButtonMask*中, 則會將一般按鈕記錄為不需要提高許可權。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcommonbuttons"></a>CTaskDialog:: SetCommonButtons

將通用按鈕新增至`CTaskDialog`。

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>參數

*nButtonMask*<br/>
在要加入至`CTaskDialog`之按鈕的遮罩。

*nDisabledButtonMask*<br/>
在要停用之按鈕的遮罩。

*nElevationButtonMask*<br/>
在需要提高許可權之按鈕的遮罩。

### <a name="remarks"></a>備註

您無法在建立此`CTaskDialog`類別實例的顯示視窗之後呼叫這個方法。 如果您這樣做, 這個方法就會擲回例外狀況。

*NButtonMask*所指出的按鈕會覆寫先前加入至的`CTaskDialog`任何一般按鈕。 只有*nButtonMask*中指出的按鈕可供使用。

如果*nDisabledButtonMask*或*nElevationButtonMask*包含不在*nButtonMask*中的按鈕, 這個方法就會使用 [[確定](diagnostic-services.md#ensure)] 宏來擲回例外狀況。

根據預設, 所有通用按鈕都會啟用, 而且不需要提高許可權。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcontent"></a>CTaskDialog:: SetContent

更新的內容`CTaskDialog`。

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>參數

*strContent*<br/>
在要向使用者顯示的字串。

### <a name="remarks"></a>備註

`CTaskDialog`類別的內容是在對話方塊的主要區段中, 向使用者顯示的文字。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setdefaultcommandcontrol"></a>CTaskDialog:: SetDefaultCommandControl

指定預設的命令按鈕控制項。

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>參數

*nCommandControlID*<br/>
在要做為預設值之命令按鈕控制項的識別碼。

### <a name="remarks"></a>備註

預設的命令按鈕控制項是第一次向使用者顯示時`CTaskDialog`所選取的控制項。

如果找不到*nCommandControlID*所指定的命令按鈕控制項, 則這個方法會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setdefaultradiobutton"></a>CTaskDialog:: SetDefaultRadioButton

指定預設的選項按鈕。

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在要做為預設值的選項按鈕識別碼。

### <a name="remarks"></a>備註

[預設] 選項按鈕是第一次向使用者顯示`CTaskDialog`時所選取的按鈕。

如果找不到*nRadioButtonID*所指定的選項按鈕, 這個方法就會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setdialogwidth"></a>CTaskDialog:: SetDialogWidth

調整的寬度`CTaskDialog`。

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
在對話方塊的寬度 (以圖元為單位)。

### <a name="remarks"></a>備註

參數*nWidth*必須大於或等於0。 否則, 這個方法會擲回例外狀況。

如果*nWidth*設定為 0, 這個方法會將對話方塊設定為預設大小。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setexpansionarea"></a>CTaskDialog:: SetExpansionArea

更新的展開區域`CTaskDialog`。

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>參數

*strExpandedInformation*<br/>
在當使用者按一下展開`CTaskDialog`按鈕時, 顯示在對話方塊主體中的字串。

*strCollapsedLabel*<br/>
在折迭的區域`CTaskDialog`折迭時, 在展開按鈕旁顯示的字串。

*strExpandedLabel*<br/>
在顯示展開的區域`CTaskDialog`時, 顯示在展開按鈕旁邊的字串。

### <a name="remarks"></a>備註

`CTaskDialog`類別的擴充區域可讓您為使用者提供額外的資訊。 擴充區域位於的主要部分`CTaskDialog`, 位於標題和內容字串正下方。

當第一次顯示時, 它不會顯示展開的資訊, `strCollapsedLabel`並放在展開按鈕旁。 `CTaskDialog` 當使用者按一下展開按鈕時, `CTaskDialog`會顯示*strExpandedInformation* , 並將標籤變更為*strExpandedLabel*。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootericon"></a>CTaskDialog:: SetFooterIcon

更新的頁尾圖示`CTaskDialog`。

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>參數

*hFooterIcon*<br/>
在的新圖示`CTaskDialog`。

*lpszFooterIcon*<br/>
在的新圖示`CTaskDialog`。

### <a name="remarks"></a>備註

頁尾圖示會顯示在[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的底部。 它可以有相關聯的頁尾文字。 您可以使用[CTaskDialog:: SetFooterText](#setfootertext)來變更頁尾文字。

如果`CTaskDialog`顯示, 或輸入參數為 Null, 這個方法就會擲回具有 [[確定](diagnostic-services.md#ensure)] 宏的例外狀況。

`CTaskDialog`只能接受或`LPCWSTR`做為頁尾圖示。 `HICON` 這是藉由在 TDF_USE_HICON_FOOTER 中設定選項, 或使用[CTaskDialog:: SetOptions](#setoptions)來設定。 根據預設, `CTaskDialog`會設定為使用`LPCWSTR`做為頁尾圖示的輸入類型。 如果您嘗試使用不適當的類型來設定圖示, 這個方法會產生例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootertext"></a>CTaskDialog:: SetFooterText

更新頁尾上`CTaskDialog`的文字。

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>參數

*strFooterText*<br/>
在頁尾的新文字。

### <a name="remarks"></a>備註

頁尾圖示會出現在底部的頁尾`CTaskDialog`文字旁邊。 您可以使用[CTaskDialog:: SetFooterIcon](#setfootericon)變更頁尾圖示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmainicon"></a>CTaskDialog:: SetMainIcon

更新的主要圖示`CTaskDialog`。

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>參數

*hMainIcon*<br/>
在新的圖示。

*lpszMainIcon*<br/>
在新的圖示。

### <a name="remarks"></a>備註

如果`CTaskDialog`顯示, 或輸入參數為 Null, 這個方法就會擲回具有 [[確定](diagnostic-services.md#ensure)] 宏的例外狀況。

`CTaskDialog`只能接受或`LPCWSTR`作為主要圖示。 `HICON` 您可以藉由在此函式中或在[CTaskDialog:: SetOptions](#setoptions)方法中設定 TDF_USE_HICON_MAIN 選項來進行設定。 根據預設, `CTaskDialog`會設定為使用`LPCWSTR`作為主要圖示的輸入類型。 如果您嘗試使用不適當的類型來設定圖示, 這個方法會產生例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmaininstruction"></a>CTaskDialog:: SetMainInstruction

更新的主要指令`CTaskDialog`。

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>參數

*strInstructions*<br/>
在新的主要指令。

### <a name="remarks"></a>備註

`CTaskDialog`類別的主要指示是以較大的粗體字型向使用者顯示的文字。 它位於標題列底下的對話方塊中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setoptions"></a>CTaskDialog:: SetOptions

設定的選項`CTaskDialog`。

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>參數

*nOptionFlag*<br/>
在要用於的旗標集合`CTaskDialog`。

### <a name="remarks"></a>備註

這個方法會清除的所有目前選項`CTaskDialog`。 若要保留目前的選項, 您必須先使用[CTaskDialog:: GetOptions](#getoptions)來抓取它們, 並將它們與您要設定的選項結合。

下表列出所有有效的選項。

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|啟用中的`CTaskDialog`超連結。|
|TDF_USE_HICON_MAIN|將設定`HICON`為使用主要圖示的。 `CTaskDialog` 替代方式是使用`LPCWSTR`。|
|TDF_USE_HICON_FOOTER|將設定`HICON`為使用頁尾圖示的。 `CTaskDialog` 替代方式是使用`LPCWSTR`。|
|TDF_ALLOW_DIALOG_CANCELLATION|可讓使用者使用鍵盤或`CTaskDialog`對話方塊右上角的圖示來關閉, 即使未啟用 [**取消**] 按鈕也一樣。 如果未設定此旗標, 而且未啟用 [**取消**] 按鈕, 使用者就無法使用 Alt + F4、esc 鍵或標題列的 [關閉] 按鈕來關閉對話方塊。|
|TDF_USE_COMMAND_LINKS|將設定`CTaskDialog`為使用命令按鈕控制項。|
|TDF_USE_COMMAND_LINKS_NO_ICON|將設定`CTaskDialog`為使用命令按鈕控制項, 而不顯示控制項旁邊的圖示。 TDF_USE_COMMAND_LINKS 會覆寫 TDF_USE_COMMAND_LINKS_NO_ICON。|
|TDF_EXPAND_FOOTER_AREA|表示擴充區域目前已展開。|
|TDF_EXPANDED_BY_DEFAULT|決定是否依預設展開擴充區域。|
|TDF_VERIFICATION_FLAG_CHECKED|表示目前已選取 [驗證] 核取方塊。|
|TDF_SHOW_PROGRESS_BAR|`CTaskDialog`設定以顯示進度列。|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|將進度列設定為捲軸進度列。 如果您啟用此選項, 您必須將 TDF_SHOW_PROGRESS_BAR 設定為具有預期的行為。|
|TDF_CALLBACK_TIMER|`CTaskDialog`表示回呼間隔設定為大約200毫秒。|
|TDF_POSITION_RELATIVE_TO_WINDOW|將設定`CTaskDialog`為與父視窗相對的置中位置。 如果未啟用此旗標, `CTaskDialog`則會以相對於監視器的中央為中心。|
|TDF_RTL_LAYOUT|設定由`CTaskDialog`右至左閱讀版面配置的。|
|TDF_NO_DEFAULT_RADIO_BUTTON|表示當`CTaskDialog`出現時, 不會選取任何選項按鈕。|
|TDF_CAN_BE_MINIMIZED|讓使用者可以最小化`CTaskDialog`。 若要支援此選項, `CTaskDialog`無法強制回應。 MFC 不支援此選項, 因為 MFC 不支援`CTaskDialog`非強制回應。|

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setprogressbarmarquee"></a>CTaskDialog:: SetProgressBarMarquee

設定的`CTaskDialog`捲軸列, 並將其新增至對話方塊。

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>參數

*bEnabled*<br/>
在TRUE 表示啟用捲軸列;FALSE 表示停用捲軸列, 並將`CTaskDialog`它從移除。

*nMarqueeSpeed*<br/>
在整數, 表示捲軸的速度。

### <a name="remarks"></a>備註

在`CTaskDialog`類別的主要文字底下會出現捲軸。

使用*nMarqueeSpeed*設定字幕的速度;較大的值表示速度較慢。 *NMarqueeSpeed*的值為0時, 表示捲軸會以視窗的預設速度移動。

如果*nMarqueeSpeed*小於 0, 這個方法就會擲回例外狀況, 其中包含 [[確定](diagnostic-services.md#ensure)] 宏。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarposition"></a>CTaskDialog:: SetProgressBarPosition

調整進度列的位置。

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>參數

*nProgressPos*<br/>
在進度列的位置。

### <a name="remarks"></a>備註

如果*nProgressPos*不在進度列範圍內, 這個方法會擲回例外狀況, 其中包含 [[確定](diagnostic-services.md#ensure)] 宏。 您可以使用[CTaskDialog:: SetProgressBarRange](#setprogressbarrange)來變更進度列範圍。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarrange"></a>CTaskDialog:: SetProgressBarRange

調整進度列的範圍。

```
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

進度列的位置相對於*nRangeMin*和*nRangeMax*。 例如, 如果*nRangeMin*是 50, 而*nRangeMax*是 100, 則75的位置是在進度列的一半。 請使用[CTaskDialog:: SetProgressBarPosition](#setprogressbarposition)來設定進度列的位置。

若要顯示進度列, 必須啟用 [TDF_SHOW_PROGRESS_BAR] 選項, 而且不能啟用 TDF_SHOW_MARQUEE_PROGRESS_BAR。 這個方法會自動設定 TDF_SHOW_PROGRESS_BAR 並清除 TDF_SHOW_MARQUEE_PROGRESS_BAR。 請使用[CTaskDialog:: SetOptions](#setoptions)手動變更這個[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)實例的選項。

如果*nRangeMin*不小於*nRangeMax*, 這個方法就會擲回例外狀況, 其中包含[確保](diagnostic-services.md#ensure)宏。 如果已經顯示, 而且有捲軸`CTaskDialog`進度列, 這個方法也會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarstate"></a>CTaskDialog:: SetProgressBarState

設定進度列的狀態, 並將其顯示在上`CTaskDialog`。

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>參數

*nState*<br/>
在進度列的狀態。 如需可能的值, 請參閱備註一節。

### <a name="remarks"></a>備註

這個方法`CTaskDialog`會擲回例外狀況, 其中如果已顯示, 而且具有「天棚」進度列, 則會使用「[確定](diagnostic-services.md#ensure)」宏。

下表列出*nState*的可能值。 在所有這些情況下, 進度列會以一般色彩填滿, 直到到達指定的停止位置。 在該時間點, 它會根據狀態來變更色彩。

|||
|-|-|
|PBST_NORMAL|在進度列填滿之後, `CTaskDialog`不會變更橫條的色彩。 根據預設, 一般色彩為綠色。|
|PBST_ERROR|在進度列填滿之後, `CTaskDialog`會將橫條的色彩變更為錯誤色彩。 根據預設, 這是紅色。|
|PBST_PAUSED|在進度列填滿之後, `CTaskDialog`會將橫條的色彩變更為暫停的色彩。 根據預設, 這是黃色。|

您可以使用[CTaskDialog:: SetProgressBarPosition](#setprogressbarposition)來設定進度列停止的位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setradiobuttonoptions"></a>CTaskDialog:: SetRadioButtonOptions

啟用或停用選項按鈕。

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
在選項按鈕控制項的 ID。

*bEnabled*<br/>
在TRUE 表示啟用選項按鈕;FALSE 表示停用選項按鈕。

### <a name="remarks"></a>備註

如果*nRadioButtonID*不是選項按鈕的有效識別碼, 這個方法就會擲回例外狀況, 其中包含 [[確定](diagnostic-services.md#ensure)] 宏。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setverificationcheckbox"></a>CTaskDialog:: SetVerificationCheckbox

設定 [驗證] 核取方塊的核取狀態。

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>參數

*bChecked*<br/>
在若要在顯示時`CTaskDialog`選取 [驗證] 核取方塊, 則為 TRUE;FALSE `CTaskDialog`表示在顯示時未選取 [驗證] 核取方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setverificationcheckboxtext"></a>CTaskDialog:: SetVerificationCheckboxText

設定顯示在 [驗證] 核取方塊右邊的文字。

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>參數

*strVerificationText*<br/>
在此方法顯示在 [驗證] 核取方塊旁邊的文字。

### <a name="remarks"></a>備註

如果這個`CTaskDialog`類別的實例已經顯示, 這個方法就會擲回例外狀況, 其中包含 [[確定](diagnostic-services.md#ensure)] 宏。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setwindowtitle"></a>CTaskDialog:: SetWindowTitle

設定的標題`CTaskDialog`。

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>參數

*strWindowTitle*<br/>
在的新標題`CTaskDialog`。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="showdialog"></a>CTaskDialog:: ShowDialog

建立並顯示`CTaskDialog`。

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
在要用於內容`CTaskDialog`的字串。

*strMainInstruction*<br/>
在的主要指令`CTaskDialog`。

*strTitle*<br/>
在的標題`CTaskDialog`。

*nIDCommandControlsFirst*<br/>
在第一個命令的字串識別碼。

*nIDCommandControlsLast*<br/>
在最後一個命令的字串識別碼。

*nCommonButtons*<br/>
在要加入至`CTaskDialog`之按鈕的遮罩。

*nTaskDialogOptions*<br/>
在要用於的選項組`CTaskDialog`。

*strFooter*<br/>
在要當做頁尾使用的字串。

### <a name="return-value"></a>傳回值

對應至使用者所做選擇的整數。

### <a name="remarks"></a>備註

這個靜態方法可讓您建立`CTaskDialog`類別的實例, 而不需要在程式碼中明確`CTaskDialog`建立物件。 因為沒有`CTaskDialog` `CTaskDialog`物件, 所以如果您使用這個方法向使用者顯示, 就無法呼叫的任何其他方法。 `CTaskDialog`

這個方法會使用您應用程式資源檔中的資料來建立命令按鈕控制項。 資源檔中的字串資料表有數個具有相關聯字串識別碼的字串。 這個方法會在*nIDCommandControlsFirst*和*nCommandControlsLast*(含) 之間的字串資料表中, 為每個有效的專案加入一個命令按鈕控制項。 針對這些命令按鈕控制項, 字串資料表中的字串是控制項的標題, 而字串 ID 則是控制項的識別碼。

如需有效選項的清單, 請參閱[CTaskDialog:: SetOptions](#setoptions) 。

當`CTaskDialog`使用者選取通用按鈕、命令連結控制項或`CTaskDialog`關閉時, 就會關閉。 傳回值是指出使用者如何關閉對話方塊的識別碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="taskdialogcallback"></a>CTaskDialog:: TaskDialogCallback

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
在`m_hWnd` 結構`CTaskDialog`的控制碼。

*uNotification*<br/>
在指定所產生之訊息的通知程式碼。

*wParam*<br/>
在訊息的詳細資訊。

*lParam*<br/>
在訊息的詳細資訊。

*dwRefData*<br/>
在要套用回撥`CTaskDialog`訊息之物件的指標。

### <a name="return-value"></a>傳回值

視特定的通知碼而定。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

的預設執行`TaskDialogCallback`會處理特定訊息, 然後在[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的方法上呼叫適當的。 例如, 為了回應 TDN_BUTTON_CLICKED 訊息, `TaskDialogCallback`會呼叫[CTaskDialog:: OnCommandControlClick](#oncommandcontrolclick)。

*WParam*和*lParam*的值取決於特定產生的訊息。 其中一個或兩個值都可能是空的。 下表列出支援的預設通知, 以及*wParam*和*lParam*的值代表的內容。 如果您在衍生類別中覆寫這個方法, 您應該為下表中的每個訊息執行回呼程式碼。

|通知訊息|*wParam*Value|*lParam*Value|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|未使用。|未使用。|
|TDN_NAVIGATED|未使用。|未使用。|
|TDN_BUTTON_CLICKED|命令按鈕控制項識別碼。|未使用。|
|TDN_HYPERLINK_CLICKED|未使用。|包含連結的[LPCWSTR](/windows/win32/WinProg/windows-data-types)結構。|
|TDN_TIMER|自建立或重設`CTaskDialog`計時器後的時間 (以毫秒為單位)。|未使用。|
|TDN_DESTROYED|未使用。|未使用。|
|TDN_RADIO_BUTTON_CLICKED|選項按鈕識別碼。|未使用。|
|TDN_DIALOG_CONSTRUCTED|未使用。|未使用。|
|TDN_VERIFICATION_CLICKED|如果已核取此核取方塊, 則為 1, 如果不是, 則為0。|未使用。|
|TDN_HELP|未使用。|未使用。|
|TDN_EXPANDO_BUTTON_CLICKED|如果展開區域已折迭, 則為 0;如果顯示展開文字, 則為非零。|未使用。|

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[逐步解說：新增 CTaskDialog 至應用程式](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
