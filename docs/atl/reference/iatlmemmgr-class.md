---
title: IAtlMemMgr 類別
ms.date: 11/04/2016
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
ms.openlocfilehash: a0d79ae95a0604ca75f03673873e99394a1bc295
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496073"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr 類別

此類別代表記憶體管理員的介面。

## <a name="syntax"></a>語法

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[定位](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[受](#free)|呼叫這個方法以釋放記憶體區塊。|
|[GetSize](#getsize)|呼叫這個方法, 以取出已配置記憶體區塊的大小。|
|[重新配置](#reallocate)|呼叫這個方法來重新配置記憶體區塊。|

## <a name="remarks"></a>備註

這個介面是由[CComHeap](../../atl/reference/ccomheap-class.md)、 [CCRTHeap](../../atl/reference/ccrtheap-class.md)、 [CLocalHeap](../../atl/reference/clocalheap-class.md)、 [CGlobalHeap](../../atl/reference/cglobalheap-class.md)或[CWin32Heap](../../atl/reference/cwin32heap-class.md)所執行。

> [!NOTE]
>  本機和全域堆積函數的速度比其他記憶體管理函式慢, 而且不提供許多功能。 因此, 新的應用程式應該使用[堆積函數](/windows/win32/Memory/heap-functions)。 這些是在[CWin32Heap](../../atl/reference/cwin32heap-class.md)類別中提供。

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>需求

**標頭:** atlmem。h

##  <a name="allocate"></a>  IAtlMemMgr::Allocate

呼叫這個方法來配置記憶體區塊。

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*nBytes*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫[IAtlMemMgr:: Free](#free)或[IAtlMemMgr::](#reallocate)重新配置以釋放這個方法所配置的記憶體。

### <a name="example"></a>範例

如需範例, 請參閱[IAtlMemMgr 總覽](../../atl/reference/iatlmemmgr-class.md)。

##  <a name="free"></a>IAtlMemMgr:: Free

呼叫這個方法以釋放記憶體區塊。

```
void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。

### <a name="remarks"></a>備註

使用此方法來釋放[IAtlMemMgr:: Allocate](#allocate)或[IAtlMemMgr::](#reallocate)重新配置所取得的記憶體。

### <a name="example"></a>範例

如需範例, 請參閱[IAtlMemMgr 總覽](../../atl/reference/iatlmemmgr-class.md)。

##  <a name="getsize"></a>IAtlMemMgr:: GetSize

呼叫這個方法, 以取出已配置記憶體區塊的大小。

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。

### <a name="return-value"></a>傳回值

傳回記憶體區塊的大小 (以位元組為單位)。

### <a name="example"></a>範例

如需範例, 請參閱[IAtlMemMgr 總覽](../../atl/reference/iatlmemmgr-class.md)。

##  <a name="reallocate"></a>  IAtlMemMgr::Reallocate

呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。

*nBytes*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫[IAtlMemMgr:: Free](#free)或[IAtlMemMgr::](#reallocate)重新配置以釋放這個方法所配置的記憶體。

在概念上, 這個方法會釋出現有的記憶體, 並配置新的記憶體區塊。 事實上, 現有的記憶體可能會擴充或重複使用。

### <a name="example"></a>範例

如需範例, 請參閱[IAtlMemMgr 總覽](../../atl/reference/iatlmemmgr-class.md)。

##  <a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowCoNtextMenu

`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示它自己的內容功能表。

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>參數

*pbAllowContextMenu*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_TRUE。

##  <a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI

`AllowShowUI`屬性會指定是否允許裝載的控制項顯示自己的使用者介面。

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>參數

*pbAllowShowUI*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_FALSE。

##  <a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation

`AllowWindowlessActivation`屬性會指定容器是否允許無視窗啟用。

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>參數

*pbAllowWindowless*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_TRUE。

##  <a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor

`BackColor`屬性會指定容器的環境背景色彩。

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>參數

*pclrBackground*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用 COLOR_BTNFACE 或 COLOR_WINDOW 做為此屬性的預設值 (視主機視窗的父系是否為對話而定)。

##  <a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault`是一種環境屬性, 可讓控制項找出它是否為預設控制項。

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>參數

*pbDisplayAsDefault*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_FALSE。

##  <a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`屬性會指定因應按兩下而應進行的作業。

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>參數

*pdwDocHostDoubleClickFlags*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 DOCHOSTUIDBLCLK_DEFAULT。

##  <a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags

`DocHostFlags`屬性會指定主機物件的使用者介面功能。

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>參數

*pdwDocHostFlags*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 DOCHOSTUIFLAG_NO3DBORDER。

##  <a name="get_font"></a>IAxWinAmbientDispatch::get_Font

`Font`屬性會指定容器的環境字型。

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
脫銷`IFontDisp`介面指標的位址, 用來接收這個屬性的目前值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用預設的 GUI 字型或系統字型做為此屬性的預設值。

##  <a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor

`ForeColor`屬性會指定容器的環境前景色彩。

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>參數

*pclrForeground*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用系統視窗文字色彩做為此屬性的預設值。

##  <a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID

`LocaleID`屬性會指定容器的環境地區設定識別碼。

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>參數

*plcidLocaleID*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用使用者的預設地區設定, 做為這個屬性的預設值。

使用此方法, 您可以探索環境 LocalID, 也就是您的控制項使用的程式 LocaleID。 一旦知道 LocaleID, 您就可以呼叫程式碼, 從資源檔或附屬 DLL 載入地區設定特定的標題、錯誤訊息正文等等。

##  <a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect

`MessageReflect`環境屬性會指定容器是否會反映裝載控制項的訊息。

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>參數

*pbMessageReflect*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_TRUE。

##  <a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath

`OptionKeyPath`屬性會指定使用者設定的登錄機碼路徑。

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>參數

*pbstrOptionKeyPath*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles

`ShowGrabHandles`環境屬性可讓控制項找出它是否應該使用抓取控點來繪製本身。

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>參數

*pbShowGrabHandles*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件的執行一律會傳回 VARIANT_FALSE 做為這個屬性的值。

##  <a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching

`ShowHatching`環境屬性可讓控制項找出它是否應該繪製其本身的影線。

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>參數

*pbShowHatching*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件的執行一律會傳回 VARIANT_FALSE 做為這個屬性的值。

##  <a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode

`UserMode`屬性會指定容器的環境使用者模式。

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>參數

*pbUserMode*<br/>
脫銷要接收此屬性目前值的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_TRUE。

##  <a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::p ut_AllowCoNtextMenu

`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示它自己的內容功能表。

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>參數

*bAllowContextMenu*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_TRUE。

##  <a name="put_allowshowui"></a>IAxWinAmbientDispatch::p ut_AllowShowUI

`AllowShowUI`屬性會指定是否允許裝載的控制項顯示自己的使用者介面。

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>參數

*bAllowShowUI*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_FALSE。

##  <a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::p ut_AllowWindowlessActivation

`AllowWindowlessActivation`屬性會指定容器是否允許無視窗啟用。

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>參數

*bAllowWindowless*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_TRUE。

##  <a name="put_backcolor"></a>IAxWinAmbientDispatch::p ut_BackColor

`BackColor`屬性會指定容器的環境背景色彩。

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>參數

*clrBackground*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用 COLOR_BTNFACE 或 COLOR_WINDOW 做為此屬性的預設值 (視主機視窗的父系是否為對話而定)。

##  <a name="put_displayasdefault"></a>IAxWinAmbientDispatch::p ut_DisplayAsDefault

`DisplayAsDefault`是一種環境屬性, 可讓控制項找出它是否為預設控制項。

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>參數

*bDisplayAsDefault*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_FALSE。

##  <a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::p ut_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`屬性會指定因應按兩下而應進行的作業。

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>參數

*dwDocHostDoubleClickFlags*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 DOCHOSTUIDBLCLK_DEFAULT。

##  <a name="put_dochostflags"></a>IAxWinAmbientDispatch::p ut_DocHostFlags

`DocHostFlags`屬性會指定主機物件的使用者介面功能。

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>參數

*dwDocHostFlags*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 DOCHOSTUIFLAG_NO3DBORDER。

##  <a name="put_font"></a>IAxWinAmbientDispatch::p ut_Font

`Font`屬性會指定容器的環境字型。

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用預設的 GUI 字型或系統字型做為此屬性的預設值。

##  <a name="put_forecolor"></a>IAxWinAmbientDispatch::p ut_ForeColor

`ForeColor`屬性會指定容器的環境前景色彩。

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>參數

*clrForeground*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用系統視窗文字色彩做為此屬性的預設值。

##  <a name="put_localeid"></a>IAxWinAmbientDispatch::p ut_LocaleID

`LocaleID`屬性會指定容器的環境地區設定識別碼。

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>參數

*lcidLocaleID*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用使用者的預設地區設定, 做為這個屬性的預設值。

##  <a name="put_messagereflect"></a>IAxWinAmbientDispatch::p ut_MessageReflect

`MessageReflect`環境屬性會指定容器是否會反映裝載控制項的訊息。

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>參數

*bMessageReflect*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_TRUE。

##  <a name="put_optionkeypath"></a>IAxWinAmbientDispatch::p ut_OptionKeyPath

`OptionKeyPath`屬性會指定使用者設定的登錄機碼路徑。

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>參數

*bstrOptionKeyPath*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="put_usermode"></a>IAxWinAmbientDispatch::p ut_UserMode

`UserMode`屬性會指定容器的環境使用者模式。

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>參數

*bUserMode*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件實作為此屬性的預設值使用 VARIANT_TRUE。

##  <a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch

呼叫這個方法時, 會使用使用者定義的介面來補充預設環境屬性介面。

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>參數

*pDispatch*<br/>
新介面的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

使用`SetAmbientDispatch`新介面的指標呼叫時, 如果[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)尚未提供這些屬性, 則這個新介面將用來叫用裝載控制項所要求的任何屬性或方法。

##  <a name="attachcontrol"></a>IAxWinHostWindow::AttachControl

使用*hWnd*所識別的視窗, 將現有 (和先前初始化的) 控制項附加至主機物件。

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>參數

*pUnkControl*<br/>
在要附加至主機`IUnknown`物件之控制項介面的指標。

*hWnd*<br/>
在要用於裝載之視窗的控制碼。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="createcontrol"></a>IAxWinHostWindow:: CreateControl

建立控制項、將它初始化, 然後將它裝載在*hWnd*所識別的視窗中。

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>參數

*lpTricsData*<br/>
在識別要建立之控制項的字串。 可以是 CLSID (必須包含大括弧)、ProgID、URL 或原始 HTML (前面加上**MSHTML:** )。

*hWnd*<br/>
在要用於裝載之視窗的控制碼。

*pStream*<br/>
在資料流程的介面指標, 包含控制項的初始化資料。 可以是 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

此視窗會由公開此介面的主物件子類別化, 讓訊息可以反映到控制項中, 而其他容器功能將會正常執行。

呼叫這個方法相當於呼叫[IAxWinHostWindow:: CreateControlEx](#createcontrolex)。

若要建立授權的 ActiveX 控制項, 請參閱[IAxWinHostWindowLic:: CreateControlLic](#createcontrollicex)。

##  <a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx

建立 ActiveX 控制項、將它初始化, 並將它裝載在指定的視窗中, 類似于[IAxWinHostWindow:: CreateControl](#createcontrol)。

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>參數

*lpTricsData*<br/>
在識別要建立之控制項的字串。 可以是 CLSID (必須包含大括弧)、ProgID、URL 或原始 HTML (前面加上**MSHTML:** )。

*hWnd*<br/>
在要用於裝載之視窗的控制碼。

*pStream*<br/>
在資料流程的介面指標, 包含控制項的初始化資料。 可以是 Null。

*ppUnk*<br/>
脫銷將接收`IUnknown`所建立控制項之介面的指標位址。 可以是 Null。

*riidAdvise*<br/>
在所包含物件上傳出介面的介面識別碼。 可以是 IID_Null。

*punkAdvise*<br/>
在接收物件`IUnknown`介面的指標, 要連接到所`iidSink`指定之包含物件上的連接點。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

與方法`CreateControl`不同的`CreateControlEx`是, 也可以讓您接收新建立之控制項的介面指標, 並設定事件接收以接收控制項所引發的事件。

若要建立授權的 ActiveX 控制項, 請參閱[IAxWinHostWindowLic:: CreateControlLicEx](#createcontrollicex)。

##  <a name="querycontrol"></a>IAxWinHostWindow::QueryControl

傳回裝載控制項所提供的指定介面指標。

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
在所要求之控制項上的介面識別碼。

*ppvObject*<br/>
脫銷將接收所建立控制項之指定介面的指標位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch

設定外部的分配介面, 透過[IDocHostUIHandlerDispatch:: GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md)方法可供包含的控制項使用。

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
在`IDispatch`介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler

呼叫此函式可設定`CAxWindow`物件的外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)介面。

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
在`IDocHostUIHandlerDispatch`介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

此函式是供查詢主機的網站以取得`IDocHostUIHandlerDispatch`介面的控制項 (例如 Web 瀏覽器控制項) 使用。

##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

建立授權的控制項、將它初始化, 然後將它裝載在所識別`hWnd`的視窗中。

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>參數

*bstrLic*<br/>
在包含控制項之授權金鑰的 BSTR。

### <a name="remarks"></a>備註

如需其餘參數和傳回值的描述, 請參閱[IAxWinHostWindow:: CreateControl](#createcontrol) 。

呼叫這個方法相當於呼叫[IAxWinHostWindowLic:: CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>範例

如需使用`IAxWinHostWindowLic::CreateControlLic`的範例, 請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

建立授權的 ActiveX 控制項、將它初始化, 並將它裝載在指定的視窗中, 類似于[IAxWinHostWindow:: CreateControl](#createcontrol)。

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>參數

*bstrLic*<br/>
在包含控制項之授權金鑰的 BSTR。

### <a name="remarks"></a>備註

如需其餘參數和傳回值的描述, 請參閱[IAxWinHostWindow:: CreateControlEx](#createcontrolex) 。

### <a name="example"></a>範例

如需使用`IAxWinHostWindowLic::CreateControlLicEx`的範例, 請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
