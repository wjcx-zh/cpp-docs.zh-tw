---
title: "CDynamicChain 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
dev_langs:
- C++
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 54137760f2c1ee0f93fd8ad21238710f4b6a4a56
ms.contentlocale: zh-tw
ms.lasthandoff: 03/31/2017

---
# <a name="cdynamicchain-class"></a>CDynamicChain 類別
這個類別會提供支援動態鏈結的訊息對應的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CDynamicChain
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDynamicChain::CDynamicChain](#cdynamicchain)|建構函式。|  
|[CDynamicChain:: ~ CDynamicChain](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDynamicChain::CallChain](#callchain)|將導向至另一個物件的訊息對應 Windows 訊息。|  
|[CDynamicChain::RemoveChainEntry](#removechainentry)|從集合中移除訊息對應項目。|  
|[CDynamicChain::SetChainEntry](#setchainentry)|將訊息對應項目加入至集合，或修改現有的項目。|  
  
## <a name="remarks"></a>備註  
 `CDynamicChain`管理訊息對應，啟用 Windows 訊息導向，在執行階段，加入另一個物件的訊息對應的集合。  
  
 若要加入支援的訊息對應的動態鏈結，執行下列作業︰  
  
-   衍生您的類別從`CDynamicChain`。 在訊息對應中，指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)鏈結至另一個物件的預設訊息對應巨集。  
  
-   您想要從鏈結至每個的類別的衍生[CMessageMap](../../atl/reference/cmessagemap-class.md)。 `CMessageMap`讓物件公開至其他物件其訊息對應。  
  
-   呼叫`CDynamicChain::SetChainEntry`來識別物件和訊息對應您要鏈結。  
  
 例如，假設您的類別定義，如下所示︰  
  
 [!code-cpp[NVC_ATL_Windowing # 88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]  
  
 用戶端會接著呼叫`CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing # 89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]  
  
 其中`chainedObj`是鏈結的物件，而且是衍生自類別的執行個體`CMessageMap`。 現在，如果`myCtl`收到的訊息，不會處理`OnPaint`或`OnSetFocus`，視窗程序會指示訊息`chainedObj`的預設訊息對應。  
  
 如需訊息對應鏈結的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)本文 < ATL 視窗類別 >。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="callchain"></a>CDynamicChain::CallChain  
 Windows 會將訊息導向至另一個物件的訊息對應。  
  
```
BOOL CallChain(  
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```  
  
### <a name="parameters"></a>參數  
 `dwChainID`  
 [in]鏈結的物件和其訊息對應相關聯的唯一識別碼。  
  
 `hWnd`  
 [in]接收訊息的視窗控制代碼。  
  
 `uMsg`  
 [in]傳送至視窗的訊息。  
  
 `wParam`  
 [in]其他訊息的特定資訊。  
  
 `lParam`  
 [in]其他訊息的特定資訊。  
  
 `lResult`  
 [out]訊息處理的結果。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**訊息是否完全處理過，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 視窗程序來叫用`CallChain`，您必須指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)中訊息對應巨集。 如需範例，請參閱[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概觀。  
  
 `CallChain`需要先前呼叫[SetChainEntry](#setchainentry)關聯`dwChainID`物件和其訊息對應的值。  
  
##  <a name="cdynamicchain"></a>CDynamicChain::CDynamicChain  
 建構函式。  
  
```
CDynamicChain();
```  
  
##  <a name="dtor"></a>CDynamicChain:: ~ CDynamicChain  
 解構函式。  
  
```
~CDynamicChain();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="removechainentry"></a>CDynamicChain::RemoveChainEntry  
 從集合中移除指定的訊息對應。  
  
```
BOOL RemoveChainEntry(DWORD dwChainID);
```  
  
### <a name="parameters"></a>參數  
 `dwChainID`  
 [in]鏈結的物件和其訊息對應相關聯的唯一識別碼。 您原本定義此值，透過呼叫[SetChainEntry](#setchainentry)。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果從集合中成功移除的訊息對應。 否則， **FALSE**。  
  
##  <a name="setchainentry"></a>CDynamicChain::SetChainEntry  
 將指定的訊息對應新增至集合。  
  
```
BOOL SetChainEntry(  
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```  
  
### <a name="parameters"></a>參數  
 `dwChainID`  
 [in]鏈結的物件和其訊息對應相關聯的唯一識別碼。  
  
 `pObject`  
 [in]宣告的訊息對應鏈結物件的指標。 此物件必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
 `dwMsgMapID`  
 [in]訊息對應中的鍊結物件的識別碼。 預設值為 0，它會識別宣告的預設訊息對應[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)。 使用指定的替代訊息對應宣告[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，傳遞`msgMapID`。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果訊息對應成功加入至集合。 否則， **FALSE**。  
  
### <a name="remarks"></a>備註  
 如果`dwChainID`值已經存在集合中，其相關聯的物件和訊息對應會取代`pObject`和`dwMsgMapID`分別。 否則，會加入新項目。  
  
## <a name="see-also"></a>另請參閱  
 [CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

