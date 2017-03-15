---
title: "IAxWinAmbientDispatch 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatch
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 2352b970c81f58d164fb47a6d7a4728c708d864a
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinambientdispatch-interface"></a>IAxWinAmbientDispatch 介面
這個介面會提供方法來指定裝載的控制項或容器的特性。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
interface IAxWinAmbientDispatch : IDispatch
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[get_AllowContextMenu](#get_allowcontextmenu)|**AllowContextMenu**屬性會指定是否允許裝載的控制項顯示快顯功能表。|  
|[get_AllowShowUI](#get_allowshowui)|**AllowShowUI**屬性會指定是否允許裝載的控制項顯示使用者介面。|  
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|**AllowWindowlessActivation**屬性中指定容器是否允許無視窗啟用。|  
|[get_BackColor](#get_backcolor)|`BackColor`屬性會指定容器的環境背景色彩。|  
|[get_DisplayAsDefault](#get_displayasdefault)|**DisplayAsDefault**是環境的屬性，可讓控制項以瞭解其是否預設控制項。|  
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|**DocHostDoubleClickFlags**屬性會指定應在回應按兩下作業。|  
|[get_DocHostFlags](#get_dochostflags)|**DocHostFlags**屬性會指定主應用程式物件的使用者介面功能。|  
|[get_Font](#get_font)|**字型**屬性會指定容器的環境字型。|  
|[get_ForeColor](#get_forecolor)|`ForeColor`屬性會指定容器的環境前景色彩。|  
|[get_LocaleID](#get_localeid)|**LocaleID**屬性會指定容器的環境的地區設定識別碼。|  
|[get_MessageReflect](#get_messagereflect)|**MessageReflect**環境屬性會指定容器是否會反映在裝載控制項的訊息。|  
|[get_OptionKeyPath](#get_optionkeypath)|**OptionKeyPath**屬性會指定使用者設定登錄機碼路徑。|  
|[get_ShowGrabHandles](#get_showgrabhandles)|**ShowGrabHandles**環境屬性可以讓要了解是否它本身應該具有抓取控點來繪製的控制項。|  
|[get_ShowHatching](#get_showhatching)|**ShowHatching**環境屬性可以讓控制項以找出是否它應該繪製本身影線。|  
|[get_UserMode](#get_usermode)|**UserMode**屬性會指定容器的環境的使用者模式。|  
|[put_AllowContextMenu](#put_allowcontextmenu)|**AllowContextMenu**屬性會指定是否允許裝載的控制項顯示快顯功能表。|  
|[put_AllowShowUI](#put_allowshowui)|**AllowShowUI**屬性會指定是否允許裝載的控制項顯示使用者介面。|  
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|**AllowWindowlessActivation**屬性中指定容器是否允許無視窗啟用。|  
|[put_BackColor](#put_backcolor)|`BackColor`屬性會指定容器的環境背景色彩。|  
|[put_DisplayAsDefault](#put_displayasdefault)|**DisplayAsDefault**是環境的屬性，可讓控制項以瞭解其是否預設控制項。|  
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|**DocHostDoubleClickFlags**屬性會指定應在回應按兩下作業。|  
|[put_DocHostFlags](#put_dochostflags)|**DocHostFlags**屬性會指定主應用程式物件的使用者介面功能。|  
|[put_Font](#put_font)|**字型**屬性會指定容器的環境字型。|  
|[put_ForeColor](#put_forecolor)|`ForeColor`屬性會指定容器的環境前景色彩。|  
|[put_LocaleID](#put_localeid)|**LocaleID**屬性會指定容器的環境的地區設定識別碼。|  
|[put_MessageReflect](#put_messagereflect)|**MessageReflect**環境屬性會指定容器是否會反映在裝載控制項的訊息。|  
|[put_OptionKeyPath](#put_optionkeypath)|**OptionKeyPath**屬性會指定使用者設定登錄機碼路徑。|  
|[put_UserMode](#put_usermode)|**UserMode**屬性會指定容器的環境的使用者模式。|  
  
## <a name="remarks"></a>備註  
 這個介面是由 ATL 的 ActiveX 控制項裝載物件公開。 若要設定裝載的控制項可用的環境屬性，或指定容器的行為的其他層面，此介面上呼叫的方法。 若要補充所提供的屬性`IAxWinAmbientDispatch`，使用[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)。  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)將會嘗試載入型別資訊有關`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`從型別程式庫包含程式碼。  
  
 如果您要連結至 ATL90.dll， **AXHost**會從型別程式庫 DLL 中載入的型別資訊。  
  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需詳細資訊。  
  
## <a name="requirements"></a>需求  
 此介面的定義有數種格式，如下表所示。  
  
|定義類型|檔案|  
|---------------------|----------|  
|IDL|atliface.idl|  
|類型程式庫|ATL.dll|  
|C++|atliface.h （也包含在 ATLBase.h）|  
  
##  <a name="a-namegetallowcontextmenua--iaxwinambientdispatchgetallowcontextmenu"></a><a name="get_allowcontextmenu"></a>IAxWinAmbientDispatch::get_AllowContextMenu  
 **AllowContextMenu**屬性會指定是否允許裝載的控制項顯示快顯功能表。  
  
```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```  
  
### <a name="parameters"></a>參數  
 *pbAllowContextMenu*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作`VARIANT_TRUE`做為預設值，這個屬性。  
  
##  <a name="a-namegetallowshowuia--iaxwinambientdispatchgetallowshowui"></a><a name="get_allowshowui"></a>IAxWinAmbientDispatch::get_AllowShowUI  
 **AllowShowUI**屬性會指定是否允許裝載的控制項顯示使用者介面。  
  
```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```  
  
### <a name="parameters"></a>參數  
 *pbAllowShowUI*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**VARIANT_FALSE**做為預設值，這個屬性。  
  
##  <a name="a-namegetallowwindowlessactivationa--iaxwinambientdispatchgetallowwindowlessactivation"></a><a name="get_allowwindowlessactivation"></a>IAxWinAmbientDispatch::get_AllowWindowlessActivation  
 **AllowWindowlessActivation**屬性中指定容器是否允許無視窗啟用。  
  
```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```  
  
### <a name="parameters"></a>參數  
 *pbAllowWindowless*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作`VARIANT_TRUE`做為預設值，這個屬性。  
  
##  <a name="a-namegetbackcolora--iaxwinambientdispatchgetbackcolor"></a><a name="get_backcolor"></a>IAxWinAmbientDispatch::get_BackColor  
 `BackColor`屬性會指定容器的環境背景色彩。  
  
```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```  
  
### <a name="parameters"></a>參數  
 *pclrBackground*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**COLOR_BTNFACE**或**COLOR_WINDOW**作為預設值，這個屬性 （取決於是否裝載視窗的父代為對話方塊）。  
  
##  <a name="a-namegetdisplayasdefaulta--iaxwinambientdispatchgetdisplayasdefault"></a><a name="get_displayasdefault"></a>IAxWinAmbientDispatch::get_DisplayAsDefault  
 **DisplayAsDefault**是環境的屬性，可讓控制項以瞭解其是否預設控制項。  
  
```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```  
  
### <a name="parameters"></a>參數  
 *pbDisplayAsDefault*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**VARIANT_FALSE**做為預設值，這個屬性。  
  
##  <a name="a-namegetdochostdoubleclickflagsa--iaxwinambientdispatchgetdochostdoubleclickflags"></a><a name="get_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::get_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags**屬性會指定應在回應按兩下作業。  
  
```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>參數  
 *pdwDocHostDoubleClickFlags*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**DOCHOSTUIDBLCLK_DEFAULT**做為預設值，這個屬性。  
  
##  <a name="a-namegetdochostflagsa--iaxwinambientdispatchgetdochostflags"></a><a name="get_dochostflags"></a>IAxWinAmbientDispatch::get_DocHostFlags  
 **DocHostFlags**屬性會指定主應用程式物件的使用者介面功能。  
  
```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```  
  
### <a name="parameters"></a>參數  
 *pdwDocHostFlags*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**DOCHOSTUIFLAG_NO3DBORDER**做為預設值，這個屬性。  
  
##  <a name="a-namegetfonta--iaxwinambientdispatchgetfont"></a><a name="get_font"></a>IAxWinAmbientDispatch::get_Font  
 **字型**屬性會指定容器的環境字型。  
  
```
STDMETHOD(get_Font)(IFontDisp** pFont);
```  
  
### <a name="parameters"></a>參數  
 `pFont`  
 [out]位址**IFontDisp**用來接收此屬性的目前值的介面指標。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 ATL 主應用程式物件實作會使用做為預設值，這個屬性的預設 GUI 字型或系統字型。  
  
##  <a name="a-namegetforecolora--iaxwinambientdispatchgetforecolor"></a><a name="get_forecolor"></a>IAxWinAmbientDispatch::get_ForeColor  
 `ForeColor`屬性會指定容器的環境前景色彩。  
  
```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```  
  
### <a name="parameters"></a>參數  
 *pclrForeground*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 ATL 主應用程式物件實作這個屬性的預設值為使用系統視窗文字色彩。  
  
##  <a name="a-namegetlocaleida--iaxwinambientdispatchgetlocaleid"></a><a name="get_localeid"></a>IAxWinAmbientDispatch::get_LocaleID  
 **LocaleID**屬性會指定容器的環境的地區設定識別碼。  
  
```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```  
  
### <a name="parameters"></a>參數  
 *plcidLocaleID*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 ATL 主應用程式物件實作這個屬性的預設值為使用使用者的預設地區設定。  
  
 您可以使用這個方法來探索環境 LocalID，也就是程式的地區設定識別碼控制項使用中。 一旦您知道地區設定識別碼，您可以從資源檔或附屬 DLL 等等呼叫的程式碼載入特定地區設定標題，錯誤訊息文字。  
  
##  <a name="a-namegetmessagereflecta--iaxwinambientdispatchgetmessagereflect"></a><a name="get_messagereflect"></a>IAxWinAmbientDispatch::get_MessageReflect  
 **MessageReflect**環境屬性會指定容器是否會反映在裝載控制項的訊息。  
  
```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```  
  
### <a name="parameters"></a>參數  
 *pbMessageReflect*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作`VARIANT_TRUE`做為預設值，這個屬性。  
  
##  <a name="a-namegetoptionkeypatha--iaxwinambientdispatchgetoptionkeypath"></a><a name="get_optionkeypath"></a>IAxWinAmbientDispatch::get_OptionKeyPath  
 **OptionKeyPath**屬性會指定使用者設定登錄機碼路徑。  
  
```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```  
  
### <a name="parameters"></a>參數  
 *pbstrOptionKeyPath*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="a-namegetshowgrabhandlesa--iaxwinambientdispatchgetshowgrabhandles"></a><a name="get_showgrabhandles"></a>IAxWinAmbientDispatch::get_ShowGrabHandles  
 **ShowGrabHandles**環境屬性可以讓要了解是否它本身應該具有抓取控點來繪製的控制項。  
  
```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```  
  
### <a name="parameters"></a>參數  
 *pbShowGrabHandles*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 ATL 主機物件實作一律會傳回**VARIANT_FALSE**做為這個屬性的值。  
  
##  <a name="a-namegetshowhatchinga--iaxwinambientdispatchgetshowhatching"></a><a name="get_showhatching"></a>IAxWinAmbientDispatch::get_ShowHatching  
 **ShowHatching**環境屬性可以讓控制項以找出是否它應該繪製本身影線。  
  
```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```  
  
### <a name="parameters"></a>參數  
 *pbShowHatching*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 ATL 主機物件實作一律會傳回**VARIANT_FALSE**做為這個屬性的值。  
  
##  <a name="a-namegetusermodea--iaxwinambientdispatchgetusermode"></a><a name="get_usermode"></a>IAxWinAmbientDispatch::get_UserMode  
 **UserMode**屬性會指定容器的環境的使用者模式。  
  
```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```  
  
### <a name="parameters"></a>參數  
 *pbUserMode*  
 [out]若要接收此屬性的目前值變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作`VARIANT_TRUE`做為預設值，這個屬性。  
  
##  <a name="a-nameputallowcontextmenua--iaxwinambientdispatchputallowcontextmenu"></a><a name="put_allowcontextmenu"></a>IAxWinAmbientDispatch::put_AllowContextMenu  
 **AllowContextMenu**屬性會指定是否允許裝載的控制項顯示快顯功能表。  
  
```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```  
  
### <a name="parameters"></a>參數  
 *bAllowContextMenu*  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作`VARIANT_TRUE`做為預設值，這個屬性。  
  
##  <a name="a-nameputallowshowuia--iaxwinambientdispatchputallowshowui"></a><a name="put_allowshowui"></a>IAxWinAmbientDispatch::put_AllowShowUI  
 **AllowShowUI**屬性會指定是否允許裝載的控制項顯示使用者介面。  
  
```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```  
  
### <a name="parameters"></a>參數  
 *bAllowShowUI*  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**VARIANT_FALSE**做為預設值，這個屬性。  
  
##  <a name="a-nameputallowwindowlessactivationa--iaxwinambientdispatchputallowwindowlessactivation"></a><a name="put_allowwindowlessactivation"></a>IAxWinAmbientDispatch::put_AllowWindowlessActivation  
 **AllowWindowlessActivation**屬性中指定容器是否允許無視窗啟用。  
  
```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```  
  
### <a name="parameters"></a>參數  
 *bAllowWindowless*  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作`VARIANT_TRUE`做為預設值，這個屬性。  
  
##  <a name="a-nameputbackcolora--iaxwinambientdispatchputbackcolor"></a><a name="put_backcolor"></a>IAxWinAmbientDispatch::put_BackColor  
 `BackColor`屬性會指定容器的環境背景色彩。  
  
```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```  
  
### <a name="parameters"></a>參數  
 *clrBackground*  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**COLOR_BTNFACE**或**COLOR_WINDOW**作為預設值，這個屬性 （取決於是否裝載視窗的父代為對話方塊）。  
  
##  <a name="a-nameputdisplayasdefaulta--iaxwinambientdispatchputdisplayasdefault"></a><a name="put_displayasdefault"></a>IAxWinAmbientDispatch::put_DisplayAsDefault  
 **DisplayAsDefault**是環境的屬性，可讓控制項以瞭解其是否預設控制項。  
  
```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```  
  
### <a name="parameters"></a>參數  
 `bDisplayAsDefault`  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**VARIANT_FALSE**做為預設值，這個屬性。  
  
##  <a name="a-nameputdochostdoubleclickflagsa--iaxwinambientdispatchputdochostdoubleclickflags"></a><a name="put_dochostdoubleclickflags"></a>IAxWinAmbientDispatch::put_DocHostDoubleClickFlags  
 **DocHostDoubleClickFlags**屬性會指定應在回應按兩下作業。  
  
```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```  
  
### <a name="parameters"></a>參數  
 *dwDocHostDoubleClickFlags*  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**DOCHOSTUIDBLCLK_DEFAULT**做為預設值，這個屬性。  
  
##  <a name="a-nameputdochostflagsa--iaxwinambientdispatchputdochostflags"></a><a name="put_dochostflags"></a>IAxWinAmbientDispatch::put_DocHostFlags  
 **DocHostFlags**屬性會指定主應用程式物件的使用者介面功能。  
  
```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```  
  
### <a name="parameters"></a>參數  
 *dwDocHostFlags*  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作**DOCHOSTUIFLAG_NO3DBORDER**做為預設值，這個屬性。  
  
##  <a name="a-nameputfonta--iaxwinambientdispatchputfont"></a><a name="put_font"></a>IAxWinAmbientDispatch::put_Font  
 **字型**屬性會指定容器的環境字型。  
  
```
STDMETHOD(put_Font)(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>參數  
 `pFont`  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 ATL 主應用程式物件實作會使用做為預設值，這個屬性的預設 GUI 字型或系統字型。  
  
##  <a name="a-nameputforecolora--iaxwinambientdispatchputforecolor"></a><a name="put_forecolor"></a>IAxWinAmbientDispatch::put_ForeColor  
 `ForeColor`屬性會指定容器的環境前景色彩。  
  
```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```  
  
### <a name="parameters"></a>參數  
 *clrForeground*  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 ATL 主應用程式物件實作這個屬性的預設值為使用系統視窗文字色彩。  
  
##  <a name="a-nameputlocaleida--iaxwinambientdispatchputlocaleid"></a><a name="put_localeid"></a>IAxWinAmbientDispatch::put_LocaleID  
 **LocaleID**屬性會指定容器的環境的地區設定識別碼。  
  
```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```  
  
### <a name="parameters"></a>參數  
 *lcidLocaleID*  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 ATL 主應用程式物件實作這個屬性的預設值為使用使用者的預設地區設定。  
  
##  <a name="a-nameputmessagereflecta--iaxwinambientdispatchputmessagereflect"></a><a name="put_messagereflect"></a>IAxWinAmbientDispatch::put_MessageReflect  
 **MessageReflect**環境屬性會指定容器是否會反映在裝載控制項的訊息。  
  
```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```  
  
### <a name="parameters"></a>參數  
 `bMessageReflect`  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作`VARIANT_TRUE`做為預設值，這個屬性。  
  
##  <a name="a-nameputoptionkeypatha--iaxwinambientdispatchputoptionkeypath"></a><a name="put_optionkeypath"></a>IAxWinAmbientDispatch::put_OptionKeyPath  
 **OptionKeyPath**屬性會指定使用者設定登錄機碼路徑。  
  
```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```  
  
### <a name="parameters"></a>參數  
 *bstrOptionKeyPath*  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="a-nameputusermodea--iaxwinambientdispatchputusermode"></a><a name="put_usermode"></a>IAxWinAmbientDispatch::put_UserMode  
 **UserMode**屬性會指定容器的環境的使用者模式。  
  
```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```  
  
### <a name="parameters"></a>參數  
 `bUserMode`  
 [in]這個屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 使用 ATL 主應用程式物件實作`VARIANT_TRUE`做為預設值，這個屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IAxWinAmbientDispatchEx 介面](../../atl/reference/iaxwinambientdispatchex-interface.md)   
 [IAxWinHostWindow 介面](../../atl/reference/iaxwinhostwindow-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](http://msdn.microsoft.com/library/ad1f4f16-608d-4e96-8d30-04d4ca906a7b)










