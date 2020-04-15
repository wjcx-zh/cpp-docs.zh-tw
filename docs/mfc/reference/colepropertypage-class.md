---
title: COlePropertyPage 類別
ms.date: 11/04/2016
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::OVERWRITEApply
- AFXCTL/COlePropertyPage::IsModified
- AFXCTL/COlePropertyPage::OnEditProperty
- AFXCTL/COlePropertyPage::OnHelp
- AFXCTL/COlePropertyPage::OnInitDialog
- AFXCTL/COlePropertyPage::OnObjectsChanged
- AFXCTL/COlePropertyPage::OnSetPageSite
- AFXCTL/COlePropertyPage::SetControlStatus
- AFXCTL/COlePropertyPage::SetDialogResource
- AFXCTL/COlePropertyPage::SetHelpInfo
- AFXCTL/COlePropertyPage::SetModifiedFlag
- AFXCTL/COlePropertyPage::SetPageName
helpviewer_keywords:
- COlePropertyPage [MFC], COlePropertyPage
- COlePropertyPage [MFC], GetControlStatus
- COlePropertyPage [MFC], GetObjectArray
- COlePropertyPage [MFC], GetPageSite
- COlePropertyPage [MFC], IgnoreApply
- COlePropertyPage [MFC], IsModified
- COlePropertyPage [MFC], OnEditProperty
- COlePropertyPage [MFC], OnHelp
- COlePropertyPage [MFC], OnInitDialog
- COlePropertyPage [MFC], OnObjectsChanged
- COlePropertyPage [MFC], OnSetPageSite
- COlePropertyPage [MFC], SetControlStatus
- COlePropertyPage [MFC], SetDialogResource
- COlePropertyPage [MFC], SetHelpInfo
- COlePropertyPage [MFC], SetModifiedFlag
- COlePropertyPage [MFC], SetPageName
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
ms.openlocfilehash: dbdc889e244b33365756bcbae5b37cf657a6d900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374885"
---
# <a name="colepropertypage-class"></a>COlePropertyPage 類別

