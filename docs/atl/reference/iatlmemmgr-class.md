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
ms.openlocfilehash: c296c9de79c305d0f7d2f135f250d181d3cd667a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330061"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr 類別

此類表示記憶體管理員的介面。

## <a name="syntax"></a>語法

```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[配置](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[自由](#free)|調用此方法以釋放記憶體塊。|
|[GetSize](#getsize)|調用此方法以檢索已分配記憶體塊的大小。|
|[重新分配](#reallocate)|調用此方法以重新分配記憶體區塊。|

## <a name="remarks"></a>備註

此介面由 CComHeap、CCRTHeap、CLocalHeap、CGlobalHeap 或[CWin32Heap](../../atl/reference/cwin32heap-class.md)實現。 [CComHeap](../../atl/reference/ccomheap-class.md) [CCRTHeap](../../atl/reference/ccrtheap-class.md) [CLocalHeap](../../atl/reference/clocalheap-class.md) [CGlobalHeap](../../atl/reference/cglobalheap-class.md)

> [!NOTE]
> 本地堆和全域堆函數比其他記憶體管理函數慢,並且不提供盡可能多的功能。 因此,新應用程式應使用[堆函數](/windows/win32/Memory/heap-functions)。 這些在[CWin32Heap](../../atl/reference/cwin32heap-class.md)類中可用。

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]

## <a name="requirements"></a>需求

**標題:** atlmem.h

## <a name="iatlmemmgrallocate"></a><a name="allocate"></a>IAtlMemMgr:分配

呼叫這個方法來配置記憶體區塊。

```
void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*n 位元組*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

