---
title: IAxWinAmbientDispatch 介面
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: a53481a57676b5b4a253a3501d3536e5115907a7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833409"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch 介面

這個介面會提供方法來指定託管控制項或容器的特性。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|-|-|
|[get_AllowCoNtextMenu](#get_allowcontextmenu)|`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示它自己的內容功能表。|
|[get_AllowShowUI](#get_allowshowui)|`AllowShowUI`屬性會指定是否允許裝載控制項顯示它自己的使用者介面。|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|`AllowWindowlessActivation`屬性會指定容器是否允許無視窗啟用。|
|[get_BackColor](#get_backcolor)|`BackColor`屬性會指定容器的環境背景色彩。|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` 是一個環境屬性，可讓控制項知道它是否為預設控制項。|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|`DocHostDoubleClickFlags`屬性會指定回應按兩下所應採取的操作。|
|[get_DocHostFlags](#get_dochostflags)|`DocHostFlags`屬性會指定主物件的使用者介面功能。|
|[get_Font](#get_font)|`Font`屬性會指定容器的環境字型。|
|[get_ForeColor](#get_forecolor)|`ForeColor`屬性會指定容器的環境前景色彩。|
|[get_LocaleID](#get_localeid)|`LocaleID`屬性會指定容器的環境地區設定識別碼。|
|[get_MessageReflect](#get_messagereflect)|`MessageReflect`環境屬性會指定容器是否會反映裝載控制項的訊息。|
|[get_OptionKeyPath](#get_optionkeypath)|`OptionKeyPath`屬性會指定使用者設定的登錄機碼路徑。|
|[get_ShowGrabHandles](#get_showgrabhandles)|`ShowGrabHandles`環境屬性可讓控制項知道它是否應該以抓取控點來繪製本身。|
|[get_ShowHatching](#get_showhatching)|`ShowHatching`環境屬性可讓控制項找出它是否應該繪製自己的影線。|
|[get_UserMode](#get_usermode)|`UserMode`屬性會指定容器的環境使用者模式。|
|[put_AllowCoNtextMenu](#put_allowcontextmenu)|`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示它自己的內容功能表。|
|[put_AllowShowUI](#put_allowshowui)|`AllowShowUI`屬性會指定是否允許裝載控制項顯示它自己的使用者介面。|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|`AllowWindowlessActivation`屬性會指定容器是否允許無視窗啟用。|
|[put_BackColor](#put_backcolor)|`BackColor`屬性會指定容器的環境背景色彩。|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` 是一個環境屬性，可讓控制項知道它是否為預設控制項。|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|`DocHostDoubleClickFlags`屬性會指定回應按兩下所應採取的操作。|
|[put_DocHostFlags](#put_dochostflags)|`DocHostFlags`屬性會指定主物件的使用者介面功能。|
|[put_Font](#put_font)|`Font`屬性會指定容器的環境字型。|
|[put_ForeColor](#put_forecolor)|`ForeColor`屬性會指定容器的環境前景色彩。|
|[put_LocaleID](#put_localeid)|`LocaleID`屬性會指定容器的環境地區設定識別碼。|
|[put_MessageReflect](#put_messagereflect)|`MessageReflect`環境屬性會指定容器是否會反映裝載控制項的訊息。|
|[put_OptionKeyPath](#put_optionkeypath)|`OptionKeyPath`屬性會指定使用者設定的登錄機碼路徑。|
|[put_UserMode](#put_usermode)|`UserMode`屬性會指定容器的環境使用者模式。|

## <a name="remarks"></a>備註

這個介面是由 ATL 的 ActiveX 控制項裝載物件所公開。 呼叫這個介面上的方法，將環境屬性設為可供裝載的控制項使用，或指定容器行為的其他層面。 若要補充提供的屬性 `IAxWinAmbientDispatch` ，請使用 [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)。

<xref:System.Windows.Forms.AxHost> 將會嘗試 `IAxWinAmbientDispatch` `IAxWinAmbientDispatchEx` 從包含程式碼的 typelib 載入的類型資訊。

如果您要連結至 ATL90.dll， **AXHost** 會從 DLL 中的 typelib 載入類型資訊。

如需詳細資訊，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) 。

## <a name="requirements"></a>規格需求

此介面的定義提供數種形式，如下表所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|atliface .idl|
|類型程式庫|ATL.dll|
|C++|atliface 也會包含在 Atlbase.h 中 () |

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

## <a name="see-also"></a>另請參閱

[IAxWinAmbientDispatchEx 介面](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow 介面](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow：： QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
