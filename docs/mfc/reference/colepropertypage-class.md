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
ms.openlocfilehash: 8253b2c2fa6b93ec51c7ede983ef710eed039970
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421090"
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
|[COlePropertyPage：： COlePropertyPage](#colepropertypage)|建構 `COlePropertyPage` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COlePropertyPage：： GetControlStatus](#getcontrolstatus)|指出使用者是否已修改控制項中的值。|
|[COlePropertyPage：： GetObjectArray](#getobjectarray)|傳回屬性頁正在編輯的物件陣列。|
|[COlePropertyPage：： GetPageSite](#getpagesite)|傳回屬性頁之 `IPropertyPageSite` 介面的指標。|
|[COlePropertyPage：： IgnoreApply](#ignoreapply)|決定哪些控制項未啟用 [套用] 按鈕。|
|[COlePropertyPage：： IsModified](#ismodified)|指出使用者是否已修改屬性頁。|
|[COlePropertyPage：： OnEditProperty](#oneditproperty)|當使用者編輯屬性時由架構呼叫。|
|[COlePropertyPage：： OnHelp](#onhelp)|當使用者叫用說明時由架構呼叫。|
|[COlePropertyPage：： OnInitDialog](#oninitdialog)|在初始化屬性頁時由架構呼叫。|
|[COlePropertyPage：： OnObjectsChanged](#onobjectschanged)|當選擇另一個具有新屬性的 OLE 控制項時，由架構呼叫。|
|[COlePropertyPage：： Onsetpagesite 中](#onsetpagesite)|當屬性框架提供頁面的網站時，由架構呼叫。|
|[COlePropertyPage：： SetControlStatus](#setcontrolstatus)|設定旗標，指出使用者是否已修改控制項中的值。|
|[COlePropertyPage：： SetDialogResource](#setdialogresource)|設定屬性頁的對話資源。|
|[COlePropertyPage：：含有 sethelpinfo](#sethelpinfo)|設定屬性頁的簡短解說文字、其說明檔的名稱，以及其說明內容。|
|[COlePropertyPage：： SetModifiedFlag](#setmodifiedflag)|設定旗標，指出使用者是否已修改屬性頁。|
|[COlePropertyPage：： SetPageName](#setpagename)|設定屬性頁的名稱（標題）。|

## <a name="remarks"></a>備註

例如，屬性頁可能會包含編輯控制項，讓使用者可以查看和修改控制項的 caption 屬性。

每個自訂或內建控制項屬性都可以有一個對話方塊控制項，讓控制項的使用者能夠查看目前的屬性值，並在必要時修改該值。

如需使用 `COlePropertyPage`的詳細資訊，請參閱[ActiveX 控制項：屬性頁](../../mfc/mfc-activex-controls-property-pages.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>需求

**標頭：** afxctl.h。h

##  <a name="colepropertypage"></a>COlePropertyPage：： COlePropertyPage

建構 `COlePropertyPage` 物件。

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>參數

*idDlg*<br/>
對話方塊範本的資源識別碼。

*idCaption*<br/>
屬性頁標題的資源識別碼。

### <a name="remarks"></a>備註

當您執行 `COlePropertyPage`的子類別時，您子類別的函式應該使用 `COlePropertyPage` 的「函數」來識別屬性頁所依據的對話方塊範本資源，以及包含其標題的字串資源。

##  <a name="getcontrolstatus"></a>COlePropertyPage：： GetControlStatus

判斷使用者是否已使用指定的資源識別碼修改屬性頁控制項的值。

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
屬性頁控制項的資源識別碼。

### <a name="return-value"></a>傳回值

如果已修改控制項值，則為 TRUE;否則為 FALSE。

##  <a name="getobjectarray"></a>COlePropertyPage：： GetObjectArray

傳回屬性頁正在編輯的物件陣列。

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>參數

*pnObjects*<br/>
不帶正負號長整數的指標，將會收到頁面正在編輯的物件數目。

### <a name="return-value"></a>傳回值

`IDispatch` 指標陣列的指標，用來存取屬性頁上每個控制項的屬性。 呼叫端不能釋放這些介面指標。

### <a name="remarks"></a>備註

每個屬性頁物件都會維護由頁面編輯之物件 `IDispatch` 介面的指標陣列。 此函式會將其*pnObjects*引數設定為該陣列中的元素數目，並將指標傳回陣列的第一個元素。

##  <a name="getpagesite"></a>COlePropertyPage：： GetPageSite

取得屬性頁之 `IPropertyPageSite` 介面的指標。

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>傳回值

屬性頁之 `IPropertyPageSite` 介面的指標。

### <a name="remarks"></a>備註

控制項和容器會共同合作，讓使用者可以流覽和編輯控制項屬性。 控制項提供屬性頁，每一個都是一個 OLE 物件，可讓使用者編輯一組相關的屬性。 容器會提供屬性框架，以顯示內容頁。 屬性框架會針對每個頁面提供支援 `IPropertyPageSite` 介面的頁面網站。

##  <a name="ignoreapply"></a>COlePropertyPage：： IgnoreApply

決定哪些控制項未啟用 [套用] 按鈕。

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
要忽略之控制項的識別碼。

### <a name="remarks"></a>備註

只有當屬性頁控制項的值已變更時，才會啟用屬性頁的 [套用] 按鈕。 使用此函式可指定不會在其值變更時啟用 [套用] 按鈕的控制項。

##  <a name="ismodified"></a>COlePropertyPage：： IsModified

判斷使用者是否已變更屬性頁上的任何值。

```
BOOL IsModified();
```

### <a name="return-value"></a>傳回值

如果已修改屬性頁，則為 TRUE。

##  <a name="oneditproperty"></a>COlePropertyPage：： OnEditProperty

當要編輯特定的屬性時，架構會呼叫這個函式。

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>參數

*dispid*<br/>
正在編輯之屬性的分派識別碼。

### <a name="return-value"></a>傳回值

預設的實值會傳回 FALSE。 此函式的覆寫應該傳回 TRUE。

### <a name="remarks"></a>備註

您可以覆寫它，將焦點設定在頁面上的適當控制項。 預設的執行不會執行任何操作，而且會傳回 FALSE。

##  <a name="onhelp"></a>COlePropertyPage：： OnHelp

當使用者要求線上說明時，架構會呼叫這個函式。

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>參數

*lpszHelpDir*<br/>
包含屬性頁說明檔的目錄。

### <a name="return-value"></a>傳回值

預設的實值會傳回 FALSE。

### <a name="remarks"></a>備註

如果您的屬性頁必須在使用者存取說明時執行任何特殊動作，請覆寫它。 預設的執行不會執行任何操作，而且會傳回 FALSE，指示架構呼叫 WinHelp。

##  <a name="oninitdialog"></a>COlePropertyPage：： OnInitDialog

當初始化屬性頁的對話方塊時，架構會呼叫這個函式。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 FALSE。

### <a name="remarks"></a>備註

如果在初始化對話方塊時需要任何特殊的動作，請覆寫它。 預設的實值 `CDialog::OnInitDialog` 會呼叫，並傳回 FALSE。

##  <a name="onobjectschanged"></a>COlePropertyPage：： OnObjectsChanged

當選擇另一個具有新屬性的 OLE 控制項時，由架構呼叫。

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>備註

在開發人員環境中查看 OLE 控制項的屬性時，會使用非強制回應對話方塊來顯示其屬性頁。 如果選取另一個控制項，則必須針對新的屬性集顯示一組不同的屬性頁。 架構會呼叫這個函式來通知屬性頁變更。

覆寫此函式以接收此動作的通知，並執行任何特殊動作。

##  <a name="onsetpagesite"></a>COlePropertyPage：： Onsetpagesite 中

當屬性框架提供屬性頁的頁面網站時，架構會呼叫這個函式。

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>備註

預設的執行會載入頁面的標題，並嘗試從對話資源判斷頁面的大小。 如果您的屬性頁需要任何進一步的動作，請覆寫此函式;您的覆寫應該呼叫基類執行。

##  <a name="setcontrolstatus"></a>COlePropertyPage：： SetControlStatus

變更屬性頁控制項的狀態。

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>參數

*nID*<br/>
包含屬性頁面控制項的識別碼。

*bDirty*<br/>
指定屬性頁的欄位是否已修改。 如果欄位已修改，則設定為 TRUE，如果尚未修改，則設為 FALSE。

### <a name="return-value"></a>傳回值

若已設定指定的控制項，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當屬性頁已關閉或選擇 [套用] 按鈕時，如果屬性頁面控制項的狀態是 [已變更]，控制項的屬性會以適當的值更新。

##  <a name="setdialogresource"></a>COlePropertyPage：： SetDialogResource

設定屬性頁的對話資源。

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>參數

*hDialog*<br/>
屬性頁之對話資源的控制碼。

##  <a name="sethelpinfo"></a>COlePropertyPage：：含有 sethelpinfo

指定屬性頁的工具提示資訊、說明文件名和說明內容。

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>參數

*lpszDocString*<br/>
字串，包含要在狀態列或其他位置顯示的簡短說明資訊。

*lpszHelpFile*<br/>
屬性頁說明檔的名稱。

*dwHelpCoNtext*<br/>
屬性頁的說明內容。

##  <a name="setmodifiedflag"></a>COlePropertyPage：： SetModifiedFlag

指出使用者是否已修改屬性頁。

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>參數

*bModified*<br/>
為屬性頁的已修改旗標指定新的值。

##  <a name="setpagename"></a>COlePropertyPage：： SetPageName

設定屬性頁的名稱，屬性框架通常會顯示在頁面的索引標籤上。

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>參數

*lpszPageName*<br/>
包含屬性頁名稱之字串的指標。

## <a name="see-also"></a>另請參閱

[MFC 範例 CIRC3](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
