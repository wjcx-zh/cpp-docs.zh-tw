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
ms.openlocfilehash: e9aeee31d2952d5362c983934ce85f0332f553fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366639"
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
|[C 任務對話::C任務對話](#ctaskdialog)|建構 `CTaskDialog` 物件。|

### <a name="methods"></a>方法

|||
|-|-|
|[CTask對話::新增命令控制](#addcommandcontrol)|新增指令按鍵控制檔`CTaskDialog`。|
|[CTask對話::新增無線按鈕](#addradiobutton)|新增單選按鈕`CTaskDialog`。|
|[CTask對話::按下命令控制](#clickcommandcontrol)|以程式設計方式按下命令按鈕控制件或常用按鈕。|
|[CTask對話::點擊收音機按鈕](#clickradiobutton)|以程式設計方式按下單選按鈕。|
|[CTask對話::Do模態](#domodal)|顯示`CTaskDialog`。|
|[CTask對話::取得公共按鈕計數](#getcommonbuttoncount)|檢索可用公共按鈕的數量。|
|[CTask對話::取得公共按鈕標誌](#getcommonbuttonflag)|將標準 Windows 按鈕轉換`CTaskDialog`為與 類關聯的通用按鈕類型。|
|[CTask對話::取得公共按鈕Id](#getcommonbuttonid)|將與`CTaskDialog`類關聯的常見按鈕類型之一轉換為標準 Windows 按鈕。|
|[CTask 對話:抓取選項](#getoptions)|傳回`CTaskDialog`此的選項標誌。|
|[CTask 對話:抓取所指令控制 ID](#getselectedcommandcontrolid)|返回所選命令按鈕控件。|
|[CTask對話::取得選擇無線電按鈕ID](#getselectedradiobuttonid)|返回選定的單選按鈕。|
|[CTask對話::抓取框狀態](#getverificationcheckboxstate)|檢索驗證複選框的狀態。|
|[CTask對話::啟用命令控制](#iscommandcontrolenabled)|確定是否啟用命令按鈕控制件或通用按鈕。|
|[CTask對話::開啟無線電按鈕](#isradiobuttonenabled)|確定是否啟用了單選按鈕。|
|[CTask對話::支援](#issupported)|確定執行應用程式的電腦是否支援`CTaskDialog`。|
|[C任務對話::載入命令控制](#loadcommandcontrols)|使用字串表中的數據添加命令按鈕控制項。|
|[CTask對話::載入無線按鈕](#loadradiobuttons)|使用字串表中的數據添加單選按鈕。|
|[CTask對話::導航到](#navigateto)|將焦點移至另一`CTaskDialog`個 。|
|[CTask對話::命令控制單擊](#oncommandcontrolclick)|當用戶按下命令按鈕控制件時,框架將調用此方法。|
|[CTask對話::開啟建立](#oncreate)|框架在建立 後呼叫此`CTaskDialog`方法 。|
|[C任務對話::在銷毀](#ondestroy)|框架在銷毀 之前立即呼叫此`CTaskDialog`方法 。|
|[CTask對話::打開按鈕點擊](#onexpandbuttonclick)|當用戶按一下擴展按鈕時,框架將調用此方法。|
|[CTask對話::上説明](#onhelp)|當使用者請求説明時,框架調用此方法。|
|[CTask對話::在超鏈接點擊](#onhyperlinkclick)|當用戶單擊超連結時,框架將調用此方法。|
|[CTask對話::Oninit](#oninit)|初始化 時`CTaskDialog`, 框架呼叫此方法。|
|[CTask對話::上導航頁](#onnavigatepage)|當使用者將焦點移至 上的控制項時,框架將呼叫此`CTaskDialog`方法 。|
|[CTask對話::在電臺點擊](#onradiobuttonclick)|當用戶選擇單選按鈕控制項時,框架將調用此方法。|
|[CTask對話:在計時器上](#ontimer)|當計時器過期時,框架調用此方法。|
|[CTask對話::打開驗證複選框按一下](#onverificationcheckboxclick)|當用戶單擊驗證複選框時,框架將調用此方法。|
|[CTask對話::刪除所有命令控制](#removeallcommandcontrols)|從中移除的所有指令控制器`CTaskDialog`。|
|[CTask對話::刪除所有無線按鈕](#removeallradiobuttons)|從中移除的所有單選按鈕`CTaskDialog`。|
|[CTask對話::設定命令控制選項](#setcommandcontroloptions)|更新 上的指令按鍵控制`CTaskDialog`器 。|
|[CTask對話::設定公共按鈕選項](#setcommonbuttonoptions)|更新要啟用的常見按鈕的子集,並要求 UAC 提升。|
|[CTask對話::設定公共按鈕](#setcommonbuttons)|將一般按鈕加入`CTaskDialog`。|
|[C任務對話::設定內容](#setcontent)|更新`CTaskDialog`的內容 。|
|[CTask對話::設定預設命令控制](#setdefaultcommandcontrol)|指定預設命令按鈕控制件。|
|[CTask對話::設定預設的無線電按鈕](#setdefaultradiobutton)|指定預設單選按鈕。|
|[C任務對話::設定對話寬度](#setdialogwidth)|調整的`CTaskDialog`寬度。|
|[C 任務對話::設定擴充區域](#setexpansionarea)|更新的`CTaskDialog`擴展區域。|
|[CTask對話::SetFooterIcon](#setfootericon)|更新`CTaskDialog`的頁腳圖示。|
|[CTask對話::設定文字](#setfootertext)|更新 文上的`CTaskDialog`文字 。|
|[CTask對話::設定主圖示](#setmainicon)|更新的主`CTaskDialog`圖示。|
|[CTask對話::設定主指令](#setmaininstruction)|更新的主要`CTaskDialog`指令。|
|[C 任務對話::設定選項](#setoptions)|設定的選項`CTaskDialog`。|
|[CTask對話::設定進度列](#setprogressbarmarquee)|為 配置`CTaskDialog`選框列並將其添加到對話方塊中。|
|[C任務對話::設定進度列位置](#setprogressbarposition)|調整進度條的位置。|
|[CTask對話::設定進度列範圍](#setprogressbarrange)|調整進度條的範圍。|
|[C任務對話::設定進度列](#setprogressbarstate)|設定進度列號的狀態並將顯示在上`CTaskDialog`。|
|[CTask對話::設定無線按鈕選項](#setradiobuttonoptions)|啟用或禁用單選按鈕。|
|[C任務對話::設定驗證複選框](#setverificationcheckbox)|設置驗證複選框的選中狀態。|
|[CTask對話::設定驗證複選框文字](#setverificationcheckboxtext)|設定驗證複選框右側的文本。|
|[C 任務對話::設定視窗標題](#setwindowtitle)|設定的標題`CTaskDialog`。|
|[C 任務對話::顯示對話](#showdialog)|建立並顯示`CTaskDialog`。|
|[C任務對話::工作對話回調](#taskdialogcallback)|框架調用此以回應各種 Windows 消息。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|`m_aButtons`|命令按鈕控制器的陣列`CTaskDialog`。|
|`m_aRadioButtons`|的單選按鈕控制元件的陣列`CTaskDialog`。|
|`m_bVerified`|`TRUE`指示已選中驗證複選框;`FALSE`表示它不是。|
|`m_footerIcon`|中腳的圖示`CTaskDialog`。|
|`m_hWnd`|視窗的句柄`CTaskDialog`。|
|`m_mainIcon`|的主圖示`CTaskDialog`。|
|`m_nButtonDisabled`|指示禁用哪些常見按鈕的蒙版。|
|`m_nButtonElevation`|指示哪些常見按鈕需要 UAC 提升的蒙版。|
|`m_nButtonId`|所選命令按鈕控制件的識別碼。|
|`m_nCommonButton`|指示 在 上顯示哪些常見`CTaskDialog`按鈕的 蒙版。|
|`m_nDefaultCommandControl`|顯示 時選擇的命令按鈕控制`CTaskDialog`項的識別碼。|
|`m_nDefaultRadioButton`|顯示 時選擇的單選按鈕控制`CTaskDialog`項的識別碼。|
|`m_nFlags`|指示的選項的`CTaskDialog`蒙版。|
|`m_nProgressPos`|進度條的當前位置。  這個值必須介於 `m_nProgressRangeMin` 和 `m_nProgressRangeMax` 之間。|
|`m_nProgressRangeMax`|進度條的最大值。|
|`m_nProgressRangeMin`|進度條的最小值。|
|`m_nProgressState`|進度條的狀態。 有關詳細資訊,請參閱[CTaskDialog:設定進度列](#setprogressbarstate)。|
|`m_nRadioId`|所選單選按鈕控制件的識別碼。|
|`m_nWidth`|`CTaskDialog` 的寬度 (以像素為單位)。|
|`m_strCollapse`|隱藏展開資訊`CTaskDialog`時,將顯示的字串顯示在擴展框的右側。|
|`m_strContent`|的內容字串`CTaskDialog`。|
|`m_strExpand`|顯示展開資訊`CTaskDialog`時,在擴展框右側顯示的字串。|
|`m_strFooter`|頁腳`CTaskDialog`。|
|`m_strInformation`|的延伸資訊`CTaskDialog`。|
|`m_strMainInstruction`|的主要指令`CTaskDialog`。|
|`m_strTitle`|`CTaskDialog` 的標題。|
|`m_strVerification`|在驗證複選框右側`CTaskDialog`顯示的字串。|

## <a name="remarks"></a>備註

該`CTaskDialog`類替換標準 Windows 消息框,並具有其他功能,如從使用者收集資訊的新控件。 此類位於 Visual Studio 2010 及更高版本中的 MFC 庫中。 從`CTaskDialog`Windows Vista 開始,提供 。 早期版本的 Windows`CTaskDialog`無法顯示 該物件。 用於`CTaskDialog::IsSupported`確定當前使用者是否可以顯示任務對話方塊。 仍然支持標準 Windows 消息框。

僅當`CTaskDialog`使用 Unicode 庫生成應用程式時,才可用。

有`CTaskDialog`兩個不同的構造函數。 一個建構函數允許您指定兩個命令按鈕和最多六個常規按鈕控制項。 建立 後可以新增更多命令`CTaskDialog`按鈕 。 第二個建構函數不支援任何命令按鈕,但您可以添加無限數量的常規按鈕控制項。 有關建構函數的詳細資訊,請參閱[CTaskDialog::CTaskDialog](#ctaskdialog)。

下圖顯示了一個示例`CTaskDialog`,用於說明某些控件的位置。

![CTaskDialog 範例](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialog 範例") <br/>
C 任務對話範例

## <a name="requirements"></a>需求

**最低要求作業系統:** 視窗Vista

**標題:** afxtaskdialog.h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a>CTask對話::新增命令控制

加入新的命令按鈕控制項。 `CTaskDialog`

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>參數

*n命令控制ID*<br/>
[在]命令控制標識號。

*串標題*<br/>
[在]向使用者顯示的`CTaskDialog`字串。 使用此字串來解釋命令的用途。

*b 啟用*<br/>
[在]指示新按鈕是啟用還是禁用的布爾參數。

*b 要求提升*<br/>
[在]指示命令是否需要高程的布爾參數。

### <a name="remarks"></a>備註

`CTaskDialog Class`可以顯示無限數量的命令按鈕控制項。 但是,如果`CTaskDialog`顯示任何命令按鈕控件,它最多可以顯示六個按鈕。 `CTaskDialog`如果沒有命令按鈕控件,它可以顯示無限數量的按鈕。

當使用者選擇命令按鈕控制檔時, 將`CTaskDialog`關閉 。 如果應用程式使用[CTaskDialog::DoModal](#domodal)顯示對話`DoModal`方塊, 則傳回所選命令按鈕控制項的*nCommandControlID。*

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a>CTask對話::新增無線按鈕

新增單選按鈕`CTaskDialog`。

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
[在]單選按鈕的標識號。

*串標題*<br/>
[在]在單選按鈕`CTaskDialog`旁邊顯示的字串。

*b 啟用*<br/>
[在]指示是否啟用單選按鈕的布爾參數。

### <a name="remarks"></a>備註

[CTaskDialog 類](../../mfc/reference/ctaskdialog-class.md)的單選按鈕使您能夠從用戶那裡收集資訊。 使用函數[CTaskDialog:獲取選擇無線電按鈕ID](#getselectedradiobuttonid)來確定選擇了哪個單選按鈕。

不`CTaskDialog`要求*nRadioButtonID*參數對於每個單選按鈕是唯一的。 但是,如果不為每個單選按鈕使用不同的標識符,則可能會遇到意外行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a>CTask對話::按下命令控制

以程式設計方式按下命令按鈕控制件或常用按鈕。

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>參數

*n命令控制ID*<br/>
[在]要按下的控制項的命令 ID。

### <a name="remarks"></a>備註

此方法生成視窗消息TDM_CLICK_BUTTON。

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a>CTask對話::點擊收音機按鈕

以程式設計方式按下單選按鈕。

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
[在]要按下的單選按鈕的 ID。

### <a name="remarks"></a>備註

此方法生成視窗消息TDM_CLICK_RADIO_BUTTON。

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a>C 任務對話::C任務對話

創建[CTaskDialog 類](../../mfc/reference/ctaskdialog-class.md)的實體。

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

*str 內容*<br/>
[在]用於的內容`CTaskDialog`的字串。

*斯特曼指令*<br/>
[在]的主要指令`CTaskDialog`。

*斯特標題*<br/>
[在]的標題`CTaskDialog`。

*n 通用按鈕*<br/>
[在]要新增的常用按鈕的遮罩`CTaskDialog`。

*n 工作對話選項*<br/>
[在]用於的選項`CTaskDialog`集。

*斯特福特*<br/>
[在]要用作頁腳的字串。

*nID 命令控制優先*<br/>
[在]第一個命令的字串 ID。

*nID 命令控制上次*<br/>
[在]最後一個命令的字串 ID。

### <a name="remarks"></a>備註

有兩種方法可以加入應用程式 。 `CTaskDialog` 第一種方法是使用其中一個建構函數創建`CTaskDialog`, 並使用[CTaskDialog::DoModal](#domodal)顯示它。 第二種方法是使用靜態函數[CTaskDialog::showDialog](#showdialog),它使您能夠在不顯`CTaskDialog``CTaskDialog`式建立 物件的情況下顯示 。

第二個建構函數使用來自應用程式的資源文件的數據創建命令按鈕控制項。 資源檔中的字串表具有多個字串與關聯的字串指示。 此方法為*nIDCommandControlsFirst*和*nCommandControlsLast*之間的字串表中的每個有效項目添加命令按鈕控制項,包括。 對於這些命令按鈕控制項,字串表中的字串是控制項的標題,字串 ID 是控制項的識別碼。

關於有效選項的清單,請參閱[CTaskDialog:設定選項](#setoptions)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a>CTask對話::Do模態

顯示`CTaskDialog`和使其模態。

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>參數

*h 家長*<br/>
[在]的`CTaskDialog`父視窗。

### <a name="return-value"></a>傳回值

與使用者所做的選擇對應的整數。

### <a name="remarks"></a>備註

顯示[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)的此實例。 然後,應用程式等待使用者關閉對話方塊。

當使用者`CTaskDialog`選擇公共按鈕、指令連結控制項或關閉`CTaskDialog`時 關閉 。 返回值是指示使用者如何關閉對話框的標識符。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a>CTask對話::取得公共按鈕計數

檢索常用按鈕的數量。

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>傳回值

可用的常用按鈕數。

### <a name="remarks"></a>備註

常見按鈕是提供給[CTaskDialog::CTaskDialog](#ctaskdialog)的默認按鈕。 [CTaskDialog 類](../../mfc/reference/ctaskdialog-class.md)顯示對話框底部的按鈕。

枚舉的按鈕清單在 CommCtrl.h 中提供。

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a>CTask對話::取得公共按鈕標誌

將標準 Windows 按鈕轉換為與[CTaskDialog 類](../../mfc/reference/ctaskdialog-class.md)關聯的常見按鈕類型。

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>參數

*nButtonId*<br/>
[在]標準 Windows 按鈕值。

### <a name="return-value"></a>傳回值

相應的`CTaskDialog`公用按鈕的值。 如果沒有相應的通用按鈕,此方法返回 0。

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a>CTask對話::取得公共按鈕Id

將與[CTaskDialog 類](../../mfc/reference/ctaskdialog-class.md)關聯的常見按鈕類型之一轉換為標準 Windows 按鈕。

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>參數

*nFlag*<br/>
[在]與`CTaskDialog`類關聯的通用按鈕類型。

### <a name="return-value"></a>傳回值

相應的標準 Windows 按鈕的值。 如果沒有相應的 Windows 按鈕,該方法將返回 0。

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a>CTask 對話:抓取選項

傳回`CTaskDialog`此的選項標誌。

```
int GetOptions() const;
```

### <a name="return-value"></a>傳回值

中區的旗`CTaskDialog`標 。

### <a name="remarks"></a>備註

有關[CTaskDialog 類別](../../mfc/reference/ctaskdialog-class.md)的選項的詳細資訊,請參閱[CTaskDialog::setOptions](#setoptions)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a>CTask 對話:抓取所指令控制 ID

返回所選命令按鈕控件。

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>傳回值

當前選擇指令按鈕控制件的識別碼。

### <a name="remarks"></a>備註

不必使用此方法檢索用戶選擇的命令按鈕的 ID。 該 ID 由[CTaskDialog::Do 模式或](#domodal) [CTaskDialog::顯示對話](#showdialog)返回。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a>CTask對話::取得選擇無線電按鈕ID

返回選定的單選按鈕。

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>傳回值

所選單選按鈕的 ID。

### <a name="remarks"></a>備註

用戶可以在使用者關閉對話方塊後使用此方法來檢索選定的單選按鈕。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a>CTask對話::抓取框狀態

檢索驗證複選框的狀態。

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>傳回值

如果選中該複選框,則為 TRUE,如果沒有,則 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a>CTask對話::啟用命令控制

確定是否啟用命令按鈕控制件或按鈕。

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>參數

*n命令控制ID*<br/>
[在]要測試的命令按鈕控制件或按鈕的 ID。

### <a name="return-value"></a>傳回值

如果啟用了控制項,則為 TRUE,如果未啟用,則為 FALSE。

### <a name="remarks"></a>備註

可以使用此方法確定命令按鈕控制項和`CTaskDialog`Class* 的常見按鈕的可用性。

如果*nCommandControlID*`CTaskDialog`不是常見 按鈕或命令按鈕控制件的有效識別符,則此方法將引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a>CTask對話::開啟無線電按鈕

確定是否啟用了單選按鈕。

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
[在]要測試的單選按鈕的 ID。

### <a name="return-value"></a>傳回值

如果啟用了單選按鈕,則為 TRUE,如果沒有,則 FALSE。

### <a name="remarks"></a>備註

如果*nRadioButtonID*不是單選按鈕的有效標識符,則此方法將引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a>CTask對話::支援

確定執行應用程式的電腦是否支援`CTaskDialog`。

```
static BOOL IsSupported();
```

### <a name="return-value"></a>傳回值

如果電腦支援,`CTaskDialog`則為 TRUE。否則。

### <a name="remarks"></a>備註

使用此函數在運行時確定運行應用程式的計算機是否支援該`CTaskDialog`類。 如果電腦不支援`CTaskDialog`, 應提供另一種方法將資訊傳達給使用者。 如果應用程式嘗試在不支援該`CTaskDialog``CTaskDialog`類的電腦上使用, 則應用程式將崩潰。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a>C任務對話::載入命令控制

使用字串表中的數據添加命令按鈕控制項。

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>參數

*nID 命令控制優先*<br/>
[在]第一個命令的字串 ID。

*nID 命令控制上次*<br/>
[在]最後一個命令的字串 ID。

### <a name="remarks"></a>備註

此方法透過使用來自應用程式的資源檔的資料建立命令按鈕控制項。 資源檔中的字串表具有多個字串與關聯的字串指示。 使用此方法添加的新命令按鈕控制項使用字串作為控制項的標題和控制項 ID 的字串 ID。 所選字串的範圍由*nIDCommandControlsFirst*和*nCommandControlsLast*提供,包括。 如果區域中有空條目,則 該方法不會為該條目添加命令按鈕控件。

默認情況下,啟用新的命令按鈕控制項,不需要提升。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a>CTask對話::載入無線按鈕

使用字串表中的數據添加單選按鈕控制項。

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>參數

*nIDRadioButtons 首先*<br/>
[在]第一個單選按鈕的字串 ID。

*nIDRadioButtonSLast*<br/>
[在]最後一個單選按鈕的字串 ID。

### <a name="remarks"></a>備註

此方法使用應用程式的資源檔中的數據創建單選按鈕。 資源檔中的字串表具有多個字串與關聯的字串指示。 使用此方法添加的新單選按鈕使用單選按鈕的字幕字串和單選按鈕 ID 的字串 ID。 所選字串的範圍由*nIDRadioButtonsFirst*和*nRadioButtonSLast*提供,包括。 如果範圍內有空條目,則 該方法不會為該條目添加單選按鈕。

預設情況下,啟用新的單選按鈕。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a>CTask對話::導航到

將焦點移至另一`CTaskDialog`個 。

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>參數

*o工作交談*<br/>
[在]接收`CTaskDialog`焦點的 。

### <a name="remarks"></a>備註

此方法在顯示`CTaskDialog`*oTaskDialog*時隱藏電流。 *oTaskDialog*與`CTaskDialog`當前的位置相同。

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a>CTask對話::命令控制單擊

當用戶按下命令按鈕控制件時,框架將調用此方法。

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>參數

*n命令控制ID*<br/>
[在]使用者選擇的命令按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a>CTask對話::開啟建立

框架在建立 後呼叫此`CTaskDialog`方法 。

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a>C任務對話::在銷毀

框架在銷毀 之前立即呼叫此`CTaskDialog`方法 。

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a>CTask對話::打開按鈕點擊

當用戶按一下擴展按鈕時,框架將調用此方法。

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>參數

*b 延伸*<br/>
[在]非零值表示顯示額外資訊;使用 「非零」值,表示顯示額外資訊。0 表示附加資訊已隱藏。

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a>CTask對話::上説明

當使用者請求説明時,框架調用此方法。

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a>CTask對話::在超鏈接點擊

當用戶單擊超連結時,框架將調用此方法。

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>參數

*斯特雷赫*<br/>
[在]表示超連結的字串。

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

此方法在返回S_OK之前調用[ShellExecute。](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogoninit"></a><a name="oninit"></a>CTask對話::Oninit

初始化 時`CTaskDialog`, 框架呼叫此方法。

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a>CTask對話::上導航頁

框架呼叫此方法以回應[CTaskDialog::Navigateto](#navigateto)方法。

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a>CTask對話::在電臺點擊

當用戶選擇單選按鈕控制項時,框架將調用此方法。

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
[在]使用者按下的單選按鈕控制的 ID。

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a>CTask對話:在計時器上

當計時器過期時,框架調用此方法。

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>參數

*lTime*<br/>
[在]創建 或重置計時器`CTaskDialog`以來的時間(以毫秒為單位)。

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a>CTask對話::打開驗證複選框按一下

當用戶單擊驗證複選框時,框架將調用此方法。

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>參數

*bChecked*<br/>
[在]TRUE 表示選擇了驗證複選框;FALSE 表示它不是。

### <a name="return-value"></a>傳回值

預設實現返回S_OK。

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義行為。

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a>CTask對話::刪除所有命令控制

從中移除的所有指令按鍵控制器`CTaskDialog`。

```
void RemoveAllCommandControls();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a>CTask對話::刪除所有無線按鈕

從中移除的所有單選按鈕`CTaskDialog`。

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a>CTask對話::設定命令控制選項

更新 上的指令按鍵控制`CTaskDialog`器 。

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>參數

*n命令控制ID*<br/>
[在]要更新的命令控制件的 ID。

*b 啟用*<br/>
[在]布爾參數,指示指定的命令按鈕控制項是啟用還是禁用。

*b 要求提升*<br/>
[在]布爾參數,指示指定的命令按鈕控制項是否需要高程。

### <a name="remarks"></a>備註

使用此方法可以更改命令按鈕控制項是否已啟用或在添加到`CTaskDialog`類後是否需要提升。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a>CTask對話::設定公共按鈕選項

更新要啟用的常用按鈕的子集,並要求 UAC 提升。

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>參數

*n 關閉按鈕的遮罩*<br/>
[在]要禁用的常見按鈕的掩碼。

*n 海拔按鈕的遮罩*<br/>
[在]需要高程的常見按鈕的蒙版。

### <a name="remarks"></a>備註

可以使用建構函數[CTaskDialog::CTaskDialog](#ctaskdialog)和方法[CTaskDialog::setCommonButton,](#setcommonbuttons)設置[CTaskDialog 類](../../mfc/reference/ctaskdialog-class.md)實例可用的通用按鈕。 `CTaskDialog::SetCommonButtonOptions`不支援添加新的通用按鈕。

如果使用此方法禁用或提升對此不可用的通用按鈕`CTaskDialog`,則此方法通過使用["確保"](diagnostic-services.md#ensure)宏引發異常。

此方法啟用任何可用於`CTaskDialog`但不在 n*殘疾人按鈕掩碼中的*按鈕,即使它以前已禁用也是如此。 此方法以類似的方式對待高程:如果通用按鈕可用但不包括在*nElevation Button 遮罩*中,則將通用按鈕記錄為不需要高程。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a>CTask對話::設定公共按鈕

將一般按鈕加入`CTaskDialog`。

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>參數

*nButton 遮罩*<br/>
[在]要添加到`CTaskDialog`的 按鈕的掩碼。

*n 關閉按鈕的遮罩*<br/>
[在]要禁用的按鈕的掩碼。

*n 海拔按鈕的遮罩*<br/>
[在]需要高程的按鈕的蒙版。

### <a name="remarks"></a>備註

建立類別的此實體的顯示視窗後,`CTaskDialog`無法呼叫此方法。 如果這樣做,此方法將引發異常。

*nButtonMask*指示的按鈕將覆蓋以前添加到`CTaskDialog`的任何 常見按鈕。 只有*nButton Mask*中指示的按鈕可用。

如果*n 停用 Button Mask*或*nElevationButton Mask*包含的按鈕不在*nButton Mask*中,則此方法透過使用["確保"](diagnostic-services.md#ensure)巨集引發異常。

默認情況下,所有常見按鈕都已啟用,不需要提升。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a>C任務對話::設定內容

更新`CTaskDialog`的內容 。

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>參數

*str 內容*<br/>
[在]要向使用者顯示的字串。

### <a name="remarks"></a>備註

`CTaskDialog`類的內容是在對話框的主部分向用戶顯示的文本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a>CTask對話::設定預設命令控制

指定預設命令按鈕控制件。

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>參數

*n命令控制ID*<br/>
[在]命令按鈕控制項的 ID 為預設值。

### <a name="remarks"></a>備註

預設命令按鈕控制項是首次向使用者顯示`CTaskDialog`時 選擇的控制項。

如果找不到*nCommandControlID*指定的命令按鈕控制項,此方法將引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a>CTask對話::設定預設的無線電按鈕

指定預設單選按鈕。

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
[在]作為預設值的單選按鈕的 ID。

### <a name="remarks"></a>備註

默認單選按鈕是首次向使用者顯示`CTaskDialog`時 選擇的按鈕。

如果找不到*nRadioButtonID*指定的單選按鈕,此方法將引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a>C任務對話::設定對話寬度

調整的`CTaskDialog`寬度。

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>參數

*n 寬度*<br/>
[在]對話框的寬度(以像素為單位)。

### <a name="remarks"></a>備註

參數*nWidth*必須大於或等於 0。 否則,此方法將引發異常。

如果*nWidth*設置為 0,則此方法將對話方塊設置為預設大小。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a>C 任務對話::設定擴充區域

更新的`CTaskDialog`擴展區域。

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>參數

*放大縮小字型功能 放大縮小字型功能*<br/>
[在]當使用者按一下擴展`CTaskDialog`按鈕 時,對話框正文中顯示的字串。

*str 折疊標籤*<br/>
[在]擴展區域摺疊時`CTaskDialog`顯示在擴展按鈕旁邊的字串。

*str 延伸標籤*<br/>
[在]顯示展開區域時`CTaskDialog`,在擴展按鈕旁邊顯示的字串。

### <a name="remarks"></a>備註

類的`CTaskDialog`擴展區域使您能夠向使用者提供其他資訊。 擴展區域位於的`CTaskDialog`,位於標題和內容字串的正下方。

首次顯示`CTaskDialog`時,它不顯示展開的資訊,`strCollapsedLabel`並放在擴展按鈕旁邊。 當使用者按一下延伸按鈕時`CTaskDialog`, 將顯示*str"擴展資訊*「並將標籤更改為*str」擴展標籤*。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a>CTask對話::SetFooterIcon

更新`CTaskDialog`頁 腳圖示。

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>參數

*hFooterIcon*<br/>
[在]的新圖示`CTaskDialog`。

*lpszFooterIcon*<br/>
[在]的新圖示`CTaskDialog`。

### <a name="remarks"></a>備註

頁腳圖示顯示在[CTaskDialog 類](../../mfc/reference/ctaskdialog-class.md)的底部。 它可以具有關聯的註腳文本。 您可以使用[CTaskDialog 更改註腳文字:setFooterText](#setfootertext)。

如果顯示 或輸入參數為 NULL,`CTaskDialog`則此方法會向[「確保」](diagnostic-services.md#ensure)宏引發異常。

只能`CTaskDialog`接受`HICON``LPCWSTR`或 作為頁腳圖示。 這是透過在建構函數或 CTaskDialog 中設定選項[TDF_USE_HICON_FOOTER::setOption](#setoptions)進行配置的。 預設情況下,`CTaskDialog`配置為用`LPCWSTR`作 頁腳圖示的輸入類型。 如果嘗試使用不適當的類型設置圖示,此方法將生成異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a>CTask對話::設定文字

更新 文上的`CTaskDialog`文字 。

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>參數

*斯特福特文字*<br/>
[在]頁腳的新文字。

### <a name="remarks"></a>備註

頁文圖示顯示在 的頁腳文字`CTaskDialog`旁邊 。 您可以使用[CTaskDialog 更改頁面文圖示::SetFooterIcon](#setfootericon)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a>CTask對話::設定主圖示

更新的主`CTaskDialog`圖示。

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>參數

*hMainIcon*<br/>
[在]新圖示。

*lpszMainIcon*<br/>
[在]新圖示。

### <a name="remarks"></a>備註

如果顯示 或輸入參數為 NULL,`CTaskDialog`則此方法會向[「確保」](diagnostic-services.md#ensure)宏引發異常。

只能`CTaskDialog`接受`HICON``LPCWSTR`或作為主圖示。 您可以通過在建構函數中或[CTaskDialog:setOption](#setoptions)方法中設置TDF_USE_HICON_MAIN選項來設定此選項。 預設情況下,`CTaskDialog`配置為用`LPCWSTR`作 主圖示的輸入類型。 如果嘗試使用不適當的類型設置圖示,此方法將生成異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a>CTask對話::設定主指令

更新的主要`CTaskDialog`指令。

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>參數

*序列指令*<br/>
[在]新的主指令。

### <a name="remarks"></a>備註

`CTaskDialog`類的主要指令是以大粗體顯示給使用者的文本。 它位於標題列下方的對話框中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a>C 任務對話::設定選項

設定的選項`CTaskDialog`。

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>參數

*nOptionFlag*<br/>
[在]以的標籤集`CTaskDialog`。

### <a name="remarks"></a>備註

此方法清除所有目前選項`CTaskDialog`。 若要保留當前選項,必須先使用[CTaskDialog::GetOptions](#getoptions)檢索它們,並將它們與要設置的選項合併。

下表列出了所有有效的選項。

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|啟用`CTaskDialog`中的超連結。|
|TDF_USE_HICON_MAIN|設定為`CTaskDialog`對主`HICON`圖示使用 。 另一種方法是使用`LPCWSTR`。|
|TDF_USE_HICON_FOOTER|設定為`CTaskDialog`使用`HICON`註腳圖示的 。 另一種方法是使用`LPCWSTR`。|
|TDF_ALLOW_DIALOG_CANCELLATION|允許使用者`CTaskDialog`使用鍵盤或使用對話框右上角的圖示關閉 ,即使未啟用 **「取消」** 按鈕也是如此。 如果未設定此標誌,並且未啟用 **「取消」** 按鈕,則使用者無法使用 Alt_F4、Escape 鍵或標題列的關閉按鈕關閉對話方塊。|
|TDF_USE_COMMAND_LINKS|配置`CTaskDialog`要使用的命令按鈕控制項。|
|TDF_USE_COMMAND_LINKS_NO_ICON|配置`CTaskDialog`要使用的命令按鈕控件,而不顯示控件旁邊的圖示。 TDF_USE_COMMAND_LINKS覆蓋TDF_USE_COMMAND_LINKS_NO_ICON。|
|TDF_EXPAND_FOOTER_AREA|指示擴展區域當前已展開。|
|TDF_EXPANDED_BY_DEFAULT|確定預設情況下是否擴展擴展區域。|
|TDF_VERIFICATION_FLAG_CHECKED|指示當前已選擇驗證複選框。|
|TDF_SHOW_PROGRESS_BAR|配置為`CTaskDialog`顯示進度條。|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|將進度列配置為選框進度條。 如果啟用此選項,則必須將TDF_SHOW_PROGRESS_BAR設置為具有預期行為。|
|TDF_CALLBACK_TIMER|指示`CTaskDialog`回調間隔設置為大約 200 毫秒。|
|TDF_POSITION_RELATIVE_TO_WINDOW|配置`CTaskDialog`相對於父視窗要居中。 如果未啟用此標誌,則`CTaskDialog`相對於監視器,居中。|
|TDF_RTL_LAYOUT|設定`CTaskDialog`從右至左讀取佈局的 。|
|TDF_NO_DEFAULT_RADIO_BUTTON|指示`CTaskDialog`出現時未選擇單選按鈕。|
|TDF_CAN_BE_MINIMIZED|使用使用者能夠最小化`CTaskDialog`。 要支援此選項,`CTaskDialog`不能是模態的。 MFC 不支援這個選項,因為 MFC`CTaskDialog`不支援無 模式 。|

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a>CTask對話::設定進度列

為 配置`CTaskDialog`選框列並將其添加到對話方塊中。

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 啟用選取框列;FALSE 以禁用選取框列並從 中`CTaskDialog`刪除 它。

*nMarqueeSpeed*<br/>
[在]指示選框條速度的整數。

### <a name="remarks"></a>備註

選框欄顯示在`CTaskDialog`類的主文本下方。

使用*nMarqueeSpeed*設置選框欄的速度;值越大表示速度較慢。 *nMarqueeSpeed*的值為 0 使選取框條以 Windows 的預設速度移動。

如果*nMarqueeSpeed*小於 0,此方法會向[「確保」](diagnostic-services.md#ensure)宏引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a>C任務對話::設定進度列位置

調整進度條的位置。

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>參數

*n 進步Pos*<br/>
[在]進度條的位置。

### <a name="remarks"></a>備註

如果*nProgressPos*不在進度欄範圍內,則此方法會向[「確保」](diagnostic-services.md#ensure)宏引發異常。 您可以使用[CTaskDialog 更改進度列範圍::設定進度列範圍](#setprogressbarrange)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a>CTask對話::設定進度列範圍

調整進度條的範圍。

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>參數

*恩朗明*<br/>
[在]進度條的下限。

*nRangeMax*<br/>
[在]進度條的上限。

### <a name="remarks"></a>備註

進度列的位置相對於*nRangeMin*和*nRangeMax*。 例如,如果*nRangeMin*為*50,nRangeMax*為 100,則位置為 75 的位置位於進度條的一半。 使用[CTaskDialog:設定進度列位置](#setprogressbarposition)以設定進度列的位置。

要顯示進度條,必須啟用選項TDF_SHOW_PROGRESS_BAR,並且不能啟用TDF_SHOW_MARQUEE_PROGRESS_BAR。 此方法會自動設置TDF_SHOW_PROGRESS_BAR並清除TDF_SHOW_MARQUEE_PROGRESS_BAR。 使用[CTaskDialog::設定選項](#setoptions)以手動更改[CTaskDialog 類](../../mfc/reference/ctaskdialog-class.md)的此實例的選項。

如果*nRangeMin*不小於*nRangeMax,* 則此方法會向["確保"](diagnostic-services.md#ensure)宏引發異常。 如果已顯示 ,並且具有`CTaskDialog`選 框進度列,則此方法還會引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a>C任務對話::設定進度列

設定進度列號的狀態並將顯示在上`CTaskDialog`。

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>參數

*n州*<br/>
[在]進度條的狀態。 有關可能的值,請參閱備註部分。

### <a name="remarks"></a>備註

如果已顯示 ,並且具有選框進度`CTaskDialog`列 ,則此方法會向[「確保」](diagnostic-services.md#ensure)宏引發異常。

下表列出了*nState*的可能值。 在所有這些情況下,進度條將填充常規顏色,直到它到達指定的停止位置。 此時,它將根據狀態更改顏色。

|||
|-|-|
|PBST_NORMAL|進度條填充後,`CTaskDialog`不會更改條形的顏色。 默認情況下,常規顏色為綠色。|
|PBST_ERROR|進度條填充後,`CTaskDialog`將條形的顏色更改為錯誤顏色。 默認情況下,這是紅色的。|
|PBST_PAUSED|進度條填充後,`CTaskDialog`將條形的顏色更改為已暫停的顏色。 默認情況下,這是黃色的。|

您可以使用 CTaskDialog 設定進度列停止的位置[::設定進度列位置](#setprogressbarposition)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a>CTask對話::設定無線按鈕選項

啟用或禁用單選按鈕。

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>參數

*nRadioButtonID*<br/>
[在]單選按鈕控制件的識別碼。

*b 啟用*<br/>
[在]TRUE 啟用單選按鈕;FALSE 以禁用單選按鈕。

### <a name="remarks"></a>備註

如果*nRadioButtonID*不是單選按鈕的有效 ID,則此方法會向["確保"](diagnostic-services.md#ensure)宏引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a>C任務對話::設定驗證複選框

設置驗證複選框的選中狀態。

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>參數

*bChecked*<br/>
[在]TRUE 以在 顯示`CTaskDialog`時選擇 驗證選選框;FALSE 在 顯示 時`CTaskDialog`未選擇驗證選擇的框。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a>CTask對話::設定驗證複選框文字

設置顯示在驗證複選框右側的文本。

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>參數

*str 驗證文字*<br/>
[在]此方法顯示在驗證複選框旁邊的文本。

### <a name="remarks"></a>備註

如果已顯示類的此實例,`CTaskDialog`此方法會向[「確保」](diagnostic-services.md#ensure)宏引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a>C 任務對話::設定視窗標題

設定的標題`CTaskDialog`。

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>參數

*strWindow 標題*<br/>
[在]的新標題`CTaskDialog`。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a>C 任務對話::顯示對話

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

*str 內容*<br/>
[在]用於的內容`CTaskDialog`的字串。

*斯特曼指令*<br/>
[在]的主要指令`CTaskDialog`。

*斯特標題*<br/>
[在]的標題`CTaskDialog`。

*nID 命令控制優先*<br/>
[在]第一個命令的字串 ID。

*nID 命令控制上次*<br/>
[在]最後一個命令的字串 ID。

*n 通用按鈕*<br/>
[在]要添加到`CTaskDialog`的 按鈕的掩碼。

*n 工作對話選項*<br/>
[在]用於的選項`CTaskDialog`集。

*斯特福特*<br/>
[在]要用作頁腳的字串。

### <a name="return-value"></a>傳回值

與使用者所做的選擇對應的整數。

### <a name="remarks"></a>備註

此靜態方法使您能夠建立類的實體,`CTaskDialog`而無需在程式碼中顯式`CTaskDialog`創建 物件。 由於沒有`CTaskDialog`物件`CTaskDialog`, 因此,如果使用此方法向使用者`CTaskDialog`顯示 , 則無法呼叫的任何其他方法。

此方法透過使用來自應用程式的資源檔的資料建立命令按鈕控制項。 資源檔中的字串表具有多個字串與關聯的字串指示。 此方法為*nIDCommandControlsFirst*和*nCommandControlsLast*之間的字串表中的每個有效項目添加命令按鈕控制項,包括。 對於這些命令按鈕控制項,字串表中的字串是控制項的標題,字串 ID 是控制項的識別碼。

關於有效選項的清單,請參閱[CTaskDialog:設定選項](#setoptions)。

當使用者`CTaskDialog`選擇公共按鈕、指令連結控制項或關閉`CTaskDialog`時 關閉 。 返回值是指示使用者如何關閉對話框的標識符。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a>C任務對話::工作對話回調

框架調用此方法以回應各種 Windows 消息。

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

*霍恩德*<br/>
[在]對的結構`m_hWnd``CTaskDialog`的句柄。

*u 通知*<br/>
[在]指定生成的消息的通知代碼。

*wParam*<br/>
[在]有關該消息的詳細資訊。

*lParam*<br/>
[在]有關該消息的詳細資訊。

*dwRefData*<br/>
[在]指向回調消息應用於`CTaskDialog`的物件的指標。

### <a name="return-value"></a>傳回值

取決於特定的通知代碼。 如需詳細資訊，請參閱「備註」一節。

### <a name="remarks"></a>備註

的`TaskDialogCallback`預設實現處理特定消息,然後調用[CTaskDialog 類](../../mfc/reference/ctaskdialog-class.md)的適當的 On 方法。 例如,為了回應TDN_BUTTON_CLICKED消息,`TaskDialogCallback`呼叫[CTaskDialog::OnCommandControl 按一下](#oncommandcontrolclick)。

*wParam*和*lParam*的值取決於特定生成的消息。 這些值或兩個值都可能是空的。 下表列出了支援的預設通知以及*wParam*和*lParam*的值表示的內容。 如果在派生類中重寫此方法,則應為下表中的每條消息實現回調代碼。

|通知訊息|*wParam*價值|*lParam*價值|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|未使用。|未使用。|
|TDN_NAVIGATED|未使用。|未使用。|
|TDN_BUTTON_CLICKED|命令按鈕控制 ID。|未使用。|
|TDN_HYPERLINK_CLICKED|未使用。|包含連結的[LPCWSTR](/windows/win32/WinProg/windows-data-types)結構。|
|TDN_TIMER|創建 或重置計時器`CTaskDialog`以來的時間(以毫秒為單位)。|未使用。|
|TDN_DESTROYED|未使用。|未使用。|
|TDN_RADIO_BUTTON_CLICKED|單選按鈕 ID。|未使用。|
|TDN_DIALOG_CONSTRUCTED|未使用。|未使用。|
|TDN_VERIFICATION_CLICKED|如果選中該複選框,為 1,則為 0(如果不是)。|未使用。|
|TDN_HELP|未使用。|未使用。|
|TDN_EXPANDO_BUTTON_CLICKED|如果擴展區域摺疊,0;如果顯示擴展文本,則非零。|未使用。|

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[逐步解說：將 CTaskDialog 新增至應用程式](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
