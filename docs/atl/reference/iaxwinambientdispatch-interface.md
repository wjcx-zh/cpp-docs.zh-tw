---
title: IAxWin 環境排程介面
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
ms.openlocfilehash: 6a4f5322d957b1e978bd123db3b4796be6b300da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330014"
---
# <a name="iaxwinambientdispatch-interface"></a>IAxWin 環境排程介面

此介面提供用於指定托管控件或容器特徵的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|屬性`AllowContextMenu`指定是否允許托管控件顯示其自己的上下文菜單。|
|[get_AllowShowUI](#get_allowshowui)|該`AllowShowUI`屬性指定是否允許托管控件顯示其自己的用戶介面。|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|屬性`AllowWindowlessActivation`指定容器是否允許無視窗啟動。|
|[get_BackColor](#get_backcolor)|屬性`BackColor`指定容器的環境背景顏色。|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault`是一個環境屬性,允許控件找出它是默認控制項。|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|屬性`DocHostDoubleClickFlags`指定回應雙擊而應執行的操作。|
|[get_DocHostFlags](#get_dochostflags)|該`DocHostFlags`屬性指定主機物件的用戶介面功能。|
|[get_Font](#get_font)|屬性`Font`指定容器的環境字型。|
|[get_ForeColor](#get_forecolor)|屬性`ForeColor`指定容器的環境前景顏色。|
|[get_LocaleID](#get_localeid)|屬性`LocaleID`指定容器的環境區域設定 ID。|
|[get_MessageReflect](#get_messagereflect)|環境`MessageReflect`屬性指定容器是否將消息反映到托管控件。|
|[get_OptionKeyPath](#get_optionkeypath)|該`OptionKeyPath`屬性指定用戶設置的註冊表鍵路徑。|
|[get_ShowGrabHandles](#get_showgrabhandles)|環境`ShowGrabHandles`屬性允許控件找出是否應使用抓取手柄繪製自身。|
|[get_ShowHatching](#get_showhatching)|環境`ShowHatching`屬性允許控件找出是否應繪製自身陰影。|
|[get_UserMode](#get_usermode)|該`UserMode`屬性指定容器的環境使用者模式。|
|[put_AllowContextMenu](#put_allowcontextmenu)|屬性`AllowContextMenu`指定是否允許托管控件顯示其自己的上下文菜單。|
|[put_AllowShowUI](#put_allowshowui)|該`AllowShowUI`屬性指定是否允許托管控件顯示其自己的用戶介面。|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|屬性`AllowWindowlessActivation`指定容器是否允許無視窗啟動。|
|[put_BackColor](#put_backcolor)|屬性`BackColor`指定容器的環境背景顏色。|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault`是一個環境屬性,允許控件找出它是默認控制項。|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|屬性`DocHostDoubleClickFlags`指定回應雙擊而應執行的操作。|
|[put_DocHostFlags](#put_dochostflags)|該`DocHostFlags`屬性指定主機物件的用戶介面功能。|
|[put_Font](#put_font)|屬性`Font`指定容器的環境字型。|
|[put_ForeColor](#put_forecolor)|屬性`ForeColor`指定容器的環境前景顏色。|
|[put_LocaleID](#put_localeid)|屬性`LocaleID`指定容器的環境區域設定 ID。|
|[put_MessageReflect](#put_messagereflect)|環境`MessageReflect`屬性指定容器是否將消息反映到托管控件。|
|[put_OptionKeyPath](#put_optionkeypath)|該`OptionKeyPath`屬性指定用戶設置的註冊表鍵路徑。|
|[put_UserMode](#put_usermode)|該`UserMode`屬性指定容器的環境使用者模式。|

## <a name="remarks"></a>備註

此介面由 ATL 的 ActiveX 控制項託管物件公開。 呼叫此介面上的方法以設置托管控件可用的環境屬性或指定容器行為的其他方面。 要補充`IAxWinAmbientDispatch`提供的屬性,請使用[IAxWin 環境排程Ex](../../atl/reference/iaxwinambientdispatchex-interface.md)。

<xref:System.Windows.Forms.AxHost>將嘗試載入有關`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`從包含代碼的 typelib 的類型資訊。

如果要連結到 ATL90.dll,AXHost 將從 DLL 中的 typelib**AXHost**載入類型資訊。

有關詳細資訊[,請參閱使用 ATL AXHost 託管 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

## <a name="requirements"></a>需求

此介面的定義有多種形式,如下表所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|atliface.idl|
|類型庫|ATL.dll|
|C++|atliface.h (也包含在 ATLBase.h 中)|

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

## <a name="see-also"></a>另請參閱

[IAxwin 環境排程Ex 介面](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[IAxWinHost 視窗介面](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAx 視窗::查詢主機](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
