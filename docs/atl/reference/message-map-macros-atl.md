---
title: "訊息對應巨集 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
dev_langs:
- C++
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 200d82c9d9b2ca0456ae5de4d6c937be69e212bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="message-map-macros-atl"></a>訊息對應巨集 (ATL)
這些巨集會定義訊息對應和項目。  
  
|||  
|-|-|  
|[ALT_MSG_MAP](#alt_msg_map)|標記替代訊息對應的開頭。|  
|[BEGIN_MSG_MAP](#begin_msg_map)|標記的預設訊息對應的開頭。|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|鏈結至替代的訊息對應中的基底類別。|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|鏈結至替代的訊息對應中的類別資料成員。|  
|[CHAIN_MSG_MAP](#chain_msg_map)|鏈結至預設的訊息對應中的基底類別。|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|若要在執行階段的另一個類別中的訊息對應的鏈結。|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|鏈結至預設的訊息對應中的類別資料成員。|  
|[COMMAND_CODE_HANDLER](#command_code_handler)|對應**WM_COMMAND**訊息處理常式函式，根據通知的程式碼。|  
|[COMMAND_HANDLER](#command_handler)|對應**WM_COMMAND**訊息處理常式函式，根據通知的程式碼和功能表項目、 控制項或快速鍵的識別項。|  
|[COMMAND_ID_HANDLER](#command_id_handler)|對應**WM_COMMAND**訊息處理常式函式，根據功能表項目、 控制項或快速鍵的識別項。|  
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|對應**WM_COMMAND**訊息處理常式函式，根據通知的程式碼和連續的控制項識別碼範圍。|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|對應**WM_COMMAND**訊息處理常式函式，根據連續控制識別項的範圍。|  
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|實作空白的訊息對應。|  
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|否則未處理反映訊息提供的預設處理常式。|  
|[END_MSG_MAP](#end_msg_map)|結束標記的訊息對應。|  
|[FORWARD_NOTIFICATIONS](#forward_notifications)|將轉送至父視窗的通知訊息。|  
|[MESSAGE_HANDLER](#message_handler)|將 Windows 訊息對應至處理常式函式。|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|將連續的 Windows 訊息對應至處理常式函式。|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|對應**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼。|  
|[NOTIFY_HANDLER](#notify_handler)|對應**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼和控制識別項。|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|對應**WM_NOTIFY**訊息處理常式函式，根據控制項識別項。|  
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|對應**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼和連續的控制項識別碼範圍。|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|對應**WM_NOTIFY**訊息處理常式函式，根據連續控制識別項的範圍。|  
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|反映回視窗傳送這些通知訊息。|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據通知的程式碼。|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據通知的程式碼和功能表項目、 控制項或快速鍵的識別項。|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據功能表項目、 控制項或快速鍵的識別項。|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據通知的程式碼和連續的控制項識別碼範圍。|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據連續控制識別項的範圍。|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼。|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼和控制識別項。|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據控制項識別項。|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼和連續的控制項識別碼範圍。|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據連續控制識別項的範圍。|  

## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  

##  <a name="alt_msg_map"></a>ALT_MSG_MAP  
 標記替代訊息對應的開頭。  
  
```
ALT_MSG_MAP(msgMapID)
```  
  
### <a name="parameters"></a>參數  
 `msgMapID`  
 [in]訊息對應識別碼。  
  
### <a name="remarks"></a>備註  
 ATL 識別數字的每個訊息對應。 預設訊息對應 (以宣告`BEGIN_MSG_MAP`巨集) 由 0。 替代的訊息對應由`msgMapID`。  
  
 訊息對應用來處理訊息傳送至視窗。 例如， [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)可讓您指定的訊息對應的識別碼中包含的物件。 [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc)然後會使用此訊息對應至適當的處理常式函式或另一個訊息對應的包含的視窗訊息導向。 如需宣告處理常式函式的巨集的清單，請參閱[BEGIN_MSG_MAP](#begin_msg_map)。  
  
 一定會開始使用訊息對應`BEGIN_MSG_MAP`。 然後，您可以宣告後續替代的訊息對應。  
  
 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 請注意，永遠只有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>範例  
 下列範例會顯示預設訊息對應和一個替代的訊息對應，每一個都會包含一個處理常式函式：  
  
 [!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 下一個範例顯示兩個替代訊息對應。 預設訊息對應是空的。  
  
 [!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   

##  <a name="begin_msg_map"></a>BEGIN_MSG_MAP  
 標記的預設訊息對應的開頭。  
  
```
BEGIN_MSG_MAP(theClass)
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 [in]包含訊息對應的類別名稱。  
  
### <a name="remarks"></a>備註  
 [CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc)會使用預設的訊息對應來處理訊息傳送至視窗。 訊息對應將導向至適當的處理常式函式或另一個訊息對應的訊息。  

  
 下列巨集將訊息對應處理常式函式。 此函式都必須定義在`theClass`。  
  
|巨集|描述|  
|-----------|-----------------|  
|[MESSAGE_HANDLER](#message_handler)|將 Windows 訊息對應至處理常式函式。|  
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|將連續的 Windows 訊息對應至處理常式函式。|  
|[COMMAND_HANDLER](#command_handler)|對應**WM_COMMAND**訊息處理常式函式，根據通知的程式碼和功能表項目、 控制項或快速鍵的識別項。|  
|[COMMAND_ID_HANDLER](#command_id_handler)|對應**WM_COMMAND**訊息處理常式函式，根據功能表項目、 控制項或快速鍵的識別項。|  
|[COMMAND_CODE_HANDLER](#command_handler)|對應**WM_COMMAND**訊息處理常式函式，根據通知的程式碼。|  
|[COMMAND_RANGE_HANDLER](#command_range_handler)|對應的連續範圍**WM_COMMAND**訊息處理常式函式，根據功能表項目、 控制項或快速鍵的識別項。|  
|[NOTIFY_HANDLER](#notify_handler)|對應**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼和控制識別項。|  
|[NOTIFY_ID_HANDLER](#notify_id_handler)|對應**WM_NOTIFY**訊息處理常式函式，根據控制項識別項。|  
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|對應**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼。|  
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|對應的連續範圍**WM_NOTIFY**訊息處理常式函式，根據控制識別項。|  
  
 下列巨集將導向至另一個訊息對應的訊息。 此程序稱為 「 鏈結 」。  
  
|巨集|描述|  
|-----------|-----------------|  
|[CHAIN_MSG_MAP](#chain_msg_map)|鏈結至預設的訊息對應中的基底類別。|  
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|鏈結至預設的訊息對應中的類別資料成員。|  
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|鏈結至替代的訊息對應中的基底類別。|  
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|鏈結至替代的訊息對應中的類別資料成員。|  
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|若要在執行階段的另一個類別中的預設訊息對應的鏈結。|  
  
 下列巨集可直接與父視窗的 「 反映 」 訊息。 例如，控制項通常會傳送通知訊息至其父視窗以進行處理，但父視窗可反映出控制項的訊息。  
  
|巨集|描述|  
|-----------|-----------------|  
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據通知的程式碼和功能表項目、 控制項或快速鍵的識別項。|  
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據功能表項目、 控制項或快速鍵的識別項。|  
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據通知的程式碼。|  
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據連續控制識別項的範圍。|  
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|對應反映**WM_COMMAND**訊息處理常式函式，根據通知的程式碼和連續的控制項識別碼範圍。|  
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼和控制識別項。|  
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據控制項識別項。|  
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼。|  
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據連續控制識別項的範圍。|  
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|對應反映**WM_NOTIFY**訊息處理常式函式，根據通知的程式碼和連續的控制項識別碼範圍。|  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]  
  
 當`CMyExtWindow`物件接收`WM_PAINT`訊息，訊息已導向至`CMyExtWindow::OnPaint`的實際處理。 如果`OnPaint`表示訊息不需要進一步處理訊息將則導向預設訊息對應至`CMyBaseWindow`。  
  
 除了預設的訊息對應，您可以定義具有替代訊息對應[ALT_MSG_MAP](#alt_msg_map)。 一定會開始使用訊息對應`BEGIN_MSG_MAP`。 然後，您可以宣告後續替代的訊息對應。 下列範例會顯示預設訊息對應和一個替代的訊息對應，每一個都會包含一個處理常式函式：  
  
 [!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 下一個範例顯示兩個替代訊息對應。 預設訊息對應是空的。  
  
 [!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 請注意，永遠只有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT  
 定義訊息對應中的項目。  
  
```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```  
  
### <a name="parameters"></a>參數  
 `theChainClass`  
 [in]包含訊息對應的基底類別名稱。  
  
 `msgMapID`  
 [in]訊息對應識別碼。  
  
### <a name="remarks"></a>備註  
 `CHAIN_MSG_MAP_ALT`基底類別中，會指示替代訊息對應的訊息。 您也必須宣告具有此替代訊息對應[ALT_MSG_MAP(msgMapID)](#alt_msg_map)。 若要直接基底類別的預設訊息對應的訊息 (使用宣告[BEGIN_MSG_MAP](#begin_msg_map))，使用`CHAIN_MSG_MAP`。 如需範例，請參閱[CHAIN_MSG_MAP](#chain_msg_map)。  
  
> [!NOTE]
>  一定會開始使用訊息對應`BEGIN_MSG_MAP`。 然後，您可以宣告與後續替代的訊息對應`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 每個訊息對應必須有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER  
 定義訊息對應中的項目。  
  
```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```  
  
### <a name="parameters"></a>參數  
 `theChainMember`  
 [in]包含訊息對應的資料成員名稱。  
  
 `msgMapID`  
 [in]訊息對應識別碼。  
  
### <a name="remarks"></a>備註  
 `CHAIN_MSG_MAP_ALT_MEMBER`將替代的訊息對應的訊息導向的資料成員中。 您也必須宣告具有此替代訊息對應[ALT_MSG_MAP(msgMapID)](#alt_msg_map)。 若要將訊息導向的資料成員的預設訊息對應 (以宣告[BEGIN_MSG_MAP](#begin_msg_map))，使用`CHAIN_MSG_MAP_MEMBER`。 如需範例，請參閱[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)。  
  
> [!NOTE]
>  一定會開始使用訊息對應`BEGIN_MSG_MAP`。 然後，您可以宣告與後續替代的訊息對應`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 每個訊息對應必須有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="chain_msg_map"></a>CHAIN_MSG_MAP  
 定義訊息對應中的項目。  
  
```
CHAIN_MSG_MAP(theChainClass)
```  
  
### <a name="parameters"></a>參數  
 `theChainClass`  
 [in]包含訊息對應的基底類別名稱。  
  
### <a name="remarks"></a>備註  
 `CHAIN_MSG_MAP`指示基底類別的預設訊息對應的訊息 (使用宣告[BEGIN_MSG_MAP](#begin_msg_map))。 若要將導向至基底類別的替代訊息對應的訊息 (使用宣告[ALT_MSG_MAP](#alt_msg_map))，使用[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)。  
  
> [!NOTE]
>  一定會開始使用訊息對應`BEGIN_MSG_MAP`。 然後，您可以宣告與後續替代的訊息對應`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 每個訊息對應必須有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]  
  
 此範例說明下列各項：  
  
-   如果使用的視窗程序`CMyClass`的預設訊息對應和`OnPaint`不的處理訊息時，訊息已導向至`CMyBaseClass`的預設處理的訊息對應。  
  
-   如果視窗程序正在使用中的第一個替代的訊息對應`CMyClass`，所有訊息會被都導向至`CMyBaseClass`的預設訊息對應。  
  
-   如果使用的視窗程序`CMyClass`的第二個替代訊息對應和`OnChar`不的處理訊息時，訊息會導向至指定的替代訊息對應`CMyBaseClass`。 `CMyBaseClass`必須與此訊息對應宣告`ALT_MSG_MAP(1)`。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC  
 定義訊息對應中的項目。  
  
```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```  
  
### <a name="parameters"></a>參數  
 *dynaChainID*  
 [in]物件的訊息對應的唯一識別碼。  
  
### <a name="remarks"></a>備註  
 `CHAIN_MSG_MAP_DYNAMIC`在執行階段，以在另一個物件的預設訊息對應，會指示訊息。 物件，其訊息對應相關聯*dynaChainID*，定義透過[CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry)。 您必須衍生您的類別從`CDynamicChain`才能使用`CHAIN_MSG_MAP_DYNAMIC`。 如需範例，請參閱[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概觀。  

  
> [!NOTE]
>  一定會開始使用訊息對應[BEGIN_MSG_MAP](#begin_msg_map)。 然後，您可以宣告與後續替代的訊息對應`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 每個訊息對應必須有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER  
 定義訊息對應中的項目。  
  
```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```  
  
### <a name="parameters"></a>參數  
 `theChainMember`  
 [in]包含訊息對應的資料成員名稱。  
  
### <a name="remarks"></a>備註  
 `CHAIN_MSG_MAP_MEMBER`會指示訊息的資料成員的預設訊息對應 (以宣告[BEGIN_MSG_MAP](#begin_msg_map))。 若要將訊息導向的資料成員的替代訊息對應 (以宣告[ALT_MSG_MAP](#alt_msg_map))，使用[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)。  
  
> [!NOTE]
>  一定會開始使用訊息對應`BEGIN_MSG_MAP`。 然後，您可以宣告與後續替代的訊息對應`ALT_MSG_MAP`。 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 每個訊息對應必須有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]  
  
 此範例說明下列各項：  
  
-   如果使用的視窗程序`CMyClass`的預設訊息對應和`OnPaint`不的處理訊息時，訊息已導向至`m_obj`的預設處理的訊息對應。  
  
-   如果視窗程序正在使用中的第一個替代的訊息對應`CMyClass`，所有訊息會被都導向至`m_obj`的預設訊息對應。  
  
-   如果使用的視窗程序`CMyClass`的第二個替代訊息對應和`OnChar`不的處理訊息時，訊息會導向至指定的替代訊息對應的`m_obj`。 類別`CMyContainedClass`必須與此訊息對應宣告`ALT_MSG_MAP(1)`。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="command_code_handler"></a>COMMAND_CODE_HANDLER  
 類似於[COMMAND_HANDLER](#command_handler)，但對應[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)訊息只根據通知的程式碼。  
  
```
COMMAND_CODE_HANDLER(code, func)
```  
  
### <a name="parameters"></a>參數  
 `code`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="command_handler"></a>COMMAND_HANDLER  
 定義訊息對應中的項目。  
  
```
COMMAND_HANDLER(id, code, func)
```    
  
### <a name="parameters"></a>參數  
 `id`  
 [in]功能表項目、 控制項或快速鍵的識別項。  
  
 `code`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="remarks"></a>備註  
 `COMMAND_HANDLER`對應[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)訊息傳送至指定的處理常式函數，根據通知的程式碼和控制識別項。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]  
  
 指定在任何函式`COMMAND_HANDLER`必須定義巨集，如下所示：  
  
 `LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`  
  
 訊息對應集`bHandled`至**TRUE**之前`CommandHandler`呼叫。 如果`CommandHandler`完全不會處理訊息，它應該設定`bHandled`至**FALSE**以指出需要進一步處理的訊息。  
  
> [!NOTE]
>  一定會開始使用訊息對應[BEGIN_MSG_MAP](#begin_msg_map)。 然後，您可以宣告與後續替代的訊息對應[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 每個訊息對應必須有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 除了`COMMAND_HANDLER`，您可以使用[MESSAGE_HANDLER](#message_handler)對應**WM_COMMAND**訊息而不考慮識別碼或程式碼。 在此情況下，`MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)`直接所有**WM_COMMAND**訊息至`OnHandlerFunction`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="command_id_handler"></a>COMMAND_ID_HANDLER  
 類似於[COMMAND_HANDLER](#command_handler)，但對應[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)訊息只根據功能表項目、 控制項或快速鍵的識別項。  
  
```
COMMAND_ID_HANDLER(id, func)
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]功能表項目、 控制項或傳送訊息的對應鍵的識別項。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER  
 類似於[COMMAND_RANGE_HANDLER](#command_range_handler)，但對應[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)特定通知的程式碼的控制項範圍的單一處理常式函式的訊息。  
  
```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```    
  
### <a name="parameters"></a>參數  
 `idFirst`  
 [in]標記的控制項識別碼連續範圍的開頭。  
  
 `idLast`  
 [in]標記的控制項識別碼連續範圍的結尾。  
  
 `code`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="remarks"></a>備註  
 此範圍為基礎的功能表項目、 控制項或傳送訊息的對應鍵的識別項。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="command_range_handler"></a>COMMAND_RANGE_HANDLER  
 類似於[COMMAND_HANDLER](#command_handler)，但對應[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)控制項的範圍從單一處理常式函式的訊息。  
  
```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```    
  
### <a name="parameters"></a>參數  
 `idFirst`  
 [in]標記的控制項識別碼連續範圍的開頭。  
  
 `idLast`  
 [in]標記的控制項識別碼連續範圍的結尾。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="remarks"></a>備註  
 此範圍為基礎的功能表項目、 控制項或傳送訊息的對應鍵的識別項。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP  
 宣告空白的訊息對應。  
  
```
DECLARE_EMPTY_MSG_MAP()
```  
  
### <a name="remarks"></a>備註  
 `DECLARE_EMPTY_MSG_MAP`呼叫巨集是便利巨集[BEGIN_MSG_MAP](#begin_msg_map)和[END_MSG_MAP](#end_msg_map)建立空白的訊息對應：  
  
 [!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]  
  
##  <a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER  
 提供預設的處理常式會接收的子視窗 （控制） 反映訊息。處理常式會將未處理的訊息，以正確傳遞`DefWindowProc`。  
  
```
DEFAULT_REFLECTION_HANDLER()
```  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="end_msg_map"></a>END_MSG_MAP  
 結束標記的訊息對應。  
  
```
END_MSG_MAP()
```  
  
### <a name="remarks"></a>備註  
 一律使用[BEGIN_MSG_MAP](#begin_msg_map)標記開頭的訊息對應巨集。 使用[ALT_MSG_MAP](#alt_msg_map)宣告後續替代的訊息對應。  
  
 請注意，永遠只有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>範例  
 下列範例會顯示預設訊息對應和一個替代的訊息對應，每一個都會包含一個處理常式函式：  
  
 [!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]  
  
 下一個範例顯示兩個替代訊息對應。 預設訊息對應是空的。  
  
 [!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="forward_notifications"></a>FORWARD_NOTIFICATIONS  
 將轉送至父視窗的通知訊息。  
  
```
FORWARD_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>備註  
 指定此巨集做為訊息對應的一部分。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="message_handler"></a>MESSAGE_HANDLER  
 定義訊息對應中的項目。  
  
```
MESSAGE_HANDLER( msg, func )
```  
  
### <a name="parameters"></a>參數  
 `msg`  
 [in]Windows 訊息。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="remarks"></a>備註  
 `MESSAGE_HANDLER`將 Windows 訊息對應至指定的處理常式函式。  
  
 指定在任何函式`MESSAGE_HANDLER`必須定義巨集，如下所示：  
  
 `LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`  
  
 訊息對應集`bHandled`至**TRUE**之前`MessageHandler`呼叫。 如果`MessageHandler`完全不會處理訊息，它應該設定`bHandled`至**FALSE**以指出需要進一步處理的訊息。  
  
> [!NOTE]
>  一定會開始使用訊息對應[BEGIN_MSG_MAP](#begin_msg_map)。 然後，您可以宣告與後續替代的訊息對應[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 每個訊息對應必須有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 除了`MESSAGE_HANDLER`，您可以使用[COMMAND_HANDLER](#command_handler)和[NOTIFY_HANDLER](#notify_handler)對應[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)和[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)可分別訊息。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER  
 類似於[MESSAGE_HANDLER](#message_handler)，但範圍的 Windows 訊息的單一處理常式函式的對應。  
  
```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```  
  
### <a name="parameters"></a>參數  
 *msgFirst*  
 [in]標記的訊息連續範圍的開頭。  
  
 *msgLast*  
 [in]結束標記的連續範圍的訊息。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER  
 類似於[NOTIFY_HANDLER](#notify_handler)，但對應[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)訊息只根據通知的程式碼。  
  
```
NOTIFY_CODE_HANDLER(cd, func)
```  
  
### <a name="parameters"></a>參數  
 `cd`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="notify_handler"></a>NOTIFY_HANDLER  
 定義訊息對應中的項目。  
  
```
NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]傳送訊息之控制項的識別項。  
  
 `cd`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="remarks"></a>備註  
 `NOTIFY_HANDLER`對應[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)訊息傳送至指定的處理常式函數，根據通知的程式碼和控制識別項。  
  
 指定在任何函式`NOTIFY_HANDLER`必須定義巨集，如下所示：  
  
 `LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`  
  
 訊息對應集`bHandled`至**TRUE**之前`NotifyHandler`呼叫。 如果`NotifyHandler`完全不會處理訊息，它應該設定`bHandled`至**FALSE**以指出需要進一步處理的訊息。  
  
> [!NOTE]
>  一定會開始使用訊息對應[BEGIN_MSG_MAP](#begin_msg_map)。 然後，您可以宣告與後續替代的訊息對應[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)巨集標示為訊息對應的結尾。 每個訊息對應必須有一個執行個體`BEGIN_MSG_MAP`和`END_MSG_MAP`。  
  
 除了`NOTIFY_HANDLER`，您可以使用[MESSAGE_HANDLER](#message_handler)對應**WM_NOTIFY**訊息而不考慮識別碼或程式碼。 在此情況下，`MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)`直接所有**WM_NOTIFY**訊息至`OnHandlerFunction`。  
  
 如需有關如何使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="notify_id_handler"></a>NOTIFY_ID_HANDLER  
 類似於[NOTIFY_HANDLER](#notify_handler)，但對應[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)訊息只根據控制識別項。  
  
```
NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]傳送訊息之控制項的識別項。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER  
 類似於[NOTIFY_RANGE_HANDLER](#notify_range_handler)，但對應[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)特定通知的程式碼的控制項範圍的單一處理常式函式的訊息。  
  
```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```  
  
### <a name="parameters"></a>參數  
 `idFirst`  
 [in]標記的控制項識別碼連續範圍的開頭。  
  
 `idLast`  
 [in]標記的控制項識別碼連續範圍的結尾。  
  
 `cd`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="remarks"></a>備註  
 此範圍為基礎的傳送訊息之控制項的識別項。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER  
 類似於[NOTIFY_HANDLER](#notify_handler)，但對應[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)控制項的範圍從單一處理常式函式的訊息。  
  
```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>參數  
 `idFirst`  
 [in]標記的控制項識別碼連續範圍的開頭。  
  
 `idLast`  
 [in]標記的控制項識別碼連續範圍的結尾。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="remarks"></a>備註  
 此範圍為基礎的傳送訊息之控制項的識別項。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS  
 反映回傳送它們的子視窗 （控制項） 的通知訊息。  
  
```
REFLECT_NOTIFICATIONS()
```  
  
### <a name="remarks"></a>備註  
 指定此巨集做為父視窗的訊息對應的一部分。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER  
 類似於[COMMAND_CODE_HANDLER](#command_code_handler)，但對應反映與父視窗的命令。  
  
```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```  
  
### <a name="parameters"></a>參數  
 `code`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
   
##  <a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER  
 類似於[COMMAND_HANDLER](#command_handler)，但對應反映與父視窗的命令。  
  
```
REFLECTED_COMMAND_HANDLER( id, code, func )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]功能表項目、 控制項或快速鍵的識別項。  
  
 `code`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  

##  <a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER  
 類似於[COMMAND_ID_HANDLER](#command_id_handler)，但對應反映與父視窗的命令。  
  
```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]功能表項目、 控制項或快速鍵的識別項。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  

##  <a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER  
 類似於[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)，但對應反映與父視窗的命令。  
  
```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```  
  
### <a name="parameters"></a>參數  
 `idFirst`  
 [in]標記的控制項識別碼連續範圍的開頭。  
  
 `idLast`  
 [in]標記的控制項識別碼連續範圍的結尾。  
  
 `code`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  

##  <a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER  
 類似於[COMMAND_RANGE_HANDLER](#command_range_handler)，但對應反映與父視窗的命令。  
  
```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>參數  
 `idFirst`  
 [in]標記的控制項識別碼連續範圍的開頭。  
  
 `idLast`  
 [in]標記的控制項識別碼連續範圍的結尾。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  

##  <a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER  
 類似於[NOTIFY_CODE_HANDLER](#notify_code_handler)，但對應反映與父視窗的通知。  
  
```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```  
  
### <a name="parameters"></a>參數  
 `cd`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  

##  <a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER  
 類似於[NOTIFY_HANDLER](#notify_handler)，但對應反映與父視窗的通知。  
  
```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]功能表項目、 控制項或快速鍵的識別項。  
  
 `cd`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  

##  <a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER  
 類似於[NOTIFY_ID_HANDLER](#notify_id_handler)，但對應反映與父視窗的通知。  
  
```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]功能表項目、 控制項或快速鍵的識別項。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  

##  <a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER  
 類似於[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)，但對應反映與父視窗的通知。  
  
```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```    
  
### <a name="parameters"></a>參數  
 `idFirst`  
 [in]標記的控制項識別碼連續範圍的開頭。  
  
 `idLast`  
 [in]標記的控制項識別碼連續範圍的結尾。  
  
 `cd`  
 [in]通知程式碼中。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlwin.h   
  
##  <a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER  
 類似於[NOTIFY_RANGE_HANDLER](#notify_range_handler)，但對應反映與父視窗的通知。  
  
```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```  
  
### <a name="parameters"></a>參數  
 `idFirst`  
 [in]標記的控制項識別碼連續範圍的開頭。  
  
 `idLast`  
 [in]標記的控制項識別碼連續範圍的結尾。  
  
 `func`  
 [in]訊息處理常式函式的名稱。  
  
## <a name="see-also"></a>請參閱  
 [巨集](../../atl/reference/atl-macros.md)
