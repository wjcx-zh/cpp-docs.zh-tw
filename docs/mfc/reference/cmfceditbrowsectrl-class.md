---
title: CMFCEditBrowseCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
ms.openlocfilehash: db99c5e72e84bb359184f4c62594fcddff7d8ff6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505345"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl 類別

`CMFCEditBrowseCtrl`類別支援 [編輯] [流覽] 控制項, 這是可編輯的文字方塊, 選擇性地包含 [流覽] 按鈕。 當使用者按一下瀏覽按鈕時，控制項就會執行自訂動作或顯示包含檔案瀏覽器或資料夾瀏覽器的標準對話方塊。

## <a name="syntax"></a>語法

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|預設建構函式。|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|啟用或停用 (隱藏) [流覽] 按鈕。|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|啟用 [流覽] 按鈕, 並將 [編輯流覽] 控制項放在檔案*流覽*模式。|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|啟用 [流覽] 按鈕, 並將 [編輯流覽] 控制項放在*資料夾流覽*模式中。|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|傳回目前的瀏覽模式。|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|在編輯流覽控制項更新為流覽動作的結果之後, 由架構呼叫。|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|在使用者按一下 [流覽] 按鈕之後, 由架構呼叫。|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|重新繪製目前的編輯流覽控制項。|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|由架構呼叫以繪製 [流覽] 按鈕。|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|當編輯控制項中輸入了不合法的檔案名時, 由架構呼叫。|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|會先轉譯視窗訊息, 再將它們分派至[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 如需語法和詳細資訊, 請參閱[CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|設定 [流覽] 按鈕的自訂影像。|

## <a name="remarks"></a>備註

使用 [編輯流覽] 控制項來選取檔案或資料夾名稱。 (選擇性) 使用控制項來執行自訂動作 (例如), 以顯示對話方塊。 您可以顯示或不顯示 [流覽] 按鈕, 也可以在按鈕上套用自訂標籤或影像。

[編輯流覽] 控制項的 [*流覽] 模式*會決定是否要顯示 [流覽] 按鈕, 以及按一下按鈕時所發生的動作。 如需詳細資訊, 請參閱[GetMode](#getmode)方法。

`CMFCEditBrowseCtrl`類別支援下列模式。

- **自訂模式**

   當使用者按一下 [流覽] 按鈕時, 就會執行自訂動作。 例如, 您可以顯示應用程式特定的對話方塊。

- **檔案模式**

   當使用者按一下 [流覽] 按鈕時, 會顯示標準的檔案選取對話方塊。

- **資料夾模式**

   當使用者按一下 [流覽] 按鈕時, 就會顯示 [標準資料夾選取範圍] 對話方塊。

## <a name="how-to-specify-an-edit-browse-control"></a>操作說明：指定編輯流覽控制項

請執行下列步驟, 在您的應用程式中併入編輯流覽控制項:

1. 如果您想要執行自訂瀏覽模式, 請從`CMFCEditBrowseCtrl`類別衍生您自己的類別, 然後覆寫[CMFCEditBrowseCtrl:: OnBrowse](#onbrowse)方法。 在覆寫的方法中, 執行自訂的流覽動作, 並以結果更新 [編輯流覽] 控制項。

1. `CMFCEditBrowseCtrl`將物件或衍生的編輯流覽控制項物件內嵌到父視窗物件中。

1. 如果您使用 [**類別] Wizard**建立對話方塊, 請將編輯控制項 ( `CEdit`) 新增至對話方塊表單。 此外, 新增變數以存取標頭檔中的控制項。 在您的標頭檔中, 將變數的類型從`CEdit`變更`CMFCEditBrowseCtrl`為。 [編輯流覽] 控制項將會自動建立。 如果您未使用**類別 Wizard**, 請將`CMFCEditBrowseCtrl`變數新增至標頭檔, 然後呼叫其`Create`方法。

1. 如果您將 [編輯流覽] 控制項加入對話方塊中, 請使用**ClassWizard**工具來設定資料交換。

1. 呼叫[EnableFolderBrowseButton](#enablefolderbrowsebutton)、 [EnableFileBrowseButton](#enablefilebrowsebutton)或[EnableBrowseButton](#enablebrowsebutton)方法來設定瀏覽模式, 並顯示 [流覽] 按鈕。 呼叫[GetMode](#getmode)方法, 以取得目前的瀏覽模式。

1. 若要提供 [流覽] 按鈕的自訂影像, 請呼叫[SetBrowseButtonImage](#setbrowsebuttonimage)方法, 或覆寫[OnDrawBrowseButton](#ondrawbrowsebutton)方法。

1. 若要從 [編輯流覽] 控制項移除 [流覽] 按鈕, 請呼叫[EnableBrowseButton](#enablebrowsebutton)方法, 並將*bEnable*參數設定為 FALSE。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>範例

下列範例示範如何在`CMFCEditBrowseCtrl`類別中使用兩個方法: `EnableFolderBrowseButton`和`EnableFileBrowseButton`。 這個範例是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>需求

**標頭:** afxeditbrowsectrl。h

##  <a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl:: EnableBrowseButton

顯示或不會在目前的編輯流覽控制項上顯示 [流覽] 按鈕。

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>參數

*bEnable*<br/>
TRUE 表示要顯示 [流覽] 按鈕;FALSE 則不會顯示 [流覽] 按鈕。 預設值為 TRUE。

*szLabel*<br/>
顯示在 [流覽] 按鈕上的標籤。 預設值為 " **...** "。

### <a name="remarks"></a>備註

如果*bEnable*參數為 TRUE, 請在按下 [流覽] 按鈕時, 執行自訂動作來執行。 若要執行自訂動作, 請從`CMFCEditBrowseCtrl`類別衍生一個類別, 然後覆寫它的[OnBrowse](#onbrowse)方法。

如果*bEnable*參數為 TRUE, 則控制項`BrowseMode_Default`的瀏覽模式為, 否則瀏覽模式為。 `BrowseMode_None` 如需瀏覽模式的詳細資訊, 請參閱[GetMode](#getmode)方法。

##  <a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl:: EnableFileBrowseButton

顯示目前編輯流覽控制項的 [流覽] 按鈕, 並將控制項置於檔案*流覽*模式。

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>參數

*lpszDefExt*<br/>
指定用於檔案選取對話方塊中的預設副檔名。 預設值為 Null。

*lpszFilter*<br/>
指定用於檔案選取對話方塊中的預設篩選字串。 預設值為 Null。

*dwFlags*<br/>
對話方塊旗標。 預設值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的位元組合 (OR)。

### <a name="remarks"></a>備註

當編輯瀏覽控制項處於檔案瀏覽模式時，若使用者按一下 [瀏覽] 按鈕，控制項將會顯示標準檔案選取對話方塊。

如需可用旗標的完整清單, 請參閱[OPENFILENAME 結構](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)。

##  <a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl:: EnableFolderBrowseButton

顯示目前編輯流覽控制項的 [流覽] 按鈕, 並將控制項置於*資料夾流覽*模式。

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>備註

當編輯流覽控制項在資料夾瀏覽模式中, 且使用者按一下 [流覽] 按鈕時, 控制項會顯示 [標準資料夾選取範圍] 對話方塊。

##  <a name="getmode"></a>CMFCEditBrowseCtrl:: GetMode

抓取目前編輯流覽控制項的瀏覽模式。

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>傳回值

其中一個列舉值, 指定編輯流覽控制項的目前模式。 [流覽] 模式會決定架構是否顯示 [流覽] 按鈕, 以及當使用者按一下該按鈕時, 會發生什麼動作。

下表列出可能的傳回值。

|值|描述|
|-----------|-----------------|
|`BrowseMode_Default`|**自訂模式**。 執行程式設計人員定義的動作。|
|`BrowseMode_File`|檔案**模式**。 [標準檔案瀏覽器] 對話方塊隨即顯示。|
|`BrowseMode_Folder`|**資料夾模式**。 [標準資料夾瀏覽器] 對話方塊隨即顯示。|
|`BrowseMode_None`|[流覽] 按鈕不會顯示。|

### <a name="remarks"></a>備註

根據預設, `CMFCEditBrowseCtrl`物件會初始化為`BrowseMode_None`模式。 使用[CMFCEditBrowseCtrl:: EnableBrowseButton](#enablebrowsebutton)、 [CMFCEditBrowseCtrl:: EnableFileBrowseButton](#enablefilebrowsebutton)和[CMFCEditBrowseCtrl:: EnableFolderBrowseButton](#enablefolderbrowsebutton)方法修改瀏覽模式。

##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl:: OnAfterUpdate

在編輯流覽控制項更新為流覽動作的結果之後, 由架構呼叫。

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>備註

在衍生類別中覆寫這個方法, 以執行自訂動作。

##  <a name="onbrowse"></a>CMFCEditBrowseCtrl:: OnBrowse

在使用者按一下 [編輯流覽] 控制項的 [流覽] 按鈕之後, 由架構呼叫。

```
virtual void OnBrowse();
```

### <a name="remarks"></a>備註

當使用者按一下 [編輯流覽] 控制項的 [流覽] 按鈕時, 請使用這個方法來執行自訂程式碼。 從`CMFCEditBrowseCtrl`類別衍生您自己的類別, 並覆`OnBrowse`寫其方法。 在該方法中, 執行自訂的流覽動作, 並選擇性地更新編輯流覽控制項的文字方塊。 在您的應用程式中, 使用[EnableBrowseButton](#enablebrowsebutton)方法, 將 [編輯流覽] 控制項放在*自訂流覽*模式。

##  <a name="onchangelayout"></a>CMFCEditBrowseCtrl:: OnChangeLayout

重新繪製目前的編輯流覽控制項。

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>備註

當編輯流覽控制項的瀏覽模式變更時, 架構會呼叫這個方法。 如需詳細資訊, 請參閱[CMFCEditBrowseCtrl:: GetMode](#getmode)。

##  <a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl:: OnDrawBrowseButton

由架構呼叫, 以在編輯流覽控制項上繪製 [流覽] 按鈕。

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>參數

*pDC*<br/>
裝置內容的指標。

[週框]<br/>
[流覽] 按鈕的周框。

*bIsButtonPressed*<br/>
如果按鈕已按下, 則為 TRUE;否則為 FALSE。

*bIsButtonHot*<br/>
如果按鈕已反白顯示, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

覆寫衍生類別中的這個函式, 以自訂 [流覽] 按鈕的外觀。

##  <a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl:: SetBrowseButtonImage

在 [編輯流覽] 控制項的 [流覽] 按鈕上設定自訂影像。

```
void SetBrowseButtonImage(
    HICON hIcon,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(UINT uiBmpResId);
```

### <a name="parameters"></a>參數

*hIcon*<br/>
圖示的控制碼。

*hBitmap*<br/>
點陣圖的控制碼。

*uiBmpResId*<br/>
點陣圖的資源識別碼。

*bAutoDestroy*<br/>
TRUE 表示在此方法結束時刪除指定的圖示或點陣圖;否則為 FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

使用此方法可將自訂影像套用至 [流覽] 按鈕。 根據預設, 當 [編輯流覽] 控制項處於 *[檔案流覽]* 或 *[資料夾流覽*] 模式時, 架構會取得標準影像。

##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName

當編輯控制項中輸入了不合法的檔案名時, 由架構呼叫。

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>參數

*strFileName*<br/>
指定不正確的檔案名。

### <a name="return-value"></a>傳回值

如果無法將此檔案名進一步傳遞至檔案對話方塊, 則應該傳回 FALSE。 在此情況下, 焦點會設回編輯控制項, 使用者應該繼續編輯。 預設的執行會顯示訊息方塊, 告知使用者不合法的檔案名, 並傳回 FALSE。 您可以覆寫這個方法、更正檔案名, 並傳回 TRUE 進行進一步的處理。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
