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
ms.openlocfilehash: a33414ec1c1b01742382150049f8e99f4a70ae34
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833422"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr 類別

此類別代表記憶體管理員的介面。

## <a name="syntax"></a>語法

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|-|-|
|[分配](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[免費](#free)|呼叫這個方法來釋放記憶體區塊。|
|[GetSize](#getsize)|呼叫這個方法，以取得配置的記憶體區塊大小。|
|[重新配置](#reallocate)|呼叫這個方法來重新配置記憶體區塊。|

## <a name="remarks"></a>備註

此介面是由 [CComHeap](../../atl/reference/ccomheap-class.md)、 [CCRTHeap](../../atl/reference/ccrtheap-class.md)、 [CLocalHeap](../../atl/reference/clocalheap-class.md)、 [CGlobalHeap](../../atl/reference/cglobalheap-class.md)或 [CWin32Heap](../../atl/reference/cwin32heap-class.md)所執行。

> [!NOTE]
> 本機和全域堆積函數比其他記憶體管理函數慢，而且不提供許多功能。 因此，新的應用程式應該使用 [堆積函數](/windows/win32/Memory/heap-functions)。 這些都可在 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 類別中使用。

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>規格需求

**標頭：** atlmem。h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a> IAtlMemMgr：： Allocate

呼叫這個方法來配置記憶體區塊。

```cpp
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*n*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫 [IAtlMemMgr：： Free](#free) 或 [IAtlMemMgr：：](#reallocate) 重新配置，以釋放這個方法所配置的記憶體。

### <a name="example"></a>範例

如需範例，請參閱 [IAtlMemMgr 總覽](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iatlmemmgrfree"></a><a name="free"></a> IAtlMemMgr：： Free

呼叫這個方法來釋放記憶體區塊。

```cpp
void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。

### <a name="remarks"></a>備註

您可以使用這個方法來釋放 [IAtlMemMgr：： Allocate](#allocate) 或 [IAtlMemMgr：：](#reallocate)重新配置所取得的記憶體。

### <a name="example"></a>範例

如需範例，請參閱 [IAtlMemMgr 總覽](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a> IAtlMemMgr：： GetSize

呼叫這個方法，以取得配置的記憶體區塊大小。

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。

### <a name="return-value"></a>傳回值

傳回記憶體區塊的大小（以位元組為單位）。

### <a name="example"></a>範例

如需範例，請參閱 [IAtlMemMgr 總覽](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a> IAtlMemMgr：：重新配置

呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。

```cpp
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。

*n*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫 [IAtlMemMgr：： Free](#free) 或 [IAtlMemMgr：：](#reallocate) 重新配置，以釋放這個方法所配置的記憶體。

就概念而言，這個方法會釋出現有的記憶體，並配置新的記憶體區塊。 在現實情況下，現有的記憶體可能會擴充或重複使用。

### <a name="example"></a>範例

如需範例，請參閱 [IAtlMemMgr 總覽](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a> IAxWinAmbientDispatch：： get_AllowCoNtextMenu

`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示它自己的內容功能表。

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>參數

*pbAllowCoNtextMenu*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_TRUE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a> IAxWinAmbientDispatch：： get_AllowShowUI

`AllowShowUI`屬性會指定是否允許裝載控制項顯示它自己的使用者介面。

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>參數

*pbAllowShowUI*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_FALSE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a> IAxWinAmbientDispatch：： get_AllowWindowlessActivation

`AllowWindowlessActivation`屬性會指定容器是否允許無視窗啟用。

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>參數

*pbAllowWindowless*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_TRUE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a> IAxWinAmbientDispatch：： get_BackColor

`BackColor`屬性會指定容器的環境背景色彩。

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>參數

*pclrBackground*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 COLOR_BTNFACE 或 COLOR_WINDOW 做為這個屬性的預設值 (取決於主視窗的父系是對話方塊或不) 。

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a> IAxWinAmbientDispatch：： get_DisplayAsDefault

`DisplayAsDefault` 是一個環境屬性，可讓控制項知道它是否為預設控制項。

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>參數

*pbDisplayAsDefault*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_FALSE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a> IAxWinAmbientDispatch：： get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`屬性會指定回應按兩下所應採取的操作。

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>參數

*pdwDocHostDoubleClickFlags*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 DOCHOSTUIDBLCLK_DEFAULT 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a> IAxWinAmbientDispatch：： get_DocHostFlags

`DocHostFlags`屬性會指定主物件的使用者介面功能。

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>參數

*pdwDocHostFlags*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 DOCHOSTUIFLAG_NO3DBORDER 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a> IAxWinAmbientDispatch：： get_Font

`Font`屬性會指定容器的環境字型。

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
擴展介面指標的位址， `IFontDisp` 用來接收這個屬性的目前值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用預設的 GUI 字型或系統字型作為這個屬性的預設值。

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a> IAxWinAmbientDispatch：： get_ForeColor

`ForeColor`屬性會指定容器的環境前景色彩。

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>參數

*pclrForeground*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用系統視窗文字色彩做為這個屬性的預設值。

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a> IAxWinAmbientDispatch：： get_LocaleID

`LocaleID`屬性會指定容器的環境地區設定識別碼。

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>參數

*plcidLocaleID*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用使用者的預設地區設定做為這個屬性的預設值。

使用這個方法時，您可以探索環境 LocalID，也就是您的控制項使用的程式 LocaleID。 知道 LocaleID 之後，您就可以呼叫程式碼，從資源檔或附屬 DLL 載入地區設定特定的標題、錯誤訊息正文等等。

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a> IAxWinAmbientDispatch：： get_MessageReflect

`MessageReflect`環境屬性會指定容器是否會反映裝載控制項的訊息。

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>參數

*pbMessageReflect*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_TRUE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a> IAxWinAmbientDispatch：： get_OptionKeyPath

`OptionKeyPath`屬性會指定使用者設定的登錄機碼路徑。

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>參數

*pbstrOptionKeyPath*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a> IAxWinAmbientDispatch：： get_ShowGrabHandles

`ShowGrabHandles`環境屬性可讓控制項知道它是否應該以抓取控點來繪製本身。

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>參數

*pbShowGrabHandles*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行一律會傳回 VARIANT_FALSE 做為這個屬性的值。

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a> IAxWinAmbientDispatch：： get_ShowHatching

`ShowHatching`環境屬性可讓控制項找出它是否應該繪製自己的影線。

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>參數

*pbShowHatching*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行一律會傳回 VARIANT_FALSE 做為這個屬性的值。

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a> IAxWinAmbientDispatch：： get_UserMode

`UserMode`屬性會指定容器的環境使用者模式。

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>參數

*pbUserMode*<br/>
擴展要接收這個屬性之目前值的變數位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_TRUE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a> IAxWinAmbientDispatch：:p ut_AllowCoNtextMenu

`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示它自己的內容功能表。

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>參數

*bAllowCoNtextMenu*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_TRUE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a> IAxWinAmbientDispatch：:p ut_AllowShowUI

`AllowShowUI`屬性會指定是否允許裝載控制項顯示它自己的使用者介面。

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>參數

*bAllowShowUI*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_FALSE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a> IAxWinAmbientDispatch：:p ut_AllowWindowlessActivation

`AllowWindowlessActivation`屬性會指定容器是否允許無視窗啟用。

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>參數

*bAllowWindowless*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_TRUE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a> IAxWinAmbientDispatch：:p ut_BackColor

`BackColor`屬性會指定容器的環境背景色彩。

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>參數

*clrBackground*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 COLOR_BTNFACE 或 COLOR_WINDOW 做為這個屬性的預設值 (取決於主視窗的父系是對話方塊或不) 。

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a> IAxWinAmbientDispatch：:p ut_DisplayAsDefault

`DisplayAsDefault` 是一個環境屬性，可讓控制項知道它是否為預設控制項。

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>參數

*bDisplayAsDefault*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_FALSE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a> IAxWinAmbientDispatch：:p ut_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`屬性會指定回應按兩下所應採取的操作。

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>參數

*dwDocHostDoubleClickFlags*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 DOCHOSTUIDBLCLK_DEFAULT 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a> IAxWinAmbientDispatch：:p ut_DocHostFlags

`DocHostFlags`屬性會指定主物件的使用者介面功能。

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>參數

*dwDocHostFlags*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 DOCHOSTUIFLAG_NO3DBORDER 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a> IAxWinAmbientDispatch：:p ut_Font

`Font`屬性會指定容器的環境字型。

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用預設的 GUI 字型或系統字型作為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a> IAxWinAmbientDispatch：:p ut_ForeColor

`ForeColor`屬性會指定容器的環境前景色彩。

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>參數

*clrForeground*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用系統視窗文字色彩做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a> IAxWinAmbientDispatch：:p ut_LocaleID

`LocaleID`屬性會指定容器的環境地區設定識別碼。

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>參數

*lcidLocaleID*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主控制項物件執行會使用使用者的預設地區設定做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a> IAxWinAmbientDispatch：:p ut_MessageReflect

`MessageReflect`環境屬性會指定容器是否會反映裝載控制項的訊息。

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>參數

*bMessageReflect*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_TRUE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a> IAxWinAmbientDispatch：:p ut_OptionKeyPath

`OptionKeyPath`屬性會指定使用者設定的登錄機碼路徑。

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>參數

*bstrOptionKeyPath*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a> IAxWinAmbientDispatch：:p ut_UserMode

`UserMode`屬性會指定容器的環境使用者模式。

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>參數

*bUserMode*<br/>
在這個屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主物件的執行會使用 VARIANT_TRUE 做為這個屬性的預設值。

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a> IAxWinAmbientDispatchEx：： SetAmbientDispatch

呼叫這個方法來補充具有使用者定義介面的預設環境屬性介面。

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>參數

*pDispatch*<br/>
新介面的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

當 `SetAmbientDispatch` 使用新介面的指標呼叫時，這個新介面將用來叫用裝載控制項所要求的任何屬性或方法（如果 [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)尚未提供這些屬性）。

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a> IAxWinHostWindow：： AttachControl

使用 *hWnd*所識別的視窗，將現有的 (和先前初始化的) 控制項附加至主物件。

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>參數

*pUnkControl*<br/>
在要 `IUnknown` 附加至主控制項物件之控制項介面的指標。

*hWnd*<br/>
在要用於裝載的視窗控制碼。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a> IAxWinHostWindow：： CreateControl

建立控制項、將它初始化，然後將它裝載在 *hWnd*所識別的視窗中。

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>參數

*lpTricsData*<br/>
在識別要建立之控制項的字串。 可以是 CLSID (必須包含大括弧) 、ProgID、URL 或原始 HTML (前面加上 **MSHTML：**) 。

*hWnd*<br/>
在要用於裝載的視窗控制碼。

*pStream*<br/>
在資料流程的介面指標，包含控制項的初始化資料。 可以是 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此視窗會由公開此介面的主機物件進行子類別化，如此一來，就可以將訊息反映到控制項，而且其他容器功能將會運作。

呼叫這個方法相當於呼叫 [IAxWinHostWindow：： CreateControlEx](#createcontrolex)。

若要建立授權的 ActiveX 控制項，請參閱 [IAxWinHostWindowLic：： CreateControlLic](#createcontrollicex)。

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a> IAxWinHostWindow：： CreateControlEx

建立 ActiveX 控制項、將它初始化，然後將它裝載于指定的視窗中，類似于 [IAxWinHostWindow：： CreateControl](#createcontrol)。

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
在識別要建立之控制項的字串。 可以是 CLSID (必須包含大括弧) 、ProgID、URL 或原始 HTML (前面加上 **MSHTML：**) 。

*hWnd*<br/>
在要用於裝載的視窗控制碼。

*pStream*<br/>
在資料流程的介面指標，包含控制項的初始化資料。 可以是 NULL。

*ppUnk*<br/>
擴展將接收 `IUnknown` 所建立控制項介面之指標的位址。 可以是 NULL。

*riidAdvise*<br/>
在包含物件上之輸出介面的介面識別碼。 可以是 IID_Null。

*punkAdvise*<br/>
在要 `IUnknown` 連接到所指定之所包含物件上連接點的接收物件介面指標 `iidSink` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

與方法不同的是 `CreateControl` ， `CreateControlEx` 也可讓您接收新建立之控制項的介面指標，並設定事件接收以接收控制項所引發的事件。

若要建立授權的 ActiveX 控制項，請參閱 [IAxWinHostWindowLic：： CreateControlLicEx](#createcontrollicex)。

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a> IAxWinHostWindow：： QueryControl

傳回裝載控制項所提供的指定介面指標。

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
在所要求控制項上介面的識別碼。

*ppvObject*<br/>
擴展將接收所建立控制項之指定介面之指標的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> IAxWinHostWindow：： SetExternalDispatch

設定可透過 [IDocHostUIHandlerDispatch：： GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) 方法供包含的控制項使用的外部介面。

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
在介面的指標 `IDispatch` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> IAxWinHostWindow：： SetExternalUIHandler

呼叫此函式可設定物件的外部 [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) 介面 `CAxWindow` 。

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
在介面的指標 `IDocHostUIHandlerDispatch` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

這個函式是由控制項 (使用，例如 Web 瀏覽器控制項) ，可查詢主機的 `IDocHostUIHandlerDispatch` 介面。

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a> IAxWinHostWindowLic：： CreateControlLic

建立授權的控制項、將它初始化，然後將它裝載在所識別的視窗中 `hWnd` 。

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>參數

*bstrLic*<br/>
在包含控制項授權金鑰的 BSTR。

### <a name="remarks"></a>備註

如需其餘參數和傳回值的描述，請參閱 [IAxWinHostWindow：： CreateControl](#createcontrol) 。

呼叫這個方法相當於呼叫 [IAxWinHostWindowLic：： CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>範例

如需使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) `IAxWinHostWindowLic::CreateControlLic` 。

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a> IAxWinHostWindowLic：： CreateControlLicEx

建立授權的 ActiveX 控制項、將它初始化，然後將它裝載于指定的視窗中，類似于 [IAxWinHostWindow：： CreateControl](#createcontrol)。

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
在包含控制項授權金鑰的 BSTR。

### <a name="remarks"></a>備註

如需其餘參數和傳回值的描述，請參閱 [IAxWinHostWindow：： CreateControlEx](#createcontrolex) 。

### <a name="example"></a>範例

如需使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) `IAxWinHostWindowLic::CreateControlLicEx` 。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
