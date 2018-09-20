---
title: COlePropertyPage 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7db08ae9b9c2899709f4c6511478714869475ae7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386427"
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
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|建構 `COlePropertyPage` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|指出使用者是否已修改控制項中的值。|
|[COlePropertyPage::GetObjectArray](#getobjectarray)|傳回正在編輯的屬性頁的物件陣列。|
|[COlePropertyPage::GetPageSite](#getpagesite)|讓指標回到屬性頁的`IPropertyPageSite`介面。|
|[COlePropertyPage::IgnoreApply](#ignoreapply)|決定哪些控制項不會啟用 [套用] 按鈕。|
|[COlePropertyPage::IsModified](#ismodified)|指出使用者是否已修改的屬性頁。|
|[COlePropertyPage::OnEditProperty](#oneditproperty)|當使用者編輯屬性時，由架構呼叫。|
|[COlePropertyPage::OnHelp](#onhelp)|當使用者叫用說明時，由架構呼叫。|
|[COlePropertyPage::OnInitDialog](#oninitdialog)|初始化的屬性頁時由架構呼叫。|
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|選擇另一個 OLE 控制項，使用新的屬性時，由架構呼叫。|
|[Colepropertypage:: Onsetpagesite](#onsetpagesite)|當屬性框架提供網頁的網站時由架構呼叫。|
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|設定旗標，指出使用者是否已修改控制項中的值。|
|[COlePropertyPage::SetDialogResource](#setdialogresource)|設定屬性頁的對話方塊資源。|
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|設定屬性頁的簡短說明文字，其說明檔和其說明內容的名稱。|
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|設定旗標，指出使用者是否已修改的屬性頁。|
|[COlePropertyPage::SetPageName](#setpagename)|設定屬性頁的名稱 （標題）。|

## <a name="remarks"></a>備註

比方說，屬性頁可能包含編輯控制項，可讓使用者檢視和修改控制項的 [標題] 屬性。

每個自訂或內建的控制項屬性可以有對話方塊的控制項，可讓控制項的使用者檢視目前的屬性值，並視需要修改該值。

如需有關使用`COlePropertyPage`，請參閱文章[ActiveX 控制項： 屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>需求

**標頭：** afxctl.h

##  <a name="colepropertypage"></a>  COlePropertyPage::COlePropertyPage

建構 `COlePropertyPage` 物件。

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>參數

*idDlg*<br/>
對話方塊範本資源識別碼。

*idCaption*<br/>
資源識別碼的屬性頁的標題。

### <a name="remarks"></a>備註

當您實作的子類別`COlePropertyPage`，您的子類別建構函式應該使用`COlePropertyPage`建構函式識別的對話方塊範本資源上所依據的屬性頁和包含它的標題的字串資源。

##  <a name="getcontrolstatus"></a>  COlePropertyPage::GetControlStatus

判斷使用者是否已修改的值的屬性頁控制項，並提供指定的資源識別碼。

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
屬性頁控制項的資源識別碼。

### <a name="return-value"></a>傳回值

如果已修改控制項的值;，則為 TRUE。否則為 FALSE。

##  <a name="getobjectarray"></a>  COlePropertyPage::GetObjectArray

傳回正在編輯的屬性頁的物件陣列。

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>參數

*pnObjects*<br/>
將會收到頁面正在編輯的物件數目的不帶正負號長整數指標。

### <a name="return-value"></a>傳回值

陣列的指標`IDispatch`指標，用來存取屬性頁上的每個控制項的屬性。 呼叫端必須釋放這些介面指標。

### <a name="remarks"></a>備註

每個屬性頁物件會維護的指標陣列`IDispatch`頁面正在編輯之物件的介面。 此函式會將其*pnObjects*該陣列中的項目數的引數和傳回陣列的第一個元素的指標。

##  <a name="getpagesite"></a>  COlePropertyPage::GetPageSite

取得屬性頁的指標`IPropertyPageSite`介面。

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>傳回值

屬性頁的指標`IPropertyPageSite`介面。

### <a name="remarks"></a>備註

控制項和容器共同合作，讓使用者可以瀏覽並編輯控制項屬性。 控制項提供屬性頁中，每個都是 OLE 物件，可讓使用者編輯一組相關的屬性。 容器會提供顯示屬性頁的屬性畫面格。 針對每個頁面中，屬性框架提供網頁站台，可支援`IPropertyPageSite`介面。

##  <a name="ignoreapply"></a>  COlePropertyPage::IgnoreApply

決定哪些控制項不會啟用 [套用] 按鈕。

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
要忽略的控制項 ID。

### <a name="remarks"></a>備註

只有在已變更的屬性頁面控制項的值時，才啟用屬性頁的 [套用] 按鈕。 您可以使用此函式來指定不會使其值變更時，啟用 [套用] 按鈕的控制項。

##  <a name="ismodified"></a>  COlePropertyPage::IsModified

判斷使用者是否已變更屬性頁上的任何值。

```
BOOL IsModified();
```

### <a name="return-value"></a>傳回值

如果已修改的屬性頁，則為 TRUE。

##  <a name="oneditproperty"></a>  COlePropertyPage::OnEditProperty

若要編輯的特定屬性時，架構會呼叫此函式。

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>參數

*dispid*<br/>
正在編輯之屬性的分派識別碼。

### <a name="return-value"></a>傳回值

預設實作會傳回 FALSE。 此函式的覆寫應該會傳回 TRUE。

### <a name="remarks"></a>備註

您可以覆寫它將焦點設定為適當的控制項，在頁面上。 預設實作不做任何動作，且會傳回 FALSE。

##  <a name="onhelp"></a>  COlePropertyPage::OnHelp

當使用者要求線上說明時，架構會呼叫此函式。

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>參數

*lpszHelpDir*<br/>
包含屬性頁的說明檔的目錄。

### <a name="return-value"></a>傳回值

預設實作會傳回 FALSE。

### <a name="remarks"></a>備註

覆寫它，如果您的屬性頁面必須執行任何特殊動作，當使用者存取說明。 預設實作不做任何動作，並傳回 FALSE，指示 framework 呼叫 WinHelp。

##  <a name="oninitdialog"></a>  COlePropertyPage::OnInitDialog

初始化屬性頁的對話方塊時，架構會呼叫此函式。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

預設實作會傳回 FALSE。

### <a name="remarks"></a>備註

如果初始化對話方塊時，不需要任何特殊的動作，則請它覆寫。 預設實作會呼叫`CDialog::OnInitDialog`且會傳回 FALSE。

##  <a name="onobjectschanged"></a>  COlePropertyPage::OnObjectsChanged

選擇另一個 OLE 控制項，使用新的屬性時，由架構呼叫。

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>備註

當開發人員環境中檢視 OLE 控制項的屬性，非強制回應對話方塊用來顯示其屬性頁。 如果選取另一個控制項，則必須顯示一組不同的屬性頁的一組新的屬性。 架構會呼叫此函式可通知此變更的屬性頁面。

覆寫這個函式來接收通知，此動作，並執行任何特殊動作。

##  <a name="onsetpagesite"></a>  Colepropertypage:: Onsetpagesite

當屬性框架提供屬性頁的頁面網站時，架構會呼叫此函式。

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>備註

預設實作會載入網頁的標題，並會嘗試判斷從對話方塊資源的頁面大小。 覆寫這個函式，如果您的屬性頁面需要任何進一步的動作;覆寫應該呼叫基底類別實作。

##  <a name="setcontrolstatus"></a>  COlePropertyPage::SetControlStatus

變更屬性頁面上控制項的狀態。

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>參數

*nID*<br/>
包含的屬性頁面上控制項的識別碼。

*bDirty*<br/>
指定是否已修改的屬性頁面 欄位。 如果欄位已修改，FALSE 如果未修改，請設定為 TRUE。

### <a name="return-value"></a>傳回值

為 TRUE，如果已設定為指定的控制項;否則為 FALSE。

### <a name="remarks"></a>備註

如果屬性頁面上控制項的狀態已經變更，關閉 [屬性] 頁面，或選擇 [套用] 按鈕時，將會使用適當的值更新控制項的屬性。

##  <a name="setdialogresource"></a>  COlePropertyPage::SetDialogResource

設定屬性頁的對話方塊資源。

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>參數

*hDialog*<br/>
屬性頁的對話方塊資源的控制代碼。

##  <a name="sethelpinfo"></a>  COlePropertyPage::SetHelpInfo

指定工具提示資訊、 說明檔案名稱和屬性頁的說明內容。

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>參數

*lpszDocString*<br/>
字串，包含顯示在狀態列上或其他位置的簡短說明資訊。

*lpszHelpFile*<br/>
屬性頁的說明檔的名稱。

*dwHelpContext*<br/>
[屬性] 頁面的說明內容。

##  <a name="setmodifiedflag"></a>  COlePropertyPage::SetModifiedFlag

指出使用者是否已修改的屬性頁。

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>參數

*bModified*<br/>
指定屬性頁的修改的旗標的新值。

##  <a name="setpagename"></a>  COlePropertyPage::SetPageName

設定屬性框架通常會顯示在頁面的索引標籤的屬性頁的名稱。

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>參數

*lpszPageName*<br/>
包含屬性頁的名稱的字串指標。

## <a name="see-also"></a>另請參閱

[MFC 範例 CIRC3](../../visual-cpp-samples.md)<br/>
[MFC 範例 TESTHELP](../../visual-cpp-samples.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