調用[IAtlMemMgr::免費](#free)或[IAtlMemMgr:重新分配](#reallocate)以釋放此方法分配的記憶體。

### <a name="example"></a>範例

例如,請參閱[IAtlMemgr 概述](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iatlmemmgrfree"></a><a name="free"></a>IAtlMemMgr:免費

調用此方法以釋放記憶體塊。

```
void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。

### <a name="remarks"></a>備註

使用此方法釋放[IAtlMemMgr](#allocate)獲得的記憶體::分配或[IAtlMemmgr::重新分配](#reallocate)。

### <a name="example"></a>範例

例如,請參閱[IAtlMemgr 概述](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iatlmemmgrgetsize"></a><a name="getsize"></a>IAtlMemMgr:取得Size

調用此方法以檢索已分配記憶體塊的大小。

```
size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。

### <a name="return-value"></a>傳回值

返回記憶體塊的大小(以位元組為單位)。

### <a name="example"></a>範例

例如,請參閱[IAtlMemgr 概述](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iatlmemmgrreallocate"></a><a name="reallocate"></a>IAtlMemMgr:重新分配

呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。

```
void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。

*n 位元組*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

調用[IAtlMemMgr::免費](#free)或[IAtlMemMgr:重新分配](#reallocate)以釋放此方法分配的記憶體。

從概念上講,此方法會釋放現有記憶體並分配新的記憶體塊。 實際上,現有記憶體可能會擴展或以其他方式重用。

### <a name="example"></a>範例

例如,請參閱[IAtlMemgr 概述](../../atl/reference/iatlmemmgr-class.md)。

## <a name="iaxwinambientdispatchget_allowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWin 環境調度::get_AllowContextMenu

屬性`AllowContextMenu`指定是否允許托管控件顯示其自己的上下文菜單。

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>參數

*pbAllow 上下文選單*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_TRUE作為此屬性的預設值。

## <a name="iaxwinambientdispatchget_allowshowui"></a><a name="get_allowshowui"></a>IAxWin 環境調度::get_AllowShowUI

該`AllowShowUI`屬性指定是否允許托管控件顯示其自己的用戶介面。

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>參數

*pbAllowShowUI*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_FALSE作為此屬性的預設值。

## <a name="iaxwinambientdispatchget_allowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWin 環境調度::get_AllowWindowlessActivation

屬性`AllowWindowlessActivation`指定容器是否允許無視窗啟動。

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>參數

*pbAllow 無視窗*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_TRUE作為此屬性的預設值。

## <a name="iaxwinambientdispatchget_backcolor"></a><a name="get_backcolor"></a>IAxWin 環境調度::get_BackColor

屬性`BackColor`指定容器的環境背景顏色。

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>參數

*pclr背景*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用COLOR_BTNFACE或COLOR_WINDOW作為此屬性的預設值(取決於主機視窗的父物件是否是對話框)。

## <a name="iaxwinambientdispatchget_displayasdefault"></a><a name="get_displayasdefault"></a>IAxWin 環境調度::get_DisplayAsDefault

`DisplayAsDefault`是一個環境屬性,允許控件找出它是默認控制項。

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>參數

*pb 顯示AsDefault*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_FALSE作為此屬性的預設值。

## <a name="iaxwinambientdispatchget_dochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWin 環境調度::get_DocHostDoubleClickFlags

屬性`DocHostDoubleClickFlags`指定回應雙擊而應執行的操作。

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>參數

*pdwDocHost雙擊旗標*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用DOCHOSTUIDBLCLK_DEFAULT作為此屬性的預設值。

## <a name="iaxwinambientdispatchget_dochostflags"></a><a name="get_dochostflags"></a>IAxWin 環境調度::get_DocHostFlags

該`DocHostFlags`屬性指定主機物件的用戶介面功能。

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>參數

*pdwDocHostFlags*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用DOCHOSTUIFLAG_NO3DBORDER作為此屬性的預設值。

## <a name="iaxwinambientdispatchget_font"></a><a name="get_font"></a>IAxWin 環境調度::get_Font

屬性`Font`指定容器的環境字型。

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
[出]用於接收此屬性的`IFontDisp`當前值的介面指標的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用預設 GUI 字體或系統字體作為此屬性的預設值。

## <a name="iaxwinambientdispatchget_forecolor"></a><a name="get_forecolor"></a>IAxWin 環境調度::get_ForeColor

屬性`ForeColor`指定容器的環境前景顏色。

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>參數

*pclr前景*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用系統視窗文本顏色作為此屬性的預設值。

## <a name="iaxwinambientdispatchget_localeid"></a><a name="get_localeid"></a>IAxWin 環境調度::get_LocaleID

屬性`LocaleID`指定容器的環境區域設定 ID。

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>參數

*plcidLocaleID*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用使用者的預設區域設置作為此屬性的預設值。

使用此方法,您可以發現環境局部 ID,即控制項正在使用的程式的 LocaleID。 瞭解區域設定ID後,可以調用代碼從資源檔或附屬DLL載入特定於區域設置的標題、錯誤消息文本等。

## <a name="iaxwinambientdispatchget_messagereflect"></a><a name="get_messagereflect"></a>IAxWin 環境調度::get_MessageReflect

環境`MessageReflect`屬性指定容器是否將消息反映到托管控件。

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>參數

*pbMessage 反射*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_TRUE作為此屬性的預設值。

## <a name="iaxwinambientdispatchget_optionkeypath"></a><a name="get_optionkeypath"></a>IAxWin 環境調度::get_OptionKeyPath

該`OptionKeyPath`屬性指定用戶設置的註冊表鍵路徑。

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>參數

*pbstrOptionKeyPath*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinambientdispatchget_showgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWin 環境調度::get_ShowGrabHandles

環境`ShowGrabHandles`屬性允許控件找出是否應使用抓取手柄繪製自身。

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>參數

*pbShowGrabHandles*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機對象實現始終返回VARIANT_FALSE作為此屬性的值。

## <a name="iaxwinambientdispatchget_showhatching"></a><a name="get_showhatching"></a>IAxWin 環境調度::get_ShowHatching

環境`ShowHatching`屬性允許控件找出是否應繪製自身陰影。

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>參數

*pbShowHatching*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機對象實現始終返回VARIANT_FALSE作為此屬性的值。

## <a name="iaxwinambientdispatchget_usermode"></a><a name="get_usermode"></a>IAxWin 環境調度::get_UserMode

該`UserMode`屬性指定容器的環境使用者模式。

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>參數

*pbUser 模式*<br/>
[出]用於接收此屬性的當前值的變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_TRUE作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_allowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxwin 環境排程::put_允許上下文選單

屬性`AllowContextMenu`指定是否允許托管控件顯示其自己的上下文菜單。

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>參數

*bAllowContext選單*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_TRUE作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_allowshowui"></a><a name="put_allowshowui"></a>IAxWin 環境調度::put_允許ShowUI

該`AllowShowUI`屬性指定是否允許托管控件顯示其自己的用戶介面。

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>參數

*bAllowShowUI*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_FALSE作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_allowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxwin 環境排程::put_允許無視窗啟動

屬性`AllowWindowlessActivation`指定容器是否允許無視窗啟動。

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>參數

*bAllow 無視窗*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_TRUE作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_backcolor"></a><a name="put_backcolor"></a>IAxWin 環境調度::put_背面顏色

屬性`BackColor`指定容器的環境背景顏色。

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>參數

*clrBackground*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用COLOR_BTNFACE或COLOR_WINDOW作為此屬性的預設值(取決於主機視窗的父物件是否是對話框)。

## <a name="iaxwinambientdispatchput_displayasdefault"></a><a name="put_displayasdefault"></a>IAxWin 環境排程::put_顯示為預設

`DisplayAsDefault`是一個環境屬性,允許控件找出它是默認控制項。

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>參數

*b 顯示預設*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_FALSE作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_dochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxwin 環境調度::put_DocHost 雙鍵單擊標誌

屬性`DocHostDoubleClickFlags`指定回應雙擊而應執行的操作。

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>參數

*dwDocHost雙擊旗標*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用DOCHOSTUIDBLCLK_DEFAULT作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_dochostflags"></a><a name="put_dochostflags"></a>IAxWin 環境排程::put_DocHostFlags

該`DocHostFlags`屬性指定主機物件的用戶介面功能。

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>參數

*dwDocHostFlags*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用DOCHOSTUIFLAG_NO3DBORDER作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_font"></a><a name="put_font"></a>IAxWin 環境調度::put_Font

屬性`Font`指定容器的環境字型。

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用預設 GUI 字體或系統字體作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_forecolor"></a><a name="put_forecolor"></a>IAxWin 環境排程::put_ForeColor

屬性`ForeColor`指定容器的環境前景顏色。

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>參數

*clr前景*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用系統視窗文本顏色作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_localeid"></a><a name="put_localeid"></a>IAxWin 環境調度::put_localeID

屬性`LocaleID`指定容器的環境區域設定 ID。

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>參數

*lcidLocaleID*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用使用者的預設區域設置作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_messagereflect"></a><a name="put_messagereflect"></a>IAxWin 環境調度::put_消息反射

環境`MessageReflect`屬性指定容器是否將消息反映到托管控件。

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>參數

*b消息反射*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_TRUE作為此屬性的預設值。

## <a name="iaxwinambientdispatchput_optionkeypath"></a><a name="put_optionkeypath"></a>IAxWin 環境排程::put_選項關鍵路徑

該`OptionKeyPath`屬性指定用戶設置的註冊表鍵路徑。

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>參數

*bstrOptionKeyPath*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinambientdispatchput_usermode"></a><a name="put_usermode"></a>IAxWin 環境排程::put_使用者模式

該`UserMode`屬性指定容器的環境使用者模式。

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>參數

*使用者模式*<br/>
[在]此屬性的新值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實現使用VARIANT_TRUE作為此屬性的預設值。

## <a name="iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxwin 環境排程Ex::設定環境排程

呼叫此方法是為了使用使用者定義的介面補充預設環境屬性介面。

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>參數

*pDispatch*<br/>
指向新介面的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

當`SetAmbientDispatch`使用指向新介面的指標調用時,此新介面將用於調用託管控件要求的任何屬性或方法 - 如果這些屬性尚未由[IAxWinAmbient Dispatch](../../atl/reference/iaxwinambientdispatch-interface.md)提供。

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHost 視窗::附加控制

使用*hWnd*標識的視窗將現有(以前初始化)控制件附加到主機物件。

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>參數

*pUnkControl*<br/>
[在]指向要附加到主機`IUnknown`物件的控制埠介面的指標。

*hWnd*<br/>
[在]用於託管的視窗的句柄。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHost 視窗:建立控制

創建控制項,初始化它,並將其託管在*hWnd*識別的視窗中。

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>參數

*lpTricsData*<br/>
[在]識別要建立的控制項的字串。 可以是 CLSID(必須包括大括號)、ProgID、URL 或原始 HTML(由**MSHTML**預置: 。

*hWnd*<br/>
[在]用於託管的視窗的句柄。

*pStream*<br/>
[在]包含控制程式初始化資料的流的介面指標。 可以是 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此視窗將由公開此介面的主機物件進行子分類,以便消息可以反射到控制項,其他容器功能將起作用。

呼叫此方法等效於呼叫[IAxWinHostWindow::createControlEx](#createcontrolex)。

要建立授權的 ActiveX 控制件,請參閱[IAxWinHostWindowlic::建立控制項](#createcontrollicex)。

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHost 視窗:建立控制Ex

建立一個 ActiveX 控制件,初始化它,並將其託管在指定的視窗中,類似於[IAxWinHostWindow::建立控制](#createcontrol)。

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
[在]識別要建立的控制項的字串。 可以是 CLSID(必須包括大括號)、ProgID、URL 或原始 HTML(與**MSHTML**一起預置碼: 。

*hWnd*<br/>
[在]用於託管的視窗的句柄。

*pStream*<br/>
[在]包含控制程式初始化資料的流的介面指標。 可以是 NULL。

*普恩克*<br/>
[出]將接收創建控制項介面`IUnknown`的指標的位址。 可以是 NULL。

*里德建議*<br/>
[在]包含物件上傳出介面的介面標識符。 可以IID_NULL。

*龐克建議*<br/>
[在]指向要連接到`IUnknown`所指定包含物件的連接點的接收器物件的介面的`iidSink`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

與`CreateControl`方法不同`CreateControlEx`,還允許您接收指向新創建的控制項的介面指標,並設置事件接收器以接收控制項觸發的事件。

要建立授權的 ActiveX 控制件,請參閱[IAxWinHostWindowlic::建立控制項](#createcontrollicex)。

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHost 視窗::查詢控制

返回托管控件提供的指定介面指標。

```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
[在]請求的控制項上的介面的 ID。

*ppvObject*<br/>
[出]將接收已創建控制項的指定介面的指標的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHost 視窗::設定外部排程

設置外部介面,可透過[IDocHostUIHandlerDispatch:get 外部](../../atl/reference/idochostuihandlerdispatch-interface.md)方法包含控制項。

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
[在]指向介面的`IDispatch`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHost 視窗::設定外部 UIHandler

呼叫此函數以設定`CAxWindow`物件的外部[IDocHostUIHandlerDispatch 介面](../../atl/reference/idochostuihandlerdispatch-interface.md)。

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
[在]指向介面的`IDocHostUIHandlerDispatch`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此函數由查詢主機網站的`IDocHostUIHandlerDispatch`介面的控制項(如Web瀏覽器控制項)使用。

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostwindowlic::建立控制

建立許可控制項,初始化它,並將其託管在識別的`hWnd`視窗中。

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>參數

*bstrLIC*<br/>
[在]包含控制項的授權金鑰的 BSTR。

### <a name="remarks"></a>備註

有關剩餘參數和返回值的說明,請參閱[IAxWinHostWindow:建立控制](#createcontrol)。

呼叫此方法等效於呼叫[IAxWinHostWindowlic::建立控制](#createcontrollicex)

### <a name="example"></a>範例

有關`IAxWinHostWindowLic::CreateControlLic`使用的樣本,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHost視窗::建立控制

建立授權的 ActiveX 控制件,初始化它,並將其託管在指定的視窗中,類似於[IAxWinHostWindow::建立控制](#createcontrol)。

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

*bstrLIC*<br/>
[在]包含控制項的授權金鑰的 BSTR。

### <a name="remarks"></a>備註

有關剩餘參數和返回值的說明,請參閱[IAxWinHostWindow:創建ControlEx。](#createcontrolex)

### <a name="example"></a>範例

有關`IAxWinHostWindowLic::CreateControlLicEx`使用的樣本,請參閱[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)託管 ActiveX 控制件。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
