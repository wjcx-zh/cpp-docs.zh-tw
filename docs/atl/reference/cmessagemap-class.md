---
title: "CMessageMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
dev_langs:
- C++
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 04aff6922358048fcbd330096eb26a412cdb75ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmessagemap-class"></a>CMessageMap 類別
這個類別可讓物件的訊息對應是由另一個物件的存取。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class ATL_NO_VTABLE CMessageMap
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|存取訊息對應中的`CMessageMap`-衍生的類別。|  
  
## <a name="remarks"></a>備註  
 `CMessageMap`是抽象的基底類別，可讓物件的訊息對應至另一個物件的存取。 為了讓公開其訊息對應的物件，其類別必須衍生自`CMessageMap`。  
  
 使用 ATL`CMessageMap`支援包含 windows 和動態的訊息對應鏈結。 例如，任何類別包含[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)物件必須衍生自`CMessageMap`。 下列程式碼取自[SUBEDIT](../../visual-cpp-samples.md)範例。 透過[CComControl](../../atl/reference/ccomcontrol-class.md)、`CAtlEdit`類別自動衍生自`CMessageMap`。  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]  
  
 因為自主的視窗中， `m_EditCtrl`，會使用訊息對應中包含的類別，`CAtlEdit`衍生自`CMessageMap`。  
  
 如需訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)本文 < ATL 視窗類別 >。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage  
 存取所識別的訊息對應`dwMsgMapID`中`CMessageMap`-衍生的類別。  
  
```
virtual BOOL ProcessWindowMessage(  
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```  
  
### <a name="parameters"></a>參數  
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
  
 `dwMsgMapID`  
 [in]會處理訊息的訊息對應的識別項。 預設的訊息對應，以宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，由 0。 使用替代的訊息對應宣告[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，由`msgMapID`。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果訊息已完整處理，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 由視窗程序的呼叫[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)物件或物件的以動態方式鏈結至訊息對應。  
  
## <a name="see-also"></a>請參閱  
 [CDynamicChain 類別](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [類別概觀](../../atl/atl-class-overview.md)
