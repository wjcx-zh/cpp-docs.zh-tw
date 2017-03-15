---
title: "CAxWindow2T 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAxWindow2T<TBase>
- ATL::CAxWindow2T
- CAxWindow2T
- ATL.CAxWindow2T<TBase>
- ATL.CAxWindow2T
- CAxWindow2
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
caps.latest.revision: 22
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
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: a0724b0ea8922d1f39d8cf7ccd630068c32ea3ac
ms.lasthandoff: 02/28/2017

---
# <a name="caxwindow2t-class"></a>CAxWindow2T 類別
這個類別提供方法來操作裝載 ActiveX 控制項，並也有支援裝載授權的 ActiveX 控制項的視窗。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```  
  
#### <a name="parameters"></a>參數  
 *TBase*  
 從中類別`CAxWindowT`衍生。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|建構 `CAxWindow2T` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAxWindow2T::Create](#create)|建立主應用程式視窗。|  
|[CAxWindow2T::CreateControlLic](#createcontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|  
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|建立授權的 ActiveX 控制項、 將它初始化、 它裝載於指定的視窗，並從控制項擷取介面指標 （或指標）。|  
|[CAxWindow2T::GetWndClassName](#getwndclassname)|擷取的視窗類別名稱的靜態方法。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAxWindow2T::operator =](#operator_eq)|指派`HWND`至現有`CAxWindow2T`物件。|  
  
## <a name="remarks"></a>備註  
 `CAxWindow2T`提供方法來管理視窗裝載 ActiveX 控制項。 `CAxWindow2T`也有授權的 ActiveX 控制項裝載支援。 裝載由 「 **AtlAxWinLic80**」，這會由包裝`CAxWindow2T`。  
  
 類別`CAxWindow2`實作為的特製化`CAxWindow2T`類別。 此特製化會宣告為︰  
  
 `typedef CAxWindow2T <CWindow> CAxWindow2;`  
  
> [!NOTE]
> `CAxWindowT`成員會記載在[CAxWindow](../../atl/reference/caxwindow-class.md)。  
  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需範例，會使用這個類別的成員。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `TBase`  
  
 `CAxWindowT`  
  
 `CAxWindow2T`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="a-namecaxwindow2ta--caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T  
 建構 `CAxWindow2T` 物件。  
  
```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 現有的視窗控制代碼。  
  
##  <a name="a-namecreatea--caxwindow2tcreate"></a><a name="create"></a>CAxWindow2T::Create  
 建立主應用程式視窗。  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="remarks"></a>備註  
 `CAxWindow2T::Create`呼叫[CWindow::Create](../../atl/reference/cwindow-class.md#create)與`LPCTSTR lpstrWndClass`參數設定為提供裝載控制項的視窗類別 ( **AtlAxWinLic80**)。  
  
 請參閱`CWindow::Create`參數和傳回值的說明。  
  
 **請注意**如果會使用 0 做為值`MenuOrID`參數，它必須指定為 0U （預設值） 以避免編譯器錯誤。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用範例`CAxWindow2T::Create`。  
  
##  <a name="a-namecreatecontrollica--caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a>CAxWindow2T::CreateControlLic  
 建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。  
  
```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```  
  
### <a name="parameters"></a>參數  
 `bstrLicKey`  
 授權金鑰控制項;如果建立要在未經授權的控制項，則為 NULL。  
  
### <a name="remarks"></a>備註  
 請參閱[CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol)其餘參數和傳回值的說明。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用範例`CAxWindow2T::CreateControlLic`。  
  
##  <a name="a-namecreatecontrollicexa--caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx  
 建立授權的 ActiveX 控制項、 將它初始化、 它裝載於指定的視窗，並從控制項擷取介面指標 （或指標）。  
  
```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```  
  
### <a name="parameters"></a>參數  
 `bstrLicKey`  
 授權金鑰控制項;如果建立要在未經授權的控制項，則為 NULL。  
  
### <a name="remarks"></a>備註  
 請參閱[CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex)其餘參數和傳回值的說明。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用範例`CAxWindow2T::CreateControlLicEx`。  
  
##  <a name="a-namegetwndclassnamea--caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow2T::GetWndClassName  
 擷取的視窗類別名稱。  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含視窗類別名稱的指標 ( **AtlAxWinLic80**) 可裝載授權和要在未經授權的 ActiveX 控制項。  
  
##  <a name="a-nameoperatoreqa--caxwindow2toperator-"></a><a name="operator_eq"></a>CAxWindow2T::operator =  
 指派`HWND`至現有`CAxWindow2T`物件。  
  
```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 現有的視窗控制代碼。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)

