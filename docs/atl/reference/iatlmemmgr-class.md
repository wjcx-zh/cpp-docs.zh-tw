---
title: "IAtlMemMgr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAtlMemMgr
dev_langs:
- C++
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8e63d6dd9197aa3b81f893c58a1c8e41dfe2cc1b
ms.lasthandoff: 02/24/2017

---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr 類別
此類別代表記憶體管理員介面。  
  
## <a name="syntax"></a>語法  
  
```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[配置](#allocate)|呼叫這個方法來配置記憶體區塊。|  
|[免費](#free)|呼叫此方法以釋放記憶體區塊。|  
|[GetSize](#getsize)|呼叫這個方法來擷取配置的記憶體區塊大小。|  
|[重新配置](#reallocate)|呼叫這個方法來重新配置的記憶體區塊。|  
  
## <a name="remarks"></a>備註  
 這個介面由實作[CComHeap](../../atl/reference/ccomheap-class.md)， [CCRTHeap](../../atl/reference/ccrtheap-class.md)， [CLocalHeap](../../atl/reference/clocalheap-class.md)， [CGlobalHeap](../../atl/reference/cglobalheap-class.md)，或[CWin32Heap](../../atl/reference/cwin32heap-class.md)。  
  
> [!NOTE]
>  本機和全域堆積函式低於其他記憶體管理函式，但並未提供最多的功能。 因此，新的應用程式應該使用[堆積函式](http://msdn.microsoft.com/library/windows/desktop/aa366711)。 這些是用於[CWin32Heap](../../atl/reference/cwin32heap-class.md)類別。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&94;](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlmem.h  
  
##  <a name="a-nameallocatea--iatlmemmgrallocate"></a><a name="allocate"></a>IAtlMemMgr::Allocate  
 呼叫這個方法來配置記憶體區塊。  
  
```
void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBytes`  
 在新記憶體區塊中要求的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫[IAtlMemMgr::Free](#free)或[IAtlMemMgr::Reallocate](#reallocate)釋放透過這個方法配置的記憶體。  
  
### <a name="example"></a>範例  
 如需範例，請參閱[IAtlMemMgr 概觀](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="a-namefreea--iatlmemmgrfree"></a><a name="free"></a>IAtlMemMgr::Free  
 呼叫此方法以釋放記憶體區塊。  
  
```
void Free(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 此記憶體管理員先前所配置之記憶體的指標。  
  
### <a name="remarks"></a>備註  
 使用此方法來釋放所佔用的記憶體[IAtlMemMgr::Allocate](#allocate)或[IAtlMemMgr::Reallocate](#reallocate)。  
  
### <a name="example"></a>範例  
 如需範例，請參閱[IAtlMemMgr 概觀](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="a-namegetsizea--iatlmemmgrgetsize"></a><a name="getsize"></a>IAtlMemMgr::GetSize  
 呼叫這個方法來擷取配置的記憶體區塊大小。  
  
```
size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 此記憶體管理員先前所配置之記憶體的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回記憶體區塊的大小，以位元組為單位。  
  
### <a name="example"></a>範例  
 如需範例，請參閱[IAtlMemMgr 概觀](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="a-namereallocatea--iatlmemmgrreallocate"></a><a name="reallocate"></a>IAtlMemMgr::Reallocate  
 呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。  
  
```
void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 此記憶體管理員先前所配置之記憶體的指標。  
  
 `nBytes`  
 在新記憶體區塊中要求的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫[IAtlMemMgr::Free](#free)或[IAtlMemMgr::Reallocate](#reallocate)釋放透過這個方法配置的記憶體。  
  
 在概念上這個方法會釋放現有的記憶體，並會配置新的記憶體區塊。 事實上，可能會擴充或否則重複使用現有的記憶體。  
  
### <a name="example"></a>範例  
 如需範例，請參閱[IAtlMemMgr 概觀](../../atl/reference/iatlmemmgr-class.md)。  
  
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
  
##  <a name="a-namesetambientdispatcha--iaxwinambientdispatchexsetambientdispatch"></a><a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch  
 呼叫這個方法是以補充預設環境屬性的介面與使用者定義的介面。  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>參數  
 *pDispatch*  
 新的介面指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 當`SetAmbientDispatch`稱為的新介面的指標，這個新介面將用來叫用任何屬性或方法要求輸入裝載控制項 — 如果這些屬性所未提供的[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)。  
  
##  <a name="a-nameattachcontrola--iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHostWindow::AttachControl  
 將現有的 （與先前初始化的） 控制項加入至使用視窗所識別的主物件`hWnd`。  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 *pUnkControl*  
 [in]指標**IUnknown**控制項連接至主應用程式物件的介面。  
  
 `hWnd`  
 [in]若要用來裝載視窗的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="a-namecreatecontrola--iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHostWindow::CreateControl  
 建立控制項、 將它初始化，以及裝載於所識別的視窗`hWnd`。  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>參數  
 `lpTricsData`  
 [in]字串，識別要建立的控制項。 可以是的 CLSID （必須包含在大括號）、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。  
  
 `hWnd`  
 [in]若要用來裝載視窗的控制代碼。  
  
 `pStream`  
 [in]包含控制項的初始化資料的資料流的介面指標。 可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 這個視窗會公開這個介面，以讓訊息可以反映至控制項和其他容器功能，將會使用主應用程式物件的子類別化。  
  
 呼叫這個方法就相當於呼叫[IAxWinHostWindow::CreateControlEx](#createcontrolex)。  
  
 若要建立授權的 ActiveX 控制項，請參閱[IAxWinHostWindowLic::CreateControlLic](#createcontrollicex)。  
  
##  <a name="a-namecreatecontrolexa--iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx  
 建立 ActiveX 控制項、 將它初始化，以及裝載於指定的視窗，類似於[IAxWinHostWindow::CreateControl](#createcontrol)。  
  
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
 `lpTricsData`  
 [in]字串，識別要建立的控制項。 可以是的 CLSID （必須包含在大括號）、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。  
  
 `hWnd`  
 [in]若要用來裝載視窗的控制代碼。  
  
 `pStream`  
 [in]包含控制項的初始化資料的資料流的介面指標。 可以是**NULL**。  
  
 `ppUnk`  
 [out]將會收到的指標位址**IUnknown**介面建立的控制項。 可以是**NULL**。  
  
 *riidAdvise*  
 [in]所包含的物件上的輸出介面的介面識別項。 可以是**IID_NULL**。  
  
 *punkAdvise*  
 [in]指標**IUnknown**介面連線到所指定的包含物件的連接點的接收器物件`iidSink`。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 不同於`CreateControl`方法，`CreateControlEx`也可讓您接收新建立的控制項的介面指標，並將事件接收器設定為接收控制項引發的事件。  
  
 若要建立授權的 ActiveX 控制項，請參閱[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)。  
  
##  <a name="a-namequerycontrola--iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHostWindow::QueryControl  
 傳回所裝載的控制項提供指定的介面指標。  
  
```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `riid`  
 [in]所要求的控制項上的介面識別碼。  
  
 `ppvObject`  
 [out]將會收到建立控制項的指定的介面的指標位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="a-namesetexternaldispatcha--iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch  
 設定外部的分配介面，可用於包含的控制項，透過[IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md)方法。  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>參數  
 `pDisp`  
 [in]指標`IDispatch`介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="a-namesetexternaluihandlera--iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler  
 呼叫此函式來設定外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)介面`CAxWindow`物件。  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>參數  
 `pDisp`  
 [in]指標**IDocHostUIHandlerDispatch**介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 查詢主應用程式網站的控制項 （例如 Web 瀏覽器控制項） 會使用此函式`IDocHostUIHandlerDispatch`介面。  
  
##  <a name="a-namecreatecontrollica--iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic  
 建立授權的控制項、 將它初始化，以及裝載於所識別的視窗`hWnd`。  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>參數  
 `bstrLic`  
 [in]包含控制項的授權金鑰 BSTR。  
  
### <a name="remarks"></a>備註  
 請參閱[IAxWinHostWindow::CreateControl](#createcontrol)其餘參數和傳回值的說明。  
  
 呼叫這個方法就相當於呼叫[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用範例`IAxWinHostWindowLic::CreateControlLic`。  
  
##  <a name="a-namecreatecontrollicexa--iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx  
 建立授權的 ActiveX 控制項、 將它初始化，以及裝載於指定的視窗，類似於[IAxWinHostWindow::CreateControl](#createcontrol)。  
  
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
 `bstrLic`  
 [in]包含控制項的授權金鑰 BSTR。  
  
### <a name="remarks"></a>備註  
 請參閱[IAxWinHostWindow::CreateControlEx](#createcontrolex)其餘參數和傳回值的說明。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用範例`IAxWinHostWindowLic::CreateControlLicEx`。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

