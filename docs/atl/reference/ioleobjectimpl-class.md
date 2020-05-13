---
title: IOleObjectimpl 類別
ms.date: 11/04/2016
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
ms.openlocfilehash: 86d82aea2e92eb99903284abe4ac03478369616c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326530"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectimpl 類別

此類實現`IUnknown`並且是容器與控件通信的主體介面。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IOleObjectImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleObjectimpl::建議](#advise)|與控制項建立諮詢連接。|
|[IOleObjectimpl:關閉](#close)|將控制狀態從運行更改為載入。|
|[IOleObjectimpl::DoVerb](#doverb)|告訴控件執行其枚舉操作之一。|
|[IOleObjectimpl::DoVerb丟棄Undo](#doverbdiscardundo)|告訴控件放棄它維護的任何撤銷狀態。|
|[IOleObjectimpl::DoVerbHide](#doverbhide)|告訴控制項從檢視中刪除其使用者介面。|
|[IOleobjectimpl::Doverbinplace啟動](#doverbinplaceactivate)|運行控制項並安裝其視窗,但不會安裝控制項的使用者介面。|
|[IOleObjectimpl::DoVerbOpen](#doverbopen)|導致在單獨的視窗中打開編輯控制項。|
|[IOleObjectimpl::DoVerb主要](#doverbprimary)|當用戶雙擊控件時執行指定的操作。 控件定義操作,通常是為了就地啟動控件。|
|[IOleObjectimpl::DoVerbshow](#doverbshow)|向用戶顯示新插入的控制項。|
|[IOleObjectimpl::DoVerbUI啟動](#doverbuiactivate)|就地啟動控制件並顯示控制項的使用者介面,如功能表和工具列。|
|[IOleObjectimpl::枚舉建議](#enumadvise)|枚舉控件的諮詢連接。|
|[IOleObjectimpl::枚舉](#enumverbs)|枚舉控件的操作。|
|[IOleObjectimpl::取得客戶端網站](#getclientsite)|檢索控件的用戶端網站。|
|[IOleObjectimpl::取得夾板資料](#getclipboarddata)|從剪貼板檢索數據。 ATL 實現返回E_NOTIMPL。|
|[IOleObjectimpl::取得範圍](#getextent)|檢索控件顯示區域的範圍。|
|[IOleObjectimpl::取得Misc狀態](#getmiscstatus)|檢索控件的狀態。|
|[IOleObjectimpl::GetMoniker](#getmoniker)|檢索控件的綽號。 ATL 實現返回E_NOTIMPL。|
|[IOleObjectimpl::獲取使用者類ID](#getuserclassid)|檢索控件的類標識符。|
|[IOleObjectimpl::取得使用者類型](#getusertype)|檢索控制件的用戶類型名稱。|
|[IOleObjectimpl::從資料中](#initfromdata)|從所選數據初始化控制項。 ATL 實現返回E_NOTIMPL。|
|[IOleobjectimpl::至前](#isuptodate)|檢查控件是否為最新控制項。 ATL 實現返回S_OK。|
|[IOleObjectimpl::在後空音丟棄undo](#onpostverbdiscardundo)|在丟棄撤消狀態後由[DoVerbDiscardUndo](#doverbdiscardundo)調用。|
|[IOleobjectimpl::在後音隱藏](#onpostverbhide)|在控制項隱藏後由[DoVerbHide](#doverbhide)調用。|
|[IOleobjectimpl::在後空音位置啟動](#onpostverbinplaceactivate)|在控制器啟動到位後,[由 DoVerbInPlace 呼叫](#doverbinplaceactivate)。|
|[IOleObjectimpl::在PostVerbopen上](#onpostverbopen)|在打開控制項以在單獨的視窗中編輯控制項後[,DoVerbOpen](#doverbopen)呼叫。|
|[IOleObjectimpl::在後場Verbshow](#onpostverbshow)|在控制項變得可見後由[DoVerbShow](#doverbshow)調用。|
|[IOleObjectimpl::在後空音啟動](#onpostverbuiactivate)|在啟動控制項的使用者介面後,[由 DoVerbUIActivate](#doverbuiactivate)調用。|
|[IOleObjectimpl::在Preverbimplundo](#onpreverbdiscardundo)|在丟棄撤消狀態之前由[DoVerbDiscardUndo](#doverbdiscardundo)調用。|
|[IOleobjectimpl::在上Verbverbhide](#onpreverbhide)|在隱藏控制項之前由[DoVerbHide](#doverbhide)調用。|
|[IOleobjectimpl::在預置位置啟動](#onpreverbinplaceactivate)|在控制器啟動到位之前,[由 DoVerbInPlace 呼叫](#doverbinplaceactivate)。|
|[IOleObjectimpl::在Preverbopen上](#onpreverbopen)|在打開控制項以在單獨的視窗中編輯之前由[DoVerbOpen](#doverbopen)調用。|
|[IOleObjectimpl::在Preverbshow上](#onpreverbshow)|在控制項變得可見之前由[DoVerbShow](#doverbshow)調用。|
|[IOleObjectimpl::在Verbui啟動上](#onpreverbuiactivate)|在啟動控制項的使用者介面之前,[由 DoVerbUIActivate](#doverbuiactivate)調用。|
|[IOleObjectimpl::設定客戶端網站](#setclientsite)|告訴控件有關其在容器中的用戶端網站。|
|[IOleObjectimpl::設定顏色方案](#setcolorscheme)|向控制項應用程式(如果有)建議顏色配置。 ATL 實現返回E_NOTIMPL。|
|[IOleObjectimpl::設定範圍](#setextent)|設置控制項的顯示區域的範圍。|
|[IOleObjectimpl::設定主機名](#sethostnames)|告訴控制項應用程式和容器文件的名稱。|
|[IOleObjectimpl::SetMoniker](#setmoniker)|告訴控件其名字是什麼。 ATL 實現返回E_NOTIMPL。|
|[IOleObjectimpl::不建議](#unadvise)|刪除與控制項的諮詢連接。|
|[IOleObjectimpl::更新](#update)|更新控件。 ATL 實現返回S_OK。|

## <a name="remarks"></a>備註

[IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject)介面是容器與控制項通訊的主要介面。 類`IOleObjectImpl`通過在調試生成中向轉儲設備`IUnknown`發送 資訊來提供此介面的默認實現和實現。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="ioleobjectimpladvise"></a><a name="advise"></a>IOleObjectimpl::建議

與控制項建立諮詢連接。

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>備註

請參閱[IOleObject::](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise)在 Windows SDK 中提供建議。

## <a name="ioleobjectimplclose"></a><a name="close"></a>IOleObjectimpl:關閉

將控制狀態從運行更改為載入。

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>備註

停用控制項並銷毀控制視窗(如果存在)。 如果控制類資料成員[CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave)為 TRUE,*並且 dwSaveOption*參數是OLECLOSE_SAVEIFDIRTY或OLECLOSE_PROMPTSAVE,則控件屬性在關閉前保存。

控制類數據成員[CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite)和[CComControlBase:m_spAdviseSink)](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)中持有的指標被釋放,數據成員[CComControlBase:::m_bNegotiatedWnd、CComControlBase:m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd)和[CComControlBase:m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex)設置為 FALSE。 [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)

請參閱[IOleObject:關閉](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close)Windows SDK。

## <a name="ioleobjectimpldoverb"></a><a name="doverb"></a>IOleObjectimpl::DoVerb

告訴控件執行其枚舉操作之一。

```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```

### <a name="remarks"></a>備註

根據的值`iVerb`,其中一個`DoVerb`ATL 説明器函數的調用如下所示:

|*iVerb*價值|多維爾布說明器函數稱為|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[多維爾布·丟棄Undo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[多維爾布](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[多維爾布林廣場啟動](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[多維爾布開啟](#doverbopen)|
|OLEIVERB_PRIMARY|[多維爾布小學](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerb屬性](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[多維爾布秀](#doverbshow)|
|OLEIVERB_UIACTIVATE|[多維爾布UI啟動](#doverbuiactivate)|

請參閱[IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)在 Windows SDK 中。

## <a name="ioleobjectimpldoverbdiscardundo"></a><a name="doverbdiscardundo"></a>IOleObjectimpl::DoVerb丟棄Undo

告訴控件放棄它維護的任何撤銷狀態。

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[在]指向容器希望控件繪製到的矩形的指標。

*hwnd 家長*<br/>
[在]包含控制項的視窗的句柄。

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="ioleobjectimpldoverbhide"></a><a name="doverbhide"></a>IOleObjectimpl::DoVerbHide

停用並刪除控制項的使用者介面,並隱藏控制項。

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[在]指向容器希望控件繪製到的矩形的指標。

*hwnd 家長*<br/>
[在]包含控制項的視窗的句柄。 ATL 實現中未使用。

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="ioleobjectimpldoverbinplaceactivate"></a><a name="doverbinplaceactivate"></a>IOleobjectimpl::Doverbinplace啟動

運行控制項並安裝其視窗,但不會安裝控制項的使用者介面。

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[在]指向容器希望控件繪製到的矩形的指標。

*hwnd 家長*<br/>
[在]包含控制項的視窗的句柄。 ATL 實現中未使用。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

通過調用[CComControlBase::在原位置啟動啟動](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)控制項。 除非控制項名稱的資料`m_bWindowOnly`成員為`DoVerbInPlaceActivate`TRUE, 否則首先嘗試將控制項啟用為無視窗控制項(僅當容器支援[IOleInPlaceSite 無視窗](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)時才可能)。 如果失敗,該函數將嘗試使用擴展功能啟動控件(僅當容器支援[IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)時才可能)。 如果失敗,該函數將嘗試啟動沒有擴展功能的控制項(僅當容器支援[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)時才可能)。 如果啟動成功,該函數將通知容器控件已啟動。

## <a name="ioleobjectimpldoverbopen"></a><a name="doverbopen"></a>IOleObjectimpl::DoVerbOpen

導致在單獨的視窗中打開編輯控制項。

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[在]指向容器希望控件繪製到的矩形的指標。

*hwnd 家長*<br/>
[在]包含控制項的視窗的句柄。

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="ioleobjectimpldoverbprimary"></a><a name="doverbprimary"></a>IOleObjectimpl::DoVerb主要

定義用戶雙擊控件時執行的操作。

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[在]指向容器希望控件繪製到的矩形的指標。

*hwnd 家長*<br/>
[在]包含控制項的視窗的句柄。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

### <a name="remarks"></a>備註

預設情況下,設置為顯示屬性頁。 您可以在控件類中重寫此行為,以在按兩下時調用其他行為;但是,在雙擊時,可以重寫此行為。例如,播放視頻或就地活動。

## <a name="ioleobjectimpldoverbshow"></a><a name="doverbshow"></a>IOleObjectimpl::DoVerbshow

告訴容器使控制項可見。

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[在]指向容器希望控件繪製到的矩形的指標。

*hwnd 家長*<br/>
[在]包含控制項的視窗的句柄。 ATL 實現中未使用。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ioleobjectimpldoverbuiactivate"></a><a name="doverbuiactivate"></a>IOleObjectimpl::DoVerbUI啟動

啟動控制項的使用者介面,並通知容器其功能表正在被複合功能表替換。

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[在]指向容器希望控件繪製到的矩形的指標。

*hwnd 家長*<br/>
[在]包含控制項的視窗的句柄。 ATL 實現中未使用。

### <a name="return-value"></a>傳回值

標準 HRESULT 值之一。

## <a name="ioleobjectimplenumadvise"></a><a name="enumadvise"></a>IOleObjectimpl::枚舉建議

提供此控制件的已註冊諮詢連接的枚舉。

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>備註

請參閱[IOleObject::Windows](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) SDK 中的 Enum 建議。

## <a name="ioleobjectimplenumverbs"></a><a name="enumverbs"></a>IOleObjectimpl::枚舉

通過調用`OleRegEnumVerbs`提供此控制件的已註冊操作(動詞)的枚舉。

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>備註

您可以將謂詞添加到專案的 .rgs 檔中。 例如,請參閱 CIRCCTL。[保監會](../../overview/visual-cpp-samples.md)樣本中的RGS。

請參閱[IOleObject::Windows](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) SDK 中的枚舉Verbs。

## <a name="ioleobjectimplgetclientsite"></a><a name="getclientsite"></a>IOleObjectimpl::取得客戶端網站

將指標放入控制類數據成員[CComControlBase:::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite)到*ppClientSite*中,並在指標上增加引用計數。

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>備註

請參閱[IOleObject:獲取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite)Windows SDK 中的用戶端網站。

## <a name="ioleobjectimplgetclipboarddata"></a><a name="getclipboarddata"></a>IOleObjectimpl::取得夾板資料

從剪貼板檢索數據。

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 IOleObject:獲取 Windows SDK 中的[「剪貼簿數據](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata)」 。

## <a name="ioleobjectimplgetextent"></a><a name="getextent"></a>IOleObjectimpl::取得範圍

以 HIMETRIC 單位(每單位 0.01 毫米)檢索正在運行的控制項的顯示大小。

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>備註

大小儲存在控制類別資料成員[CComControlBase:m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。

請參閱[IOleObject:獲取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent)Windows SDK 中的範圍。

## <a name="ioleobjectimplgetmiscstatus"></a><a name="getmiscstatus"></a>IOleObjectimpl::取得Misc狀態

通過調用`OleRegGetMiscStatus`返回指向控制項的已註冊狀態資訊的指標。

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>備註

狀態資訊包括控件和表示數據支持的行為。 您可以將狀態資訊添加到專案的 .rgs 檔中。

請參閱[IOleObject:獲取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)Windows SDK 中的 Misc 身份。

## <a name="ioleobjectimplgetmoniker"></a><a name="getmoniker"></a>IOleObjectimpl::GetMoniker

檢索控件的綽號。

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleObject:在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker)Windows SDK 中獲取 Moniker。

## <a name="ioleobjectimplgetuserclassid"></a><a name="getuserclassid"></a>IOleObjectimpl::獲取使用者類ID

返回控制項的類標識。

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>備註

請參閱[IOleObject:獲取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid)Windows SDK 中的UserClassID。

## <a name="ioleobjectimplgetusertype"></a><a name="getusertype"></a>IOleObjectimpl::取得使用者類型

通過調用`OleRegGetUserType`返回控制項的用戶類型名稱。

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>備註

使用者名用於在用戶介面元素(如功能表和對話框)中顯示。 您可以在專案的 .rgs 檔中更改使用者名類型名稱。

請參閱[IOleObject:獲取](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype)Windows SDK 中的用戶類型。

## <a name="ioleobjectimplinitfromdata"></a><a name="initfromdata"></a>IOleObjectimpl::從資料中

從所選數據初始化控制項。

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleObject:Windows SDK 中來自資料的 Initit。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata)

## <a name="ioleobjectimplisuptodate"></a><a name="isuptodate"></a>IOleobjectimpl::至前

檢查控件是否為最新控制項。

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IOleObject:Windows SDK 中的「IsUpDate」。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate)

## <a name="ioleobjectimplonpostverbdiscardundo"></a><a name="onpostverbdiscardundo"></a>IOleObjectimpl::在後空音丟棄undo

在丟棄撤消狀態後由[DoVerbDiscardUndo](#doverbdiscardundo)調用。

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

使用要在丟棄撤銷狀態後執行的代碼重寫此方法。

## <a name="ioleobjectimplonpostverbhide"></a><a name="onpostverbhide"></a>IOleobjectimpl::在後音隱藏

在控制項隱藏後由[DoVerbHide](#doverbhide)調用。

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

使用隱藏控制項後要執行的代碼覆蓋此方法。

## <a name="ioleobjectimplonpostverbinplaceactivate"></a><a name="onpostverbinplaceactivate"></a>IOleobjectimpl::在後空音位置啟動

在控制器啟動到位後,[由 DoVerbInPlace 呼叫](#doverbinplaceactivate)。

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

使用要在控制項就地啟動後執行的代碼覆蓋此方法。

## <a name="ioleobjectimplonpostverbopen"></a><a name="onpostverbopen"></a>IOleObjectimpl::在PostVerbopen上

在打開控制項以在單獨的視窗中編輯控制項後[,DoVerbOpen](#doverbopen)呼叫。

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

在打開控制項以在單獨的視窗中編輯後,使用要執行的代碼覆蓋此方法。

## <a name="ioleobjectimplonpostverbshow"></a><a name="onpostverbshow"></a>IOleObjectimpl::在後場Verbshow

在控制項變得可見後由[DoVerbShow](#doverbshow)調用。

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

使用要在控制項變得可見後執行的代碼重寫此方法。

## <a name="ioleobjectimplonpostverbuiactivate"></a><a name="onpostverbuiactivate"></a>IOleObjectimpl::在後空音啟動

在啟動控制項的使用者介面後,[由 DoVerbUIActivate](#doverbuiactivate)調用。

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

使用要在啟動控制項的使用者介面後執行的代碼覆蓋此方法。

## <a name="ioleobjectimplonpreverbdiscardundo"></a><a name="onpreverbdiscardundo"></a>IOleObjectimpl::在Preverbimplundo

在丟棄撤消狀態之前由[DoVerbDiscardUndo](#doverbdiscardundo)調用。

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

為了防止丟棄撤銷狀態,請重寫此方法以返回錯誤 HRESULT。

## <a name="ioleobjectimplonpreverbhide"></a><a name="onpreverbhide"></a>IOleobjectimpl::在上Verbverbhide

在隱藏控制項之前由[DoVerbHide](#doverbhide)調用。

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

為了防止隱藏控制項,重寫此方法以返回錯誤 HRESULT。

## <a name="ioleobjectimplonpreverbinplaceactivate"></a><a name="onpreverbinplaceactivate"></a>IOleobjectimpl::在預置位置啟動

在控制器啟動到位之前,[由 DoVerbInPlace 呼叫](#doverbinplaceactivate)。

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

為了防止在就位啟動控件,重寫此方法以返回錯誤 HRESULT。

## <a name="ioleobjectimplonpreverbopen"></a><a name="onpreverbopen"></a>IOleObjectimpl::在Preverbopen上

在打開控制項以在單獨的視窗中編輯之前由[DoVerbOpen](#doverbopen)調用。

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

為了防止在單獨的視窗中打開控制項進行編輯,重寫此方法以返回錯誤 HRESULT。

## <a name="ioleobjectimplonpreverbshow"></a><a name="onpreverbshow"></a>IOleObjectimpl::在Preverbshow上

在控制項變得可見之前由[DoVerbShow](#doverbshow)調用。

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

為了防止控制項變得可見,重寫此方法以返回錯誤 HRESULT。

## <a name="ioleobjectimplonpreverbuiactivate"></a><a name="onpreverbuiactivate"></a>IOleObjectimpl::在Verbui啟動上

在啟動控制項的使用者介面之前,[由 DoVerbUIActivate](#doverbuiactivate)調用。

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

為了防止啟動控制件的使用者介面,重寫此方法以返回錯誤 HRESULT。

## <a name="ioleobjectimplsetclientsite"></a><a name="setclientsite"></a>IOleObjectimpl::設定客戶端網站

告訴控件有關其在容器中的用戶端網站。

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>備註

然後,該方法返回S_OK。

請參閱[IOleObject:在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite)Windows SDK 中設置用戶端網站。

## <a name="ioleobjectimplsetcolorscheme"></a><a name="setcolorscheme"></a>IOleObjectimpl::設定顏色方案

向控制項應用程式(如果有)建議顏色配置。

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleObject:在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)Windows SDK 中設置顏色方案。

## <a name="ioleobjectimplsetextent"></a><a name="setextent"></a>IOleObjectimpl::設定範圍

設置控制項的顯示區域的範圍。

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>備註

否則,`SetExtent`將控制類數據`psizel`成員[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)中指向的值存儲。 此值以 HIMETRIC 單位(單位 0.01 毫米)為單位。

如果控制類數據成員[CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural)為`SetExtent`TRUE,則還會`psizel`將控制類 數據成員[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)中指向的值存儲。

如果控制類數據成員[CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize)為`SetExtent`TRUE,`SendOnDataChange`請`SendOnViewChange`呼叫 並 通知向通知持有人註冊的所有通知接收器控制大小已更改。

請參閱[IOleObject:在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent)Windows SDK 中設置範圍。

## <a name="ioleobjectimplsethostnames"></a><a name="sethostnames"></a>IOleObjectimpl::設定主機名

告訴控制項應用程式和容器文件的名稱。

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IOleObject:在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames)Windows SDK 中設置主機名。

## <a name="ioleobjectimplsetmoniker"></a><a name="setmoniker"></a>IOleObjectimpl::SetMoniker

告訴控件其名字是什麼。

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleObject:在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker)Windows SDK 中設置 Moniker。

## <a name="ioleobjectimplunadvise"></a><a name="unadvise"></a>IOleObjectimpl::不建議

刪除存儲在控制類`m_spOleAdviseHolder`的數據成員中的諮詢連接。

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>備註

請參閱[IOleObject::](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise)在 Windows SDK 中取消建議。

## <a name="ioleobjectimplupdate"></a><a name="update"></a>IOleObjectimpl::更新

更新控件。

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

請參閱[IOleObject::](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update)在 Windows SDK 中更新。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制介面](/windows/win32/com/activex-controls-interfaces)<br/>
[類別概觀](../../atl/atl-class-overview.md)