用來將自訂控制項的屬性顯示在類似對話方塊的圖形介面中。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COle 屬性頁:COle屬性頁](#colepropertypage)|建構 `COlePropertyPage` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle 屬性頁:取得控制狀態](#getcontrolstatus)|指示使用者是否已修改控制項中的值。|
|[COle 屬性頁:取得物件陣列](#getobjectarray)|返回屬性頁正在編輯的物件陣列。|
|[COle 屬性頁面:取得頁面網站](#getpagesite)|返回指向屬性頁介面的`IPropertyPageSite`指標。|
|[COle 屬性頁:忽略應用程式](#ignoreapply)|確定哪些控制項不啟用"應用程式"按鈕。|
|[COle 屬性頁:已修改](#ismodified)|指示使用者是否已修改屬性頁。|
|[COle 屬性頁:編輯屬性](#oneditproperty)|當使用者編輯屬性時由框架調用。|
|[COle 屬性頁面:上説明](#onhelp)|當用戶調用説明時由框架調用。|
|[COle 屬性頁:onInitDialog](#oninitdialog)|在初始化屬性頁時由框架調用。|
|[COle 屬性頁:開啟物件已變更](#onobjectschanged)|當選擇另一個 OLE 控制件(具有新屬性)時,由框架調用。|
|[COle 屬性頁面:在設定頁面網站](#onsetpagesite)|當屬性框架提供頁面的網站時,由框架調用。|
|[COle 屬性頁:設定控制狀態](#setcontrolstatus)|設置一個標誌,指示使用者是否已修改控制項中的值。|
|[COle 屬性頁:設定對話資源](#setdialogresource)|設置屬性頁的對話方塊資源。|
|[COle 屬性頁面:設定說明資訊](#sethelpinfo)|設置屬性頁的簡短説明文本、其幫助文件的名稱及其説明上下文。|
|[COle 屬性頁::設定修改後的 Flag](#setmodifiedflag)|設置指示使用者是否修改了屬性頁的標誌。|
|[COle 屬性頁::設定頁面名稱](#setpagename)|設置屬性頁的名稱(標題)。|

## <a name="remarks"></a>備註

例如,屬性頁可能包含一個編輯控制項,允許使用者查看和修改控制項的標題屬性。

每個自定義控制項屬性都可以具有一個對話方塊控制項,該控制項允許使用者查看當前屬性值並根據需要修改該值。

有關`COlePropertyPage`使用的詳細資訊,請參閱[「ActiveX 控件:屬性頁](../../mfc/mfc-activex-controls-property-pages.md)」一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>需求

**標題:** afxctl.h

## <a name="colepropertypagecolepropertypage"></a><a name="colepropertypage"></a>COle 屬性頁:COle屬性頁

建構 `COlePropertyPage` 物件。

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>參數

*idDlg*<br/>
對話框範本的資源 ID。

*idCaption*<br/>
屬性頁標題的資源識別碼。

### <a name="remarks"></a>備註

實現`COlePropertyPage`子 類的子類時,子類的構造函數`COlePropertyPage`應使用 建構函數來標識屬性頁所基於的對話方塊範本資源和包含其標題的字串資源。

## <a name="colepropertypagegetcontrolstatus"></a><a name="getcontrolstatus"></a>COle 屬性頁:取得控制狀態

確定使用者是否已使用指定的資源 ID 修改屬性頁控制項的值。

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
屬性頁控制件的資源 ID。

### <a name="return-value"></a>傳回值

如果控件值已被修改,則為 TRUE;否則 FALSE。

## <a name="colepropertypagegetobjectarray"></a><a name="getobjectarray"></a>COle 屬性頁:取得物件陣列

返回屬性頁正在編輯的物件陣列。

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>參數

*pn物件*<br/>
指向未簽名的長整數的指標,該整數將接收頁面正在編輯的物件數。

### <a name="return-value"></a>傳回值

指向指標陣列的`IDispatch`指標,用於訪問屬性頁上每個控制件的屬性。 調用方不得釋放這些介面指標。

### <a name="remarks"></a>備註

每個屬性頁物件都維護指向頁面正在編輯的物件`IDispatch`的介面的指標陣列。 此函數將其*pnObjects*參數設置為該陣列中的元素數,並返回指向陣列第一個元素的指標。

## <a name="colepropertypagegetpagesite"></a><a name="getpagesite"></a>COle 屬性頁面:取得頁面網站

獲取指向屬性頁介面的`IPropertyPageSite`指標。

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>傳回值

指向屬性頁介面的`IPropertyPageSite`指標。

### <a name="remarks"></a>備註

控制件和容器相互配合,以便使用者可以流覽和編輯控制項屬性。 該控件提供屬性頁,每個屬性頁都是一個 OLE 物件,允許使用者編輯一組相關的屬性。 容器提供顯示屬性頁的屬性框架。 對於每個頁面,屬性框架提供一個頁面網站,該頁網站`IPropertyPageSite`支援該介面。

## <a name="colepropertypageignoreapply"></a><a name="ignoreapply"></a>COle 屬性頁:忽略應用程式

確定哪些控制項不啟用"應用程式"按鈕。

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
要忽略的控制項的 ID。

### <a name="remarks"></a>備註

僅當更改屬性頁控件的值時,才啟用屬性頁的"應用"按鈕。 使用此函數可以指定在值更改時不會啟用"應用"按鈕的控制項。

## <a name="colepropertypageismodified"></a><a name="ismodified"></a>COle 屬性頁:已修改

確定使用者是否已更改屬性頁上的任何值。

```
BOOL IsModified();
```

### <a name="return-value"></a>傳回值

如果屬性頁已被修改,則為 TRUE。

## <a name="colepropertypageoneditproperty"></a><a name="oneditproperty"></a>COle 屬性頁:編輯屬性

當要編輯特定屬性時,框架將調用此函數。

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>參數

*不一部分*<br/>
要編輯的屬性的調度 ID。

### <a name="return-value"></a>傳回值

預設實現返回 FALSE。 此函數的重寫應返回 TRUE。

### <a name="remarks"></a>備註

您可以重寫它,將焦點設定為頁面上的相應控制項。 默認實現不執行任何操作,並返回 FALSE。

## <a name="colepropertypageonhelp"></a><a name="onhelp"></a>COle 屬性頁面:上説明

當使用者請求連線説明時,框架將調用此功能。

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>參數

*lpszHelpDir*<br/>
包含屬性頁幫助檔的目錄。

### <a name="return-value"></a>傳回值

預設實現返回 FALSE。

### <a name="remarks"></a>備註

如果屬性頁必須在使用者訪問説明時執行任何特殊操作,請覆蓋它。 預設實現不執行任何操作,並返回 FALSE,它指示框架調用 WinHelp。

## <a name="colepropertypageoninitdialog"></a><a name="oninitdialog"></a>COle 屬性頁:onInitDialog

在初始化屬性頁的對話框時,框架將調用此函數。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

預設實現返回 FALSE。

### <a name="remarks"></a>備註

如果對話框初始化時需要任何特殊操作,則覆蓋它。 默認實現調用`CDialog::OnInitDialog`並返回 FALSE。

## <a name="colepropertypageonobjectschanged"></a><a name="onobjectschanged"></a>COle 屬性頁:開啟物件已變更

當選擇另一個 OLE 控制件(具有新屬性)時,由框架調用。

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>備註

在開發人員環境中查看 OLE 控制的屬性時,將使用無模式對話框來顯示其屬性頁。 如果選擇了另一個控制項,則必須為新屬性集顯示一組不同的屬性頁。 框架呼叫此函數以通知更改的屬性頁。

重寫此函數以接收此操作的通知並執行任何特殊操作。

## <a name="colepropertypageonsetpagesite"></a><a name="onsetpagesite"></a>COle 屬性頁面:在設定頁面網站

當屬性框架提供屬性頁的頁面網站時,框架將調用此函數。

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>備註

預設實現載入頁面的標題,並嘗試從對話方塊資源確定頁面的大小。 如果屬性頁需要任何進一步操作,請覆蓋此函數;重寫應調用基類實現。

## <a name="colepropertypagesetcontrolstatus"></a><a name="setcontrolstatus"></a>COle 屬性頁:設定控制狀態

更改屬性頁控件的狀態。

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>參數

*nID*<br/>
包含屬性頁控制件的 ID。

*bDirty*<br/>
指定屬性頁的欄位是否已被修改。 如果欄位已被修改,則設置為 TRUE;如果未修改該欄位,則為 FALSE。

### <a name="return-value"></a>傳回值

如果設置了指定的控制項,則為 TRUE;如果設置了指定的控制項。否則 FALSE。

### <a name="remarks"></a>備註

如果在關閉屬性頁或選擇"應用"按鈕時屬性頁控件的狀態為臟,則控件的屬性將使用相應的值進行更新。

## <a name="colepropertypagesetdialogresource"></a><a name="setdialogresource"></a>COle 屬性頁:設定對話資源

設置屬性頁的對話方塊資源。

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>參數

*h對話*<br/>
處理屬性頁的對話方塊資源。

## <a name="colepropertypagesethelpinfo"></a><a name="sethelpinfo"></a>COle 屬性頁面:設定說明資訊

指定工具提示資訊、幫助檔名和屬性頁的説明上下文。

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>參數

*lpszDocString*<br/>
包含用於在狀態列或其他位置顯示的簡短説明資訊的字串。

*lpszHelp 檔案*<br/>
屬性頁幫助檔的名稱。

*dwHelpContext*<br/>
屬性頁的説明上下文。

## <a name="colepropertypagesetmodifiedflag"></a><a name="setmodifiedflag"></a>COle 屬性頁::設定修改後的 Flag

指示使用者是否已修改屬性頁。

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>參數

*b 修改*<br/>
指定屬性頁已修改標誌的新值。

## <a name="colepropertypagesetpagename"></a><a name="setpagename"></a>COle 屬性頁::設定頁面名稱

設置屬性頁的名稱,屬性框架通常會顯示在頁面的選項卡上。

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>參數

*lpszPage 名稱*<br/>
指向包含屬性頁名稱的字串的指標。

## <a name="see-also"></a>另請參閱

[MFC 樣品 CIRC3](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品測試](../../overview/visual-cpp-samples.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
