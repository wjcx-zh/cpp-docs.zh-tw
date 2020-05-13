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
ms.openlocfilehash: d542af4a87b6f0a33c0344d1d3da76980f8c1a91
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752375"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl 類別

該`CMFCEditBrowseCtrl`類支援編輯流覽控制項,這是一個可編輯的文本框,可選包含瀏覽按鈕。 當使用者按一下瀏覽按鈕時，控制項就會執行自訂動作或顯示包含檔案瀏覽器或資料夾瀏覽器的標準對話方塊。

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
|[CMFCEdit 瀏覽Ctrl::啟用瀏覽按鈕](#enablebrowsebutton)|啟用或禁用(隱藏)瀏覽按鈕。|
|[CMFCEdit 瀏覽Ctrl::啟用檔案瀏覽按鈕](#enablefilebrowsebutton)|啟用流覽按鈕並將編輯流覽控制項置於*檔案瀏覽*模式。|
|[CMFCEdit 瀏覽Ctrl::啟用資料夾瀏覽按鈕](#enablefolderbrowsebutton)|啟用流覽按鈕並將編輯流覽控制項置於*資料夾瀏覽*模式。|
|[CMFCEdit 瀏覽Ctrl:取得模式](#getmode)|返回當前流覽模式。|
|[CMFCEdit 瀏覽Ctrl:在更新後開啟](#onafterupdate)|編輯流覽控制件使用流覽操作的結果更新後由框架調用。|
|[CMFCEdit 流覽Ctrl::在流覽](#onbrowse)|用戶按一下瀏覽按鈕後由框架呼叫。|
|[CMFCEdit 流覽Ctrl::在更改佈局上](#onchangelayout)|重繪目前編輯流覽控制元件。|
|[CMFCEdit 流覽Ctrl::在繪製瀏覽按鈕](#ondrawbrowsebutton)|由框架調用以繪製瀏覽按鈕。|
|[CMFCEdit 流覽Ctrl:在非法檔名上](#onillegalfilename)|在編輯控制項中輸入非法檔名時由框架調用。|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|在視窗訊息發送到[翻譯訊息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[調度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)視窗功能之前進行翻譯。 有關語法和更多資訊,請參閱[CWnd::P重新翻譯消息](../../mfc/reference/cwnd-class.md#pretranslatemessage)。|
|[CMFCEdit 瀏覽Ctrl::設定瀏覽按鈕影像](#setbrowsebuttonimage)|為流覽按鈕設置自定義圖像。|

## <a name="remarks"></a>備註

使用編輯流覽控制項選擇檔或資料夾名稱。 或者,使用控制項執行自訂操作,例如顯示對話方塊。 您可以顯示或不顯示瀏覽按鈕,也可以在按鈕上應用自定義標籤或圖像。

編輯*流覽控制項的瀏覽模式*確定它是否顯示瀏覽按鈕,以及按下這個按鈕時將執行什麼操作。 有關詳細資訊,請參閱[GetMode](#getmode)方法。

該`CMFCEditBrowseCtrl`類支援以下模式。

- **自訂模式**

   當用戶按一下瀏覽按鈕時,將執行自定義操作。 例如,可以顯示特定於應用程式的對話方塊。

- **檔案模式**

   當用戶按一下瀏覽按鈕時,將顯示一個標準檔選擇對話方塊。

- **資料夾模式**

   當用戶按一下瀏覽按鈕時,將顯示一個標準資料夾選擇對話方塊。

## <a name="how-to-specify-an-edit-browse-control"></a>如何:指定編輯瀏覽控制項

執行以下步驟以在應用程式中合併編輯瀏覽控制元件:

1. 如果要實現自定義流覽模式,請`CMFCEditBrowseCtrl`從 類派生您自己的類,然後重寫[CMFCEditBrowseCtrl::onBrowse](#onbrowse)方法。 在重寫方法中,執行自定義流覽操作,並隨結果更新編輯流覽控制元件。

1. 將`CMFCEditBrowseCtrl`物件或派生的編輯流覽控制控制件物件嵌入到父視窗物件中。

1. 如果使用**類別精靈**建立對話框,請向對話框表單新增編輯控制件`CEdit`( 。 此外,添加變數以訪問標頭檔中的控制項。 在標頭檔中,將變數的類型從`CEdit`變更為`CMFCEditBrowseCtrl`。 將自動建立編輯流覽控制元件。 如果不使用**類嚮導**,請向標頭檔添加`CMFCEditBrowseCtrl`變數 ,然後調`Create`用其 方法。

1. 如果將編輯流覽控制元件添加到對話方塊中,請使用**ClassWizard**工具設置數據交換。

1. 呼叫[啟用資料夾瀏覽按鈕](#enablefolderbrowsebutton),[啟用檔案瀏覽按鈕](#enablefilebrowsebutton),或[啟用瀏覽按鈕](#enablebrowsebutton)方法,以設定瀏覽模式並顯示流覽按鈕。 調用[GetMode](#getmode)方法以獲取當前瀏覽模式。

1. 要為瀏覽按鈕提供自訂圖像,請調用[SetBrowseButtonImage](#setbrowsebuttonimage)方法或重寫[OnDrawBrowseButton](#ondrawbrowsebutton)方法。

1. 要從編輯流覽控制元件中刪除瀏覽按鈕,請呼叫[啟用BrowseButton](#enablebrowsebutton)方法,將*bEnable*參數設置為FALSE。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>範例

下面的範例展示如何在`CMFCEditBrowseCtrl`類別使用兩種方法:`EnableFolderBrowseButton`與`EnableFileBrowseButton`。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>需求

**標題:** afxeditbrowsectrl.h

## <a name="cmfceditbrowsectrlenablebrowsebutton"></a><a name="enablebrowsebutton"></a>CMFCEdit 瀏覽Ctrl::啟用瀏覽按鈕

顯示或不在當前編輯流覽控制件上顯示流覽按鈕。

```cpp
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
TRUE 顯示瀏覽按鈕;FALSE 不顯示瀏覽按鈕。 預設值為 TRUE。

*szLabel*<br/>
瀏覽按鈕上顯示的標籤。 默認值為 **"..."。**

### <a name="remarks"></a>備註

如果*bEnable*參數為 TRUE,則實現自訂操作,以便在按一下瀏覽按鈕時執行。 要實現自定義操作,請從類派生一個`CMFCEditBrowseCtrl`類,然後重寫其[OnBrowse](#onbrowse)方法。

如果*bEnable*參數為 TRUE,則控制元件`BrowseMode_Default`的瀏覽模式 為 ;否則,瀏覽模式`BrowseMode_None`為 。 有關流覽模式的詳細資訊,請參閱[GetMode](#getmode)方法。

## <a name="cmfceditbrowsectrlenablefilebrowsebutton"></a><a name="enablefilebrowsebutton"></a>CMFCEdit 瀏覽Ctrl::啟用檔案瀏覽按鈕

在當前編輯流覽控制件上顯示流覽按鈕,並將控制項置於*檔案流覽*模式。

```cpp
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>參數

*lpszDefExt*<br/>
指定用於檔案選取對話方塊中的預設副檔名。 預設值是 NULL。

*lpszFilter*<br/>
指定用於檔案選取對話方塊中的預設篩選字串。 預設值是 NULL。

*dwFlags*<br/>
對話方塊旗標。 預設值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的位元組合 (OR)。

### <a name="remarks"></a>備註

當編輯瀏覽控制項處於檔案瀏覽模式時，若使用者按一下 [瀏覽] 按鈕，控制項將會顯示標準檔案選取對話方塊。

關於可用的旗標的清單,請參閱[OPENFILENAME 結構](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)。

## <a name="cmfceditbrowsectrlenablefolderbrowsebutton"></a><a name="enablefolderbrowsebutton"></a>CMFCEdit 瀏覽Ctrl::啟用資料夾瀏覽按鈕

在當前編輯流覽控制件上顯示流覽按鈕,並將該控制件置於*資料夾流覽*模式。

```cpp
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>備註

當編輯流覽控制控制項處於資料夾瀏覽模式,並且使用者按一下流覽按鈕時,該控制項將顯示標準資料夾選擇對話方塊。

## <a name="cmfceditbrowsectrlgetmode"></a><a name="getmode"></a>CMFCEdit 瀏覽Ctrl:取得模式

檢索當前編輯流覽控制件的流覽模式。

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>傳回值

指定編輯流覽控制件的當前模式的枚舉值之一。 瀏覽模式確定框架是否顯示瀏覽按鈕,以及當用戶按下該按鈕時將執行什麼操作。

下表列出可能的傳回值。

|值|描述|
|-----------|-----------------|
|`BrowseMode_Default`|**自訂模式**。 執行程式師定義的操作。|
|`BrowseMode_File`|**檔案模式**. 將顯示標準文件瀏覽器對話方塊。|
|`BrowseMode_Folder`|**資料夾模式**。 將顯示標準資料夾瀏覽器對話方塊。|
|`BrowseMode_None`|不顯示瀏覽按鈕。|

### <a name="remarks"></a>備註

默認情況下,`CMFCEditBrowseCtrl`物件被初始化`BrowseMode_None`為模式。 使用[CMFCEditBrowseCtrl 修改流覽模式::啟用流覽按鈕](#enablebrowsebutton)[、CMFCEditBrowseCtrl::啟用文件流覽按鈕](#enablefilebrowsebutton)和[CMFCEditBrowseCtrl::啟用資料夾瀏覽按鈕](#enablefolderbrowsebutton)方法。

## <a name="cmfceditbrowsectrlonafterupdate"></a><a name="onafterupdate"></a>CMFCEdit 瀏覽Ctrl:在更新後開啟

編輯流覽控制件使用流覽操作的結果更新後由框架調用。

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>備註

重寫派生類中的此方法以實現自定義操作。

## <a name="cmfceditbrowsectrlonbrowse"></a><a name="onbrowse"></a>CMFCEdit 流覽Ctrl::在流覽

使用者按一下編輯流覽控制件的瀏覽按鈕後由框架呼叫。

```
virtual void OnBrowse();
```

### <a name="remarks"></a>備註

當用戶按一下編輯流覽控制元件的瀏覽按鈕時,使用此方法執行自訂代碼。 從`CMFCEditBrowseCtrl`類派生您自己的類並重寫`OnBrowse`其 方法。 在該方法中,實現自定義流覽操作,並選擇更新編輯流覽控制元件的文本框。 在應用程式中,使用[啟用BrowseButton](#enablebrowsebutton)方法將編輯流覽控制項元件置於*自訂流覽*模式。

## <a name="cmfceditbrowsectrlonchangelayout"></a><a name="onchangelayout"></a>CMFCEdit 流覽Ctrl::在更改佈局上

重繪目前編輯流覽控制元件。

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>備註

當編輯流覽控制元件的流覽模式發生更改時,框架將調用此方法。 有關詳細資訊,請參閱[CMFCEditBrowseCtrl::取得模式](#getmode)。

## <a name="cmfceditbrowsectrlondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCEdit 流覽Ctrl::在繪製瀏覽按鈕

框架呼叫以在編輯流覽控制元件上繪製流覽按鈕。

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

*Rect*<br/>
瀏覽按鈕的邊界矩形。

*bIsButton壓榨*<br/>
如果按下按鈕,則為 TRUE;否則,FALSE。

*bIsButtonHot*<br/>
如果按鈕突出顯示,則為 TRUE;如果按鈕突出顯示,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

在派生類中重寫此函數以自定義流覽按鈕的外觀。

## <a name="cmfceditbrowsectrlsetbrowsebuttonimage"></a><a name="setbrowsebuttonimage"></a>CMFCEdit 瀏覽Ctrl::設定瀏覽按鈕影像

在編輯流覽控制件的流覽按鈕上設置自定義圖像。

```cpp
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
圖示的句柄。

*hBitmap*<br/>
位圖的句柄。

*烏布佈雷西德*<br/>
位圖的資源識別碼。

*bAuto銷毀*<br/>
TRUE 在此方法退出時刪除指定的圖示或位圖;否則,FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

使用此方法將自定義圖像應用於瀏覽按鈕。 預設情況下,當編輯流覽控制控制件處於*文件流覽*或*資料夾流覽*模式時,框架將獲取標準圖像。

## <a name="cmfceditbrowsectrlonillegalfilename"></a><a name="onillegalfilename"></a>CMFCEdit 流覽Ctrl:在非法檔名上

在編輯控制項中輸入非法檔名時由框架調用。

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>參數

*strFilename*<br/>
指定非法檔名。

### <a name="return-value"></a>傳回值

如果無法將此檔名進一步傳遞到文件對話框,則應返回 FALSE。 在這種情況下,焦點將設置回編輯控件,使用者應繼續編輯。 默認實現顯示一個消息框,告知使用者非法檔名並返回 FALSE。 您可以重寫此方法、更正檔名並返回 TRUE 以進行進一步處理。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
