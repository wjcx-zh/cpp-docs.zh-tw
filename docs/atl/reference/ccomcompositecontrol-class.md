---
title: "CComCompositeControl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
dev_langs:
- C++
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
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
ms.openlocfilehash: ab99b8682e8b529cc124fbda1e6facaac48d0927
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl 類別
這個類別會提供實作複合控制項所需的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要為您的複合控制項支援從任何其他介面。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|建構函式。|  
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|呼叫此方法以通知或取消通知複合控制項所裝載的所有控制項。|  
|[CComCompositeControl::CalcExtent](#calcextent)|呼叫這個方法來計算的大小以**HIMETRIC**單位用來裝載複合控制項的對話方塊資源。|  
|[CComCompositeControl::Create](#create)|您可以呼叫這個方法建立複合控制項的控制項視窗。|  
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|呼叫這個方法來建立控制項的視窗，並建議任何裝載的控制項。|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|呼叫這個方法來設定使用容器的背景色彩的複合控制項的背景色彩。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|背景筆刷。|  
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|目前具有焦點的視窗控制代碼。|  
  
## <a name="remarks"></a>備註  
 類別衍生自類別`CComCompositeControl`繼承 ActiveX 複合控制項的功能。 ActiveX 控制項衍生自`CComCompositeControl`所裝載的標準對話方塊。 這類控制項稱為複合控制項，因為它們是能夠裝載其他控制項 （原生的 Windows 控制項和 ActiveX 控制項）。  
  
 `CComCompositeControl`識別用來尋找列舉中的資料成員的子類別會建立複合控制項的對話方塊資源。 成員 IDD 這個子類別設定為將做為控制項的視窗對話方塊資源的資源識別碼。 下列是範例資料成員的類別衍生自`CComCompositeControl`來識別要用於控制項的視窗對話方塊資源應該包含︰  
  
 [!code-cpp[NVC_ATL_COM&#13;](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  複合控制項一定是視窗型控制項，不過它們可以包含無視窗控制項。  
  
 所實作的控制項`CComCompositeControl`-衍生的類別有預設內建行為按下 tab 鍵。 當控制項收到焦點時所包含的應用程式中的定位時，接著按下 TAB 鍵將會導致焦點循環所有複合控制項包含的控制項，然後從複合控制項，再流向容器的定位順序中的下一個項目。 裝載控制項的定位順序由對話方塊資源，並決定的順序在哪一個按下 tab 鍵將會發生。  
  
> [!NOTE]
>  為了適當地使用加速器`CComCompositeControl`，就必須建立控制項時載入快速鍵對應表，並將控制代碼和數目的加速器回傳遞[IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)，和最後發行控制項時，終結資料表。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM&#14;](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap  
 呼叫此方法以通知或取消通知複合控制項所裝載的所有控制項。  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>參數  
 `bAdvise`  
 如果所有控制項都是要提醒您，則為 true否則為 false。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`  
 所有控制事件接收對應已連接或已成功中斷其事件來源。  
  
 **E_FAIL**  
 並非所有控制項無法連線或中斷其事件來源已順利接收對應。  
  
 `E_POINTER`  
 此錯誤通常表示控制項的事件接收對應中的項目有問題或樣板引數中使用問題`IDispEventImpl`或`IDispEventSimpleImpl`基底類別。  
  
 **CONNECT_E_ADVISELIMIT**  
 已達到其限制的連線和無法接受更多的連線點。  
  
 **CONNECT_E_CANNOTCONNECT**  
 接收不支援此連接點所需的介面。  
  
 **CONNECT_E_NOCONNECTION**  
 Cookie 值不代表有效的連接。 此錯誤通常表示控制項的事件接收對應中的項目有問題或樣板引數中使用問題`IDispEventImpl`或`IDispEventSimpleImpl`基底類別。  
  
### <a name="remarks"></a>備註  
 這個方法的基底實作會搜尋項目，在事件接收對應。 然後，它會建議或取消通知事件接收對應接收項目所描述之 COM 物件的連接點。 這個成員的方法也會依賴衍生的類別繼承自一個執行個體的事實`IDispEventImpl`為建議使用或 unadvised 接收對應中的每一個控制項。  
  
##  <a name="calcextent"></a>CComCompositeControl::CalcExtent  
 呼叫這個方法來計算的大小以**HIMETRIC**單位用來裝載複合控制項的對話方塊資源。  
  
```
BOOL CalcExtent(SIZE& size);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 參考**大小**結構，這個方法會填滿。  
  
### <a name="return-value"></a>傳回值  
 如果控制項裝載在對話方塊中，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 在傳回的大小`size`參數。  
  
##  <a name="create"></a>CComCompositeControl::Create  
 您可以呼叫這個方法建立複合控制項的控制項視窗。  
  
```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 控制項的父視窗控制代碼。  
  
 `rcPos`  
 保留的。  
  
 `dwInitParam`  
 在建立控制項期間傳遞給控制項的資料。 資料會當做`dwInitParam`會顯示為**LPARAM**參數[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)訊息，取得在建立時將會傳送至複合控制項。  
  
### <a name="return-value"></a>傳回值  
 新建立的複合控制項 對話方塊的控制代碼。  
  
### <a name="remarks"></a>備註  
 這個方法通常會呼叫控制項的就地啟用期間。  
  
##  <a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl  
 建構函式。  
  
```
CComCompositeControl();
```  
  
### <a name="remarks"></a>備註  
 初始化[CComCompositeControl::m_hbrBackground](#m_hbrbackground)和[CComCompositeControl::m_hWndFocus](#m_hwndfocus)為 NULL 的資料成員。  
  
##  <a name="dtor"></a>CComCompositeControl:: ~ CComCompositeControl  
 解構函式。  
  
```
~CComCompositeControl();
```  
  
### <a name="remarks"></a>備註  
 如果存在的話，請刪除背景物件。  
  
##  <a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow  
 呼叫這個方法來建立控制項的視窗，並建議任何裝載的控制項。  
  
```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 控制項的父視窗控制代碼。  
  
 `rcPos`  
 複合控制項在用戶端的位置矩形座標相對於`hWndParent`。  
  
### <a name="return-value"></a>傳回值  
 傳回新建立的複合控制項 對話方塊的控制代碼。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CComCompositeControl::Create](#create)和[CComCompositeControl::AdviseSinkMap](#advisesinkmap)。  
  
##  <a name="m_hbrbackground"></a>CComCompositeControl::m_hbrBackground  
 背景筆刷。  
  
```
HBRUSH m_hbrBackground;
```  
  
##  <a name="m_hwndfocus"></a>CComCompositeControl::m_hWndFocus  
 目前具有焦點的視窗控制代碼。  
  
```
HWND m_hWndFocus;
```  
  
##  <a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient  
 呼叫這個方法來設定使用容器的背景色彩的複合控制項的背景色彩。  
  
```
HRESULT SetBackgroundColorFromAmbient();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)   
 [類別概觀](../../atl/atl-class-overview.md)

