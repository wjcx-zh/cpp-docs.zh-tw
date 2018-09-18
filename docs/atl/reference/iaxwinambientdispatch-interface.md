---
title: IAxWinAmbientDispatch 介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cf8747275325332f6a2d0072e2c0ba2a66ae276
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057609"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch 介面

這個介面會提供方法來指定裝載的控制項或容器的特性。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示內容功能表。|
|[get_AllowShowUI](#get_allowshowui)|`AllowShowUI`屬性會指定是否允許裝載的控制項顯示自己的使用者介面。|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|`AllowWindowlessActivation`屬性中指定容器是否允許無視窗啟用。|
|[get_BackColor](#get_backcolor)|`BackColor`屬性會指定容器的環境背景色彩。|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` 為環境屬性，可讓您了解其是否預設控制項的控制。|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|`DocHostDoubleClickFlags`屬性會指定應該發生以回應按兩下作業。|
|[get_DocHostFlags](#get_dochostflags)|`DocHostFlags`屬性會指定主機物件的使用者介面功能。|
|[get_Font](#get_font)|`Font`屬性會指定容器的環境字型。|
|[get_ForeColor](#get_forecolor)|`ForeColor`屬性會指定容器的環境前景色彩。|
|[get_LocaleID](#get_localeid)|`LocaleID`屬性會指定容器的環境的地區設定識別碼。|
|[get_MessageReflect](#get_messagereflect)|`MessageReflect`環境屬性可讓您指定容器是否會反映裝載之控制項的訊息。|
|[get_OptionKeyPath](#get_optionkeypath)|`OptionKeyPath`屬性會指定使用者設定登錄機碼路徑。|
|[get_ShowGrabHandles](#get_showgrabhandles)|`ShowGrabHandles`環境屬性可讓您控制，若要了解是否它應該繪製本身的抓取控點。|
|[get_ShowHatching](#get_showhatching)|`ShowHatching`環境屬性可讓您了解如果它應該繪製本身影線控制。|
|[get_UserMode](#get_usermode)|`UserMode`屬性會指定容器的環境的使用者模式。|
|[put_AllowContextMenu](#put_allowcontextmenu)|`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示內容功能表。|
|[put_AllowShowUI](#put_allowshowui)|`AllowShowUI`屬性會指定是否允許裝載的控制項顯示自己的使用者介面。|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|`AllowWindowlessActivation`屬性中指定容器是否允許無視窗啟用。|
|[put_BackColor](#put_backcolor)|`BackColor`屬性會指定容器的環境背景色彩。|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` 為環境屬性，可讓您了解其是否預設控制項的控制。|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|`DocHostDoubleClickFlags`屬性會指定應該發生以回應按兩下作業。|
|[put_DocHostFlags](#put_dochostflags)|`DocHostFlags`屬性會指定主機物件的使用者介面功能。|
|[put_Font](#put_font)|`Font`屬性會指定容器的環境字型。|
|[put_ForeColor](#put_forecolor)|`ForeColor`屬性會指定容器的環境前景色彩。|
|[put_LocaleID](#put_localeid)|`LocaleID`屬性會指定容器的環境的地區設定識別碼。|
|[put_MessageReflect](#put_messagereflect)|`MessageReflect`環境屬性可讓您指定容器是否會反映裝載之控制項的訊息。|
|[put_OptionKeyPath](#put_optionkeypath)|`OptionKeyPath`屬性會指定使用者設定登錄機碼路徑。|
|[put_UserMode](#put_usermode)|`UserMode`屬性會指定容器的環境的使用者模式。|

## <a name="remarks"></a>備註

這個介面會公開由裝載物件的 ATL 的 ActiveX 控制項。 若要設定裝載的控制項可用的環境屬性，或指定的容器行為的其他層面，此介面上呼叫的方法。 若要補充所提供的屬性`IAxWinAmbientDispatch`，使用[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)。

[AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)會嘗試載入的型別資訊的相關`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`從型別程式庫包含程式碼。

如果您要連結至 ATL90.dll， **AXHost**將從型別程式庫 DLL 中載入的型別資訊。

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需詳細資訊。

## <a name="requirements"></a>需求

此介面的定義有數種格式，如下表所示。

|定義類型|檔案|
|---------------------|----------|
|IDL|atliface.idl|
|型別程式庫|ATL.dll|
|C++|atliface.h （也包含在 ATLBase.h）|

##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu

`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示內容功能表。

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>參數

*pbAllowContextMenu*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_TRUE。

##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI

`AllowShowUI`屬性會指定是否允許裝載的控制項顯示自己的使用者介面。

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>參數

*pbAllowShowUI*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_FALSE。

##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation

`AllowWindowlessActivation`屬性中指定容器是否允許無視窗啟用。

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>參數

*pbAllowWindowless*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_TRUE。

##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor

`BackColor`屬性會指定容器的環境背景色彩。

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>參數

*pclrBackground*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作使用 COLOR_BTNFACE 或 COLOR_WINDOW 做為預設值，這個屬性 （取決於是否在主視窗的父代為對話方塊）。

##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault` 為環境屬性，可讓您了解其是否預設控制項的控制。

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>參數

*pbDisplayAsDefault*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_FALSE。

##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`屬性會指定應該發生以回應按兩下作業。

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>參數

*pdwDocHostDoubleClickFlags*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用 DOCHOSTUIDBLCLK_DEFAULT，這個屬性的預設值。

##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags

`DocHostFlags`屬性會指定主機物件的使用者介面功能。

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>參數

*pdwDocHostFlags*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用 DOCHOSTUIFLAG_NO3DBORDER，這個屬性的預設值。

##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font

`Font`屬性會指定容器的環境字型。

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
[out]位址`IFontDisp`用來接收此屬性的目前值的介面指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作使用的預設 GUI 字型或系統字型做為這個屬性的預設值。

##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor

`ForeColor`屬性會指定容器的環境前景色彩。

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>參數

*pclrForeground*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為系統視窗的文字色彩。

##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID

`LocaleID`屬性會指定容器的環境的地區設定識別碼。

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>參數

*plcidLocaleID*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用使用者的預設地區設定作為預設值，這個屬性。

使用此方法中，您可以探索環境 LocalID，也就是程式的地區設定識別碼您控制項的使用中。 一旦您知道地區設定識別碼，您可以從呼叫程式碼載入地區設定特定原文字幕，錯誤訊息文字，等資源檔或附屬 DLL。

##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect

`MessageReflect`環境屬性可讓您指定容器是否會反映裝載之控制項的訊息。

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>參數

*pbMessageReflect*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_TRUE。

##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath

`OptionKeyPath`屬性會指定使用者設定登錄機碼路徑。

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>參數

*pbstrOptionKeyPath*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles

`ShowGrabHandles`環境屬性可讓您控制，若要了解是否它應該繪製本身的抓取控點。

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>參數

*pbShowGrabHandles*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作一律會傳回 VARIANT_FALSE 做為這個屬性的值。

##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching

`ShowHatching`環境屬性可讓您了解如果它應該繪製本身影線控制。

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>參數

*pbShowHatching*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作一律會傳回 VARIANT_FALSE 做為這個屬性的值。

##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode

`UserMode`屬性會指定容器的環境的使用者模式。

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>參數

*pbUserMode*<br/>
[out]要接收此屬性的目前值之變數的位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_TRUE。

##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu

`AllowContextMenu`屬性會指定是否允許裝載的控制項顯示內容功能表。

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>參數

*bAllowContextMenu*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_TRUE。

##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI

`AllowShowUI`屬性會指定是否允許裝載的控制項顯示自己的使用者介面。

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>參數

*bAllowShowUI*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_FALSE。

##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation

`AllowWindowlessActivation`屬性中指定容器是否允許無視窗啟用。

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>參數

*bAllowWindowless*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_TRUE。

##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor

`BackColor`屬性會指定容器的環境背景色彩。

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>參數

*clrBackground*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作使用 COLOR_BTNFACE 或 COLOR_WINDOW 做為預設值，這個屬性 （取決於是否在主視窗的父代為對話方塊）。

##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault` 為環境屬性，可讓您了解其是否預設控制項的控制。

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>參數

*bDisplayAsDefault*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_FALSE。

##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

`DocHostDoubleClickFlags`屬性會指定應該發生以回應按兩下作業。

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>參數

*dwDocHostDoubleClickFlags*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用 DOCHOSTUIDBLCLK_DEFAULT，這個屬性的預設值。

##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags

`DocHostFlags`屬性會指定主機物件的使用者介面功能。

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>參數

*dwDocHostFlags*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用 DOCHOSTUIFLAG_NO3DBORDER，這個屬性的預設值。

##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font

`Font`屬性會指定容器的環境字型。

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作使用的預設 GUI 字型或系統字型做為這個屬性的預設值。

##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor

`ForeColor`屬性會指定容器的環境前景色彩。

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>參數

*clrForeground*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為系統視窗的文字色彩。

##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID

`LocaleID`屬性會指定容器的環境的地區設定識別碼。

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>參數

*lcidLocaleID*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用使用者的預設地區設定作為預設值，這個屬性。

##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect

`MessageReflect`環境屬性可讓您指定容器是否會反映裝載之控制項的訊息。

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>參數

*bMessageReflect*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_TRUE。

##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath

`OptionKeyPath`屬性會指定使用者設定登錄機碼路徑。

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>參數

*bstrOptionKeyPath*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode

`UserMode`屬性會指定容器的環境的使用者模式。

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>參數

*bUserMode*<br/>
[in]此屬性的新值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_TRUE。

## <a name="see-also"></a>另請參閱

[IAxWinAmbientDispatchEx 介面](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHostWindow 介面](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)

