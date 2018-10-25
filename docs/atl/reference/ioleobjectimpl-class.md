---
title: IOleObjectImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0595b98d26b401a93545b96a719a7c0af3440fea
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054187"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 類別

這個類別會實作`IUnknown`和是透過此容器進行通訊與控制項的主要介面。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IOleObjectImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleObjectImpl::Advise](#advise)|建立與控制項的諮詢連接。|
|[IOleObjectImpl::Close](#close)|從執行載入的控制項狀態變更。|
|[IOleObjectImpl::DoVerb](#doverb)|告知控制項執行其中一個列舉的動作。|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|告知控制項以捨棄任何正在維護的復原狀態。|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|指示要從檢視移除其使用者介面控制項。|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|執行控制項並安裝它的視窗，但不會安裝控制項的使用者介面。|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|使是在個別視窗中的 開啟編輯控制項。|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|當使用者按兩下控制項時，會執行指定的動作。 控制項定義的動作，通常是為了啟用控制項就地。|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|向使用者顯示的新插入的控制項。|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|會控制就地啟動，並顯示控制項的使用者介面，例如功能表和工具列。|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|列舉控制項的諮詢連接。|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|列舉在控制項的動作。|
|[IOleObjectImpl::GetClientSite](#getclientsite)|擷取控制項的用戶端站台。|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|從剪貼簿擷取資料。 ATL 實作會傳回 E_NOTIMPL。|
|[IOleObjectImpl::GetExtent](#getextent)|擷取控制項的顯示區域的範圍。|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|擷取控制項的狀態。|
|[IOleObjectImpl::GetMoniker](#getmoniker)|擷取控制項的 moniker。 ATL 實作會傳回 E_NOTIMPL。|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|擷取控制項的類別識別項。|
|[IOleObjectImpl::GetUserType](#getusertype)|擷取控制項的使用者型別名稱。|
|[IOleObjectImpl::InitFromData](#initfromdata)|初始化從選取的資料控制項。 ATL 實作會傳回 E_NOTIMPL。|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|檢查控制項是否為最新狀態。 ATL 實作會傳回 S_OK。|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)之後會捨棄復原狀態。|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|由呼叫[DoVerbHide](#doverbhide)隱藏控制項之後。|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動控制項之後。|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|由呼叫[DoVerbOpen](#doverbopen)控制項開啟另一個視窗中進行編輯之後。|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|由呼叫[DoVerbShow](#doverbshow)控制項進行顯示之後。|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|由呼叫[DoVerbUIActivate](#doverbuiactivate)控制項的使用者介面啟動之後。|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)復原之前捨棄的狀態。|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|由呼叫[DoVerbHide](#doverbhide)隱藏控制項之前。|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動控制項之前。|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|由呼叫[DoVerbOpen](#doverbopen)控制項已開啟以在另一個視窗中編輯之前。|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|由呼叫[DoVerbShow](#doverbshow)控制項進行可見之前。|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|由呼叫[DoVerbUIActivate](#doverbuiactivate)之前已啟用控制項的使用者介面。|
|[IOleObjectImpl::SetClientSite](#setclientsite)|告訴用戶端中的站台容器控制項。|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|如果有的話，請至控制項的應用程式，建議的色彩配置。 ATL 實作會傳回 E_NOTIMPL。|
|[IOleObjectImpl::SetExtent](#setextent)|設定控制項的顯示區域的範圍。|
|[IOleObjectImpl::SetHostNames](#sethostnames)|指示控制項容器應用程式和容器文件的名稱。|
|[IOleObjectImpl::SetMoniker](#setmoniker)|指示控制項其 moniker 的功能。 ATL 實作會傳回 E_NOTIMPL。|
|[IOleObjectImpl::Unadvise](#unadvise)|刪除與控制項的諮詢連接。|
|[IOleObjectImpl::Update](#update)|更新控制項。 ATL 實作會傳回 S_OK。|

## <a name="remarks"></a>備註

[IOleObject](/windows/desktop/api/oleidl/nn-oleidl-ioleobject)介面是透過此容器進行通訊與控制項的主要介面。 類別`IOleObjectImpl`提供此介面的預設實作，並實作`IUnknown`資訊傳送給傾印裝置在偵錯組建。

**相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>需求

**標頭：** atlctl.h

##  <a name="advise"></a>  IOleObjectImpl::Advise

建立與控制項的諮詢連接。

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>備註

請參閱[IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise) Windows SDK 中。

##  <a name="close"></a>  IOleObjectImpl::Close

從執行載入的控制項狀態變更。

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>備註

停用控制項，並終結控制項視窗，若有的話。 如果控制項類別資料成員[CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave)為 TRUE 並*dwSaveOption*參數 OLECLOSE_SAVEIFDIRTY 或 OLECLOSE_PROMPTSAVE，控制項屬性在關閉前儲存。

保留在控制項類別資料成員的指標[CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite)並[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)發行時，與資料成員[CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd)， [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)，以及[CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex)設為 FALSE。

請參閱[IOleObject::Close](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-close) Windows SDK 中。

##  <a name="doverb"></a>  IOleObjectImpl::DoVerb

告知控制項執行其中一個列舉的動作。

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

值而定`iVerb`，其中一個 ATL `DoVerb` helper 函式呼叫，如下所示：

|*iVerb*值|DoVerb helper 函式呼叫|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

請參閱[IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) Windows SDK 中。

##  <a name="doverbdiscardundo"></a>  IOleObjectImpl::DoVerbDiscardUndo

告知控制項以捨棄任何正在維護的復原狀態。

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[in]指標，該矩形容器會想要繪製到的控制項。

*hwndParent*<br/>
[in]包含控制項的視窗控制代碼。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="doverbhide"></a>  IOleObjectImpl::DoVerbHide

停用和移除控制項的使用者介面，並隱藏控制項。

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[in]指標，該矩形容器會想要繪製到的控制項。

*hwndParent*<br/>
[in]包含控制項的視窗控制代碼。 不使用 ATL 實作。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="doverbinplaceactivate"></a>  IOleObjectImpl::DoVerbInPlaceActivate

執行控制項並安裝它的視窗，但不會安裝控制項的使用者介面。

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[in]指標，該矩形容器會想要繪製到的控制項。

*hwndParent*<br/>
[in]包含控制項的視窗控制代碼。 不使用 ATL 實作。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

藉由呼叫啟動就地控制項[CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)。 除非控制項類別的資料成員`m_bWindowOnly`為 TRUE 時，`DoVerbInPlaceActivate`第一次嘗試啟動該控制項做為無視窗控制項 (只有當容器支援的可能[IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless))。 如果失敗，函式會嘗試啟動該控制項擴充功能 (可能只有當容器支援[IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex))。 如果失敗，函式會嘗試啟動該控制項沒有擴充功能 (可能只有當容器支援[IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite))。 如果啟用成功時，函式會告知容器已啟動控制項。

##  <a name="doverbopen"></a>  IOleObjectImpl::DoVerbOpen

使是在個別視窗中的 開啟編輯控制項。

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[in]指標，該矩形容器會想要繪製到的控制項。

*hwndParent*<br/>
[in]包含控制項的視窗控制代碼。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="doverbprimary"></a>  IOleObjectImpl::DoVerbPrimary

定義當使用者按兩下控制項時所採取的動作。

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[in]指標，該矩形容器會想要繪製到的控制項。

*hwndParent*<br/>
[in]包含控制項的視窗控制代碼。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

根據預設，設定要顯示的屬性頁。 您可以叫用不同的行為上按兩下，控制項類別中覆寫此例如，播放視訊，或移就地啟用作用中。

##  <a name="doverbshow"></a>  IOleObjectImpl::DoVerbShow

會告知要顯示控制項的容器。

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[in]指標，該矩形容器會想要繪製到的控制項。

*hwndParent*<br/>
[in]包含控制項的視窗控制代碼。 不使用 ATL 實作。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="doverbuiactivate"></a>  IOleObjectImpl::DoVerbUIActivate

啟動控制項的使用者介面，並通知容器，由複合功能表取代其功能表。

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
[in]指標，該矩形容器會想要繪製到的控制項。

*hwndParent*<br/>
[in]包含控制項的視窗控制代碼。 不使用 ATL 實作。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

##  <a name="enumadvise"></a>  IOleObjectImpl::EnumAdvise

提供已註冊的諮詢連接，此控制項的列舉。

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>備註

請參閱[IOleObject::EnumAdvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumadvise) Windows SDK 中。

##  <a name="enumverbs"></a>  IOleObjectImpl::EnumVerbs

提供已註冊的動作 （動詞命令），此控制項的列舉型別，藉由呼叫`OleRegEnumVerbs`。

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>備註

您可以加入您的專案.rgs 檔案的動詞命令。 例如，請參閱 CIRCCTL。在 RG [CIRC](../../visual-cpp-samples.md)範例。

請參閱[Enumverbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs) Windows SDK 中。

##  <a name="getclientsite"></a>  IOleObjectImpl::GetClientSite

將指標放在控制項類別資料成員[CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite)成*ppClientSite*和指標的參考計數遞增。

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>備註

請參閱[IOleObject::GetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclientsite) Windows SDK 中。

##  <a name="getclipboarddata"></a>  IOleObjectImpl::GetClipboardData

從剪貼簿擷取資料。

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleObject::GetClipboardData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) Windows SDK 中。

##  <a name="getextent"></a>  IOleObjectImpl::GetExtent

擷取執行控制項的顯示大小以 himetric 為單位 （每個單位 0.01 公釐）。

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>備註

大小會儲存在控制項類別資料成員[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。

請參閱[IOleObject::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getextent) Windows SDK 中。

##  <a name="getmiscstatus"></a>  IOleObjectImpl::GetMiscStatus

讓指標回到控制項的已註冊的狀態資訊，藉由呼叫`OleRegGetMiscStatus`。

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>備註

狀態資訊包括支援的控制項和呈現資料的行為。 您可以將狀態資訊新增至您的專案.rgs 檔案。

請參閱[IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) Windows SDK 中。

##  <a name="getmoniker"></a>  IOleObjectImpl::GetMoniker

擷取控制項的 moniker。

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleObject::GetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmoniker) Windows SDK 中。

##  <a name="getuserclassid"></a>  IOleObjectImpl::GetUserClassID

傳回控制項的類別識別項。

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>備註

請參閱[IOleObject::GetUserClassID](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getuserclassid) Windows SDK 中。

##  <a name="getusertype"></a>  IOleObjectImpl::GetUserType

藉由呼叫傳回控制項的使用者類型名稱`OleRegGetUserType`。

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>備註

使用者類型名稱用於在使用者介面項目，例如功能表和對話方塊中顯示。 您可以變更您的專案.rgs 檔案中的使用者型別名稱。

請參閱[IOleObject::GetUserType](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getusertype) Windows SDK 中。

##  <a name="initfromdata"></a>  IOleObjectImpl::InitFromData

初始化從選取的資料控制項。

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleObject::InitFromData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-initfromdata) Windows SDK 中。

##  <a name="isuptodate"></a>  IOleObjectImpl::IsUpToDate

檢查控制項是否為最新狀態。

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱[IOleObject::IsUpToDate](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-isuptodate) Windows SDK 中。

##  <a name="onpostverbdiscardundo"></a>  IOleObjectImpl::OnPostVerbDiscardUndo

由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)之後會捨棄復原狀態。

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

覆寫這個方法與您想要執行的程式碼之後會捨棄復原狀態。

##  <a name="onpostverbhide"></a>  IOleObjectImpl::OnPostVerbHide

由呼叫[DoVerbHide](#doverbhide)隱藏控制項之後。

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

覆寫這個方法與您想要執行的程式碼之後隱藏控制項。

##  <a name="onpostverbinplaceactivate"></a>  IOleObjectImpl::OnPostVerbInPlaceActivate

由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動控制項之後。

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

覆寫這個方法與您想要執行的程式碼就地啟動控制項之後。

##  <a name="onpostverbopen"></a>  IOleObjectImpl::OnPostVerbOpen

由呼叫[DoVerbOpen](#doverbopen)控制項開啟另一個視窗中進行編輯之後。

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

覆寫此方法，以您想要控制開啟另一個視窗中進行編輯之後執行的程式碼。

##  <a name="onpostverbshow"></a>  IOleObjectImpl::OnPostVerbShow

由呼叫[DoVerbShow](#doverbshow)控制項進行顯示之後。

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

覆寫此方法，以您想要執行控制項進行顯示之後的程式碼。

##  <a name="onpostverbuiactivate"></a>  IOleObjectImpl::OnPostVerbUIActivate

由呼叫[DoVerbUIActivate](#doverbuiactivate)控制項的使用者介面啟動之後。

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

覆寫此方法，以您想要執行後已啟動控制項的使用者介面的程式碼。

##  <a name="onpreverbdiscardundo"></a>  IOleObjectImpl::OnPreVerbDiscardUndo

由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)復原之前捨棄的狀態。

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要避免被捨棄復原狀態，會覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbhide"></a>  IOleObjectImpl::OnPreVerbHide

由呼叫[DoVerbHide](#doverbhide)隱藏控制項之前。

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止在隱藏控制項，會覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbinplaceactivate"></a>  IOleObjectImpl::OnPreVerbInPlaceActivate

由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動控制項之前。

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止控制項被就地啟用，會覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbopen"></a>  IOleObjectImpl::OnPreVerbOpen

由呼叫[DoVerbOpen](#doverbopen)控制項已開啟以在另一個視窗中編輯之前。

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止控制項正在開啟另一個視窗中進行編輯，覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbshow"></a>  IOleObjectImpl::OnPreVerbShow

由呼叫[DoVerbShow](#doverbshow)控制項進行可見之前。

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止控制項成為可見，覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbuiactivate"></a>  IOleObjectImpl::OnPreVerbUIActivate

由呼叫[DoVerbUIActivate](#doverbuiactivate)之前已啟用控制項的使用者介面。

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止控制項的使用者介面啟動，會覆寫此方法以傳回錯誤 HRESULT。

##  <a name="setclientsite"></a>  IOleObjectImpl::SetClientSite

告訴用戶端中的站台容器控制項。

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>備註

接著方法會傳回 S_OK。

請參閱[IOleObject::SetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setclientsite) Windows SDK 中。

##  <a name="setcolorscheme"></a>  IOleObjectImpl::SetColorScheme

如果有的話，請至控制項的應用程式，建議的色彩配置。

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) Windows SDK 中。

##  <a name="setextent"></a>  IOleObjectImpl::SetExtent

設定控制項的顯示區域的範圍。

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>備註

否則，請`SetExtent`儲存所指向的值`psizel`控制項的類別資料成員中[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。 這個值是以 himetric 為單位 （每個單位 0.01 公釐）。

如果控制項類別資料成員[CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural)為 TRUE 時，`SetExtent`也會儲存所指向的值`psizel`控制項的類別資料成員中[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

如果控制項類別資料成員[CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize)為 TRUE 時，`SetExtent`呼叫`SendOnDataChange`和`SendOnViewChange`通知註冊控制項大小的 advise 持有者的所有通知接收變更。

請參閱[IOleObject::SetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setextent) Windows SDK 中。

##  <a name="sethostnames"></a>  IOleObjectImpl::SetHostNames

指示控制項容器應用程式和容器文件的名稱。

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱[IOleObject::SetHostNames](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-sethostnames) Windows SDK 中。

##  <a name="setmoniker"></a>  IOleObjectImpl::SetMoniker

指示控制項其 moniker 的功能。

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱[IOleObject::SetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setmoniker) Windows SDK 中。

##  <a name="unadvise"></a>  IOleObjectImpl::Unadvise

刪除儲存在控制項類別的諮詢連接`m_spOleAdviseHolder`資料成員。

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>備註

請參閱[IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise) Windows SDK 中。

##  <a name="update"></a>  IOleObjectImpl::Update

更新控制項。

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱[IOleObject::Update](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-update) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制項介面](/windows/desktop/com/activex-controls-interfaces)<br/>
[類別概觀](../../atl/atl-class-overview.md)
