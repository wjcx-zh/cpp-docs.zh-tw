---
title: IAtlMemMgr 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAtlMemMgr
- ATLMEM/ATL::IAtlMemMgr
- ATLMEM/ATL::Allocate
- ATLMEM/ATL::Free
- ATLMEM/ATL::GetSize
- ATLMEM/ATL::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- IAtlMemMgr class
- memory, managing
- memory, memory manager
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d623df9fcab776a42fda7ca13269554b9f38b56c
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880569"
---
# <a name="iatlmemmgr-class"></a>IAtlMemMgr 類別
此類別代表記憶體管理員介面。  
  
## <a name="syntax"></a>語法  
  
```
__interface __declspec(uuid("654F7EF5-CFDF-4df9-A450-6C6A13C622C0")) IAtlMemMgr
```  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[配置](#allocate)|呼叫這個方法來配置記憶體區塊。|  
|[免費](#free)|呼叫此方法來釋放記憶體區塊。|  
|[GetSize](#getsize)|呼叫這個方法來擷取已配置的記憶體區塊的大小。|  
|[重新配置](#reallocate)|呼叫這個方法來重新配置的記憶體區塊。|  
  
## <a name="remarks"></a>備註  
 此介面由實作[CComHeap](../../atl/reference/ccomheap-class.md)， [CCRTHeap](../../atl/reference/ccrtheap-class.md)， [CLocalHeap](../../atl/reference/clocalheap-class.md)， [CGlobalHeap](../../atl/reference/cglobalheap-class.md)，或[CWin32Heap](../../atl/reference/cwin32heap-class.md).  
  
> [!NOTE]
>  本機和全域堆積函式低於其他記憶體管理函式，並不會提供許多功能。 因此，應該使用新的應用程式[堆積函式](http://msdn.microsoft.com/library/windows/desktop/aa366711)。 中會有這些[CWin32Heap](../../atl/reference/cwin32heap-class.md)類別。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/cpp/iatlmemmgr-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** atlmem.h  
  
##  <a name="allocate"></a>  IAtlMemMgr::Allocate  
 呼叫這個方法來配置記憶體區塊。  
  
```
void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 *nBytes*  
 在新記憶體區塊中要求的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫[IAtlMemMgr::Free](#free)或是[IAtlMemMgr::Reallocate](#reallocate)釋放這個方法所配置的記憶體。  
  
### <a name="example"></a>範例  
 如需範例，請參閱[IAtlMemMgr 概觀](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="free"></a>  IAtlMemMgr::Free  
 呼叫此方法來釋放記憶體區塊。  
  
```
void Free(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 *p*  
 此記憶體管理員先前所配置之記憶體的指標。  
  
### <a name="remarks"></a>備註  
 使用這個方法來釋放所佔用的記憶體[IAtlMemMgr::Allocate](#allocate)或是[IAtlMemMgr::Reallocate](#reallocate)。  
  
### <a name="example"></a>範例  
 如需範例，請參閱[IAtlMemMgr 概觀](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="getsize"></a>  IAtlMemMgr::GetSize  
 呼叫這個方法來擷取已配置的記憶體區塊的大小。  
  
```
size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 *p*  
 此記憶體管理員先前所配置之記憶體的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回以位元組為單位的記憶體區塊的大小。  
  
### <a name="example"></a>範例  
 如需範例，請參閱[IAtlMemMgr 概觀](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="reallocate"></a>  IAtlMemMgr::Reallocate  
 呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。  
  
```
void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 *p*  
 此記憶體管理員先前所配置之記憶體的指標。  
  
 *nBytes*  
 在新記憶體區塊中要求的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫[IAtlMemMgr::Free](#free)或是[IAtlMemMgr::Reallocate](#reallocate)釋放這個方法所配置的記憶體。  
  
 在概念上這個方法會釋放現有的記憶體，並且配置新的記憶體區塊。 事實上，可能會擴充或否則重複使用現有的記憶體。  
  
### <a name="example"></a>範例  
 如需範例，請參閱[IAtlMemMgr 概觀](../../atl/reference/iatlmemmgr-class.md)。  
  
##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu  
 `AllowContextMenu`屬性會指定是否允許裝載的控制項顯示內容功能表。  
  
```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```  
  
### <a name="parameters"></a>參數  
 *pbAllowContextMenu*  
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
 *pbAllowShowUI*  
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
 *pbAllowWindowless*  
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
 *pclrBackground*  
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
 *pbDisplayAsDefault*  
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
 *pdwDocHostDoubleClickFlags*  
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
 *pdwDocHostFlags*  
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
 *pFont*  
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
 *pclrForeground*  
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
 *plcidLocaleID*  
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
 *pbMessageReflect*  
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
 *pbstrOptionKeyPath*  
 [out]要接收此屬性的目前值之變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles  
 `ShowGrabHandles`環境屬性可讓您控制，若要了解是否它應該繪製本身的抓取控點。  
  
```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```  
  
### <a name="parameters"></a>參數  
 *pbShowGrabHandles*  
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
 *pbShowHatching*  
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
 *pbUserMode*  
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
 *bAllowContextMenu*  
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
 *bAllowShowUI*  
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
 *bAllowWindowless*  
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
 *clrBackground*  
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
 *bDisplayAsDefault*  
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
 *dwDocHostDoubleClickFlags*  
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
 *dwDocHostFlags*  
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
 *pFont*  
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
 *clrForeground*  
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
 *lcidLocaleID*  
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
 *bMessageReflect*  
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
 *bstrOptionKeyPath*  
 [in]此屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode  
 `UserMode`屬性會指定容器的環境的使用者模式。  
  
```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```  
  
### <a name="parameters"></a>參數  
 *bUserMode*  
 [in]此屬性的新值。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 ATL 主機物件實作會使用這個屬性的預設值為 VARIANT_TRUE。  
  
##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch  
 會呼叫這個方法，來補充預設環境屬性介面與使用者定義的介面。  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>參數  
 *pDispatch*  
 新的介面指標。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 當`SetAmbientDispatch`稱為與新的介面的指標，這個新介面將用來叫用的任何屬性或方法所裝載的控制項要求 — 如果這些屬性所未提供的[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl  
 將現有的 （與先前初始化的） 的控制項附加至使用視窗所識別的主物件*hWnd*。  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 *pUnkControl*  
 [in]指標`IUnknown`要附加至主機的物件之控制項的介面。  
  
 *hWnd*  
 [in]要用來裝載之視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl  
 建立控制項，它初始化，並將它裝載在視窗中所識別*hWnd*。  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>參數  
 *lpTricsData*  
 [in]字串，識別要建立的控制項。 可以是 （必須包含在大括號） 的 CLSID、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。  
  
 *hWnd*  
 [in]要用來裝載之視窗控制代碼。  
  
 *pStream*  
 [in]包含控制項的初始化資料的資料流介面指標。 可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 此視窗會公開這個介面，讓訊息可以反映至控制項和其他容器功能將可運作的主機物件的子類別化。  
  
 呼叫這個方法就相當於呼叫[IAxWinHostWindow::CreateControlEx](#createcontrolex)。  
  
 若要建立授權的 ActiveX 控制項，請參閱[IAxWinHostWindowLic::CreateControlLic](#createcontrollicex)。  
  
##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx  
 建立 ActiveX 控制項，它初始化，並將它裝載於指定的視窗，類似於[IAxWinHostWindow::CreateControl](#createcontrol)。  
  
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
 *lpTricsData*  
 [in]字串，識別要建立的控制項。 可以是 （必須包含在大括號） 的 CLSID、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。  
  
 *hWnd*  
 [in]要用來裝載之視窗控制代碼。  
  
 *pStream*  
 [in]包含控制項的初始化資料的資料流介面指標。 可以是 NULL。  
  
 *ppUnk*  
 [out]將會收到的指標位址`IUnknown`介面建立的控制項。 可以是 NULL。  
  
 *riidAdvise*  
 [in]在所包含的物件上的輸出介面的介面識別項。 可以是 IID_NULL。  
  
 *punkAdvise*  
 [in]指標`IUnknown`連接到包含的物件所指定的連接點的接收器物件的介面`iidSink`。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 不同於`CreateControl`方法，`CreateControlEx`也可讓您接收新建立之控制項的介面指標，並設定要接收控制項所引發的事件的事件接收。  
  
 若要建立授權的 ActiveX 控制項，請參閱[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)。  
  
##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl  
 傳回所裝載的控制項提供指定的介面指標。  
  
```
STDMETHOD(QueryControl)(REFIID riid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 *riid*  
 [in]所要求的控制項上的介面識別碼。  
  
 *ppvObject*  
 [out]將會收到建立控制項的指定的介面的指標位址。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch  
 設定外部 dispinterface，也就是可包含的控制項，透過[IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md)方法。  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>參數  
 *pDisp*  
 [in]指標`IDispatch`介面。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler  
 呼叫此函式來設定外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)介面`CAxWindow`物件。  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>參數  
 *pDisp*  
 [in]指標`IDocHostUIHandlerDispatch`介面。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 這個函數由控制項 （例如 Web 瀏覽器控制項），查詢主機的網站`IDocHostUIHandlerDispatch`介面。  
  
##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic  
 建立具有授權的控制項，它初始化，並將它裝載在視窗中所識別`hWnd`。  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>參數  
 *bstrLic*  
 [in]包含控制項的授權金鑰 BSTR。  
  
### <a name="remarks"></a>備註  
 請參閱[IAxWinHostWindow::CreateControl](#createcontrol)剩餘的參數和傳回值的說明。  
  
 呼叫這個方法就相當於呼叫[IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需範例，會使用`IAxWinHostWindowLic::CreateControlLic`。  
  
##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx  
 建立授權的 ActiveX 控制項，它初始化，並將它裝載於指定的視窗，類似於[IAxWinHostWindow::CreateControl](#createcontrol)。  
  
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
 *bstrLic*  
 [in]包含控制項的授權金鑰 BSTR。  
  
### <a name="remarks"></a>備註  
 請參閱[IAxWinHostWindow::CreateControlEx](#createcontrolex)剩餘的參數和傳回值的說明。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需範例，會使用`IAxWinHostWindowLic::CreateControlLicEx`。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
