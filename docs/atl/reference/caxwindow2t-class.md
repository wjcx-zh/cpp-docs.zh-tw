---
title: "CAxWindow2T 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
dev_langs: C++
helpviewer_keywords: CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12b7c8c66a092a92ef7fce25ce283f5145d9f910
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="caxwindow2t-class"></a>CAxWindow2T 類別
這個類別會提供方法來操作裝載 ActiveX 控制項，而且具有支援裝載已授權的 ActiveX 控制項的視窗。  
  
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
 從中的類別`CAxWindowT`衍生。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|建構 `CAxWindow2T` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAxWindow2T::Create](#create)|建立主機視窗。|  
|[CAxWindow2T::CreateControlLic](#createcontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|  
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|建立授權的 ActiveX 控制項、 將它初始化、 裝載於指定的視窗，並從控制項擷取介面指標 （或指標）。|  
|[CAxWindow2T::GetWndClassName](#getwndclassname)|靜態方法，擷取的視窗類別名稱。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAxWindow2T::operator =](#operator_eq)|指派`HWND`至現有`CAxWindow2T`物件。|  
  
## <a name="remarks"></a>備註  
 `CAxWindow2T`提供方法來管理視窗裝載 ActiveX 控制項。 `CAxWindow2T`也有支援裝載已授權的 ActiveX 控制項。 裝載由" **AtlAxWinLic80**"，其中包裝`CAxWindow2T`。  
  
 類別`CAxWindow2`實作為的特製化`CAxWindow2T`類別。 此特製化宣告為：  
  
 `typedef CAxWindow2T <CWindow> CAxWindow2;`  
  
> [!NOTE]
> `CAxWindowT`成員會記載在[CAxWindow](../../atl/reference/caxwindow-class.md)。  
  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)的範例會使用這個類別的成員。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `TBase`  
  
 `CAxWindowT`  
  
 `CAxWindow2T`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T  
 建構 `CAxWindow2T` 物件。  
  
```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 現有的視窗控制代碼。  
  
##  <a name="create"></a>CAxWindow2T::Create  
 建立主機視窗。  
  
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
  
 **請注意**如果 0 的值當做使用`MenuOrID`參數，它必須指定為 0U （預設值） 若要避免編譯器錯誤。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如使用的範例`CAxWindow2T::Create`。  
  
##  <a name="createcontrollic"></a>CAxWindow2T::CreateControlLic  
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
 授權金鑰，用於控制;如果建立要在未經授權的控制項，則為 NULL。  
  
### <a name="remarks"></a>備註  
 請參閱[CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol)其餘的參數和傳回值的說明。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如使用的範例`CAxWindow2T::CreateControlLic`。  
  
##  <a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx  
 建立授權的 ActiveX 控制項、 將它初始化、 裝載於指定的視窗，並從控制項擷取介面指標 （或指標）。  
  
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
 授權金鑰，用於控制;如果建立要在未經授權的控制項，則為 NULL。  
  
### <a name="remarks"></a>備註  
 請參閱[CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex)其餘的參數和傳回值的說明。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如使用的範例`CAxWindow2T::CreateControlLicEx`。  
  
##  <a name="getwndclassname"></a>CAxWindow2T::GetWndClassName  
 擷取視窗類別名稱。  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含視窗類別名稱的指標 ( **AtlAxWinLic80**)，可裝載授權和要在未經授權的 ActiveX 控制項。  
  
##  <a name="operator_eq"></a>CAxWindow2T::operator =  
 指派`HWND`至現有`CAxWindow2T`物件。  
  
```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 現有的視窗控制代碼。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)
