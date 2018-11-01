---
title: 訊息對應巨集 (ATL)
ms.date: 11/04/2016
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
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: 5502dae40392679f47b691a822260accbf597dc0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555099"
---
# <a name="message-map-macros-atl"></a>訊息對應巨集 (ATL)

這些巨集會定義訊息對應 」 和 「 項目。

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|標記替代訊息對應的開頭。|
|[BEGIN_MSG_MAP](#begin_msg_map)|標記預設訊息對應的開頭。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|鏈結至替代的訊息對應中的基底類別。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|鏈結至替代的訊息對應中的類別資料成員。|
|[CHAIN_MSG_MAP](#chain_msg_map)|預設訊息中對應的基底類別鏈結。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|鏈結至另一個類別，在執行階段中的訊息對應。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|預設訊息中對應的類別資料成員的鏈結。|
|[COMMAND_CODE_HANDLER](#command_code_handler)|對應的 WM_COMMAND 訊息處理常式函式，以通知程式碼。|
|[COMMAND_HANDLER](#command_handler)|對應的 WM_COMMAND 訊息處理常式函式，根據通知程式碼和功能表項目、 控制項或加速器的識別碼。|
|[COMMAND_ID_HANDLER](#command_id_handler)|對應的 WM_COMMAND 訊息處理常式函式，根據識別項的功能表項目、 控制項或加速器。|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|對應的 WM_COMMAND 訊息處理常式函式，根據通知程式碼和連續範圍的控制識別項。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|對應的 WM_COMMAND 訊息處理常式函式，根據連續控制識別項的範圍。|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|實作空白的訊息對應。|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|提供反映的訊息，否則為未處理的預設處理常式。|
|[END_MSG_MAP](#end_msg_map)|標記訊息對應的結尾。|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|將轉送通知訊息給父視窗。|
|[MESSAGE_HANDLER](#message_handler)|將 Windows 訊息對應至處理常式函式。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|將連續的 Windows 訊息對應至處理常式函式。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|對應處理常式函式，通知程式碼為基礎的 WM_NOTIFY 訊息。|
|[NOTIFY_HANDLER](#notify_handler)|對應的 WM_NOTIFY 訊息處理常式函式，根據通知程式碼和控制項識別項。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|對應的 WM_NOTIFY 訊息處理常式函式，根據的控制項識別項。|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|對應的 WM_NOTIFY 訊息處理常式函式，根據通知程式碼和連續範圍的控制識別項。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|對應的 WM_NOTIFY 訊息處理常式函式，根據連續控制識別項的範圍。|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|會反映回傳送它們的視窗通知訊息。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，以通知程式碼。|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，根據通知程式碼和功能表項目、 控制項或加速器的識別碼。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，根據識別項的功能表項目、 控制項或加速器。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，根據通知程式碼和連續範圍的控制識別項。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，根據連續控制識別項的範圍。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，以通知程式碼。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，根據通知程式碼和控制項識別項。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，根據的控制項識別項。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，根據通知程式碼和連續範圍的控制識別項。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，根據連續控制識別項的範圍。|

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="alt_msg_map"></a>  ALT_MSG_MAP

標記替代訊息對應的開頭。

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>參數

*msgMapID*<br/>
[in]訊息對應識別項。

### <a name="remarks"></a>備註

ATL 識別數字的每個訊息對應。 預設訊息對應 （BEGIN_MSG_MAP 巨集宣告） 是由 0 識別。 替代的訊息對應由*msgMapID*。

訊息對應用來處理訊息傳送至視窗。 例如， [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)可讓您指定的識別項的訊息對應中包含的物件。 [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc)然後會使用此訊息對應將導向包含的視窗的訊息至適當的處理常式函式或另一個訊息對應。 如需宣告處理常式的函式的巨集的清單，請參閱 < [BEGIN_MSG_MAP](#begin_msg_map)。

一定會開始與 BEGIN_MSG_MAP 訊息對應。 然後，您可以宣告替代的後續訊息對應。

[END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 請注意，總是 BEGIN_MSG_MAP 和 END_MSG_MAP 只有一個執行個體。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

下列範例會顯示預設訊息對應以及每一個都包含一個處理常式函式的一個替代的訊息對應：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一個範例顯示兩個替代的訊息對應。 預設訊息對應是空的。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="begin_msg_map"></a>  BEGIN_MSG_MAP

標記預設訊息對應的開頭。

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
[in]包含訊息對應的類別名稱。

### <a name="remarks"></a>備註

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc)會使用預設的訊息對應來處理訊息傳送至視窗。 訊息對應會將導向至適當的處理常式函式或另一個訊息對應的訊息。

下列巨集對應至處理常式函式的訊息。 此函式必須定義於*theClass*。

|巨集|描述|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|將 Windows 訊息對應至處理常式函式。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|將連續的 Windows 訊息對應至處理常式函式。|
|[COMMAND_HANDLER](#command_handler)|對應的 WM_COMMAND 訊息處理常式函式，根據通知程式碼和功能表項目、 控制項或加速器的識別碼。|
|[COMMAND_ID_HANDLER](#command_id_handler)|對應的 WM_COMMAND 訊息處理常式函式，根據識別項的功能表項目、 控制項或加速器。|
|[COMMAND_CODE_HANDLER](#command_handler)|對應的 WM_COMMAND 訊息處理常式函式，以通知程式碼。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|對應連續 WM_COMMAND 訊息處理常式函式，根據識別項的功能表項目、 控制項或加速器。|
|[NOTIFY_HANDLER](#notify_handler)|對應的 WM_NOTIFY 訊息處理常式函式，根據通知程式碼和控制項識別項。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|對應的 WM_NOTIFY 訊息處理常式函式，根據的控制項識別項。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|對應處理常式函式，通知程式碼為基礎的 WM_NOTIFY 訊息。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|將連續的 WM_NOTIFY 訊息對應處理常式函式，根據的控制項識別項。|

下列巨集直接加入另一個訊息對應的訊息。 此程序稱為 「 鏈結 」。

|巨集|描述|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|預設訊息中對應的基底類別鏈結。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|預設訊息中對應的類別資料成員的鏈結。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|鏈結至替代的訊息對應中的基底類別。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|鏈結至替代的訊息對應中的類別資料成員。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|鏈結至另一個類別，在執行階段中的預設訊息對應。|

下列巨集直接從父視窗的 「 反映 」 訊息。 例如，控制項通常會傳送通知訊息至其父視窗，如處理，但父視窗可反映出控制項的訊息。

|巨集|描述|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，根據通知程式碼和功能表項目、 控制項或加速器的識別碼。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，根據識別項的功能表項目、 控制項或加速器。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，以通知程式碼。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，根據連續控制識別項的範圍。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|對應反映的 WM_COMMAND 訊息處理常式函式，根據通知程式碼和連續範圍的控制識別項。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，根據通知程式碼和控制項識別項。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，根據的控制項識別項。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，以通知程式碼。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，根據連續控制識別項的範圍。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|將反映的 WM_NOTIFY 訊息對應處理常式函式，根據通知程式碼和連續範圍的控制識別項。|

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

當`CMyExtWindow`物件收到 WM_PAINT 訊息時，訊息導向到`CMyExtWindow::OnPaint`的實際處理。 如果`OnPaint`指出訊息需要進一步處理，則訊息會接著被導向至預設的訊息對應中`CMyBaseWindow`。

除了預設訊息對應中，您可以定義具有替代訊息對應[ALT_MSG_MAP](#alt_msg_map)。 一定會開始與 BEGIN_MSG_MAP 訊息對應。 然後，您可以宣告替代的後續訊息對應。 下列範例會顯示預設訊息對應以及每一個都包含一個處理常式函式的一個替代的訊息對應：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一個範例顯示兩個替代的訊息對應。 預設訊息對應是空的。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 請注意，總是 BEGIN_MSG_MAP 和 END_MSG_MAP 只有一個執行個體。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="chain_msg_map_alt"></a>  CHAIN_MSG_MAP_ALT

訊息對應中定義的項目。

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>參數

*theChainClass*<br/>
[in]包含訊息對應的基底類別名稱。

*msgMapID*<br/>
[in]訊息對應識別項。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_ALT 將基底類別中導向至替代的訊息對應的訊息。 您也必須宣告與此替代訊息對應[ALT_MSG_MAP(msgMapID)](#alt_msg_map)。 若要將基底類別的預設訊息對應的訊息 (使用宣告[BEGIN_MSG_MAP](#begin_msg_map))，使用 CHAIN_MSG_MAP。 如需範例，請參閱[CHAIN_MSG_MAP](#chain_msg_map)。

> [!NOTE]
>  一定會開始與 BEGIN_MSG_MAP 訊息對應。 然後，您可以宣告使用 ALT_MSG_MAP 的後續替代的訊息對應。 [END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 每個訊息對應必須有一個執行個體 BEGIN_MSG_MAP 和 END_MSG_MAP。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="chain_msg_map_alt_member"></a>  CHAIN_MSG_MAP_ALT_MEMBER

訊息對應中定義的項目。

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>參數

*theChainMember*<br/>
[in]包含訊息對應的資料成員名稱。

*msgMapID*<br/>
[in]訊息對應識別項。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_ALT_MEMBER 指示訊息至替代的訊息對應中的資料成員。 您也必須宣告與此替代訊息對應[ALT_MSG_MAP(msgMapID)](#alt_msg_map)。 若要將資料成員的預設訊息對應的訊息 (使用宣告[BEGIN_MSG_MAP](#begin_msg_map))，使用 CHAIN_MSG_MAP_MEMBER。 如需範例，請參閱[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)。

> [!NOTE]
>  一定會開始與 BEGIN_MSG_MAP 訊息對應。 然後，您可以宣告使用 ALT_MSG_MAP 的後續替代的訊息對應。 [END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 每個訊息對應必須有一個執行個體 BEGIN_MSG_MAP 和 END_MSG_MAP。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="chain_msg_map"></a>  CHAIN_MSG_MAP

訊息對應中定義的項目。

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>參數

*theChainClass*<br/>
[in]包含訊息對應的基底類別名稱。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP 指示基底類別的預設訊息對應的訊息 (使用宣告[BEGIN_MSG_MAP](#begin_msg_map))。 若要將基底類別的替代訊息對應的訊息 (使用宣告[ALT_MSG_MAP](#alt_msg_map))，使用[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)。

> [!NOTE]
>  一定會開始與 BEGIN_MSG_MAP 訊息對應。 然後，您可以宣告使用 ALT_MSG_MAP 的後續替代的訊息對應。 [END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 每個訊息對應必須有一個執行個體 BEGIN_MSG_MAP 和 END_MSG_MAP。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

此範例說明下列要點：

- 如果使用的視窗程序`CMyClass`的預設訊息對應和`OnPaint`不會的處理訊息時，訊息導向到`CMyBaseClass`的預設處理的訊息對應。

- 如果視窗程序正在使用中的第一個替代訊息對應`CMyClass`，所有訊息會被都導向至`CMyBaseClass`的預設訊息對應。

- 如果使用的視窗程序`CMyClass`的第二個替代的訊息對應並`OnChar`不會的處理訊息，訊息會導向至指定的替代訊息對應中`CMyBaseClass`。 `CMyBaseClass` 必須有宣告 ALT_MSG_MAP(1) 與此訊息對應。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="chain_msg_map_dynamic"></a>  CHAIN_MSG_MAP_DYNAMIC

訊息對應中定義的項目。

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>參數

*dynaChainID*<br/>
[in]物件的訊息對應的唯一識別碼。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_DYNAMIC 指示訊息，在執行階段，在另一個物件的預設訊息對應。 物件，其訊息對應相關聯*dynaChainID*，其中您透過定義[CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry)。 您必須衍生您的類別，從`CDynamicChain`才能使用 CHAIN_MSG_MAP_DYNAMIC。 如需範例，請參閱[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概觀。

> [!NOTE]
>  一定會開始使用的訊息對應[BEGIN_MSG_MAP](#begin_msg_map)。 然後，您可以宣告使用 ALT_MSG_MAP 的後續替代的訊息對應。 [END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 每個訊息對應必須有一個執行個體 BEGIN_MSG_MAP 和 END_MSG_MAP。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="chain_msg_map_member"></a>  CHAIN_MSG_MAP_MEMBER

訊息對應中定義的項目。

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>參數

*theChainMember*<br/>
[in]包含訊息對應的資料成員名稱。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_MEMBER 會指示訊息的資料成員的預設訊息對應 (以宣告[BEGIN_MSG_MAP](#begin_msg_map))。 若要將導向至資料成員的替代訊息對應的訊息 (使用宣告[ALT_MSG_MAP](#alt_msg_map))，使用[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)。

> [!NOTE]
>  一定會開始與 BEGIN_MSG_MAP 訊息對應。 然後，您可以宣告使用 ALT_MSG_MAP 的後續替代的訊息對應。 [END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 每個訊息對應必須有一個執行個體 BEGIN_MSG_MAP 和 END_MSG_MAP。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

此範例說明下列要點：

- 如果使用的視窗程序`CMyClass`的預設訊息對應和`OnPaint`不會的處理訊息時，訊息導向到`m_obj`的預設處理的訊息對應。

- 如果視窗程序正在使用中的第一個替代訊息對應`CMyClass`，所有訊息會被都導向至`m_obj`的預設訊息對應。

- 如果使用的視窗程序`CMyClass`的第二個替代的訊息對應並`OnChar`不會的處理訊息，訊息會導向至指定的替代訊息對應的`m_obj`。 類別`CMyContainedClass`必須有宣告 ALT_MSG_MAP(1) 與此訊息對應。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="command_code_handler"></a>  COMMAND_CODE_HANDLER

類似於[COMMAND_HANDLER](#command_handler)，但會將對應[WM_COMMAND](/windows/desktop/menurc/wm-command)訊息只根據通知程式碼。

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>參數

*程式碼*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="command_handler"></a>  COMMAND_HANDLER

訊息對應中定義的項目。

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>參數

*id*<br/>
[in]功能表項目、 控制項或加速器的識別項。

*程式碼*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

對應 COMMAND_HANDLER [WM_COMMAND](/windows/desktop/menurc/wm-command)至指定的處理常式函式，根據通知程式碼和控制項識別項的訊息。 例如: 

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

必須定義在 COMMAND_HANDLER 巨集中指定的任何函式如下所示：

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

訊息對應集`bHandled`設為 TRUE 之前`CommandHandler`呼叫。 如果`CommandHandler`完全不會處理訊息，它應該設定`bHandled`為 FALSE，以指出需要進一步處理的訊息。

> [!NOTE]
>  一定會開始使用的訊息對應[BEGIN_MSG_MAP](#begin_msg_map)。 然後，您可以宣告使用後續的替代訊息對應[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 每個訊息對應必須有一個執行個體 BEGIN_MSG_MAP 和 END_MSG_MAP。

除了 COMMAND_HANDLER，您可以使用[MESSAGE_HANDLER](#message_handler) WM_COMMAND 訊息，而不是識別碼或程式碼對應。 在此情況下，`MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)`會將所有 WM_COMMAND 訊息都導向`OnHandlerFunction`。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="command_id_handler"></a>  COMMAND_ID_HANDLER

類似於[COMMAND_HANDLER](#command_handler)，但會將對應[WM_COMMAND](/windows/desktop/menurc/wm-command)訊息只會依據的功能表項目、 控制項或加速器的識別項。

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>參數

*id*<br/>
[in]功能表項目、 控制項或傳送訊息的對應鍵的識別碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="command_range_code_handler"></a>  COMMAND_RANGE_CODE_HANDLER

類似於[COMMAND_RANGE_HANDLER](#command_range_handler)，但會將對應[WM_COMMAND](/windows/desktop/menurc/wm-command)特定通知的程式碼從一組控制項台中單一處理常式函式的訊息。

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[in]標記控制識別項的連續範圍的開頭。

*idLast*<br/>
[in]標記的控制項識別項的連續範圍的結尾。

*程式碼*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

此範圍為基礎的功能表項目、 控制項或傳送訊息的對應鍵的識別碼。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="command_range_handler"></a>  COMMAND_RANGE_HANDLER

類似於[COMMAND_HANDLER](#command_handler)，但會將對應[WM_COMMAND](/windows/desktop/menurc/wm-command)單一處理常式函式從一組控制項台中的訊息。

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[in]標記控制識別項的連續範圍的開頭。

*idLast*<br/>
[in]標記的控制項識別項的連續範圍的結尾。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

此範圍為基礎的功能表項目、 控制項或傳送訊息的對應鍵的識別碼。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="declare_empty_msg_map"></a>  DECLARE_EMPTY_MSG_MAP

宣告空白的訊息對應。

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>備註

DECLARE_EMPTY_MSG_MAP 是為了方便起見巨集呼叫巨集[BEGIN_MSG_MAP](#begin_msg_map)並[END_MSG_MAP](#end_msg_map)建立空白的訊息對應：

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

##  <a name="default_reflection_handler"></a>  DEFAULT_REFLECTION_HANDLER

提供預設處理常式會收到子視窗 （控制） 反映訊息;處理常式將會正確傳遞未處理的訊息，以`DefWindowProc`。

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="end_msg_map"></a>  END_MSG_MAP

標記訊息對應的結尾。

```
END_MSG_MAP()
```

### <a name="remarks"></a>備註

一律使用[BEGIN_MSG_MAP](#begin_msg_map)巨集來標示訊息對應的開頭。 使用[ALT_MSG_MAP](#alt_msg_map)宣告替代的後續訊息對應。

請注意，總是 BEGIN_MSG_MAP 和 END_MSG_MAP 只有一個執行個體。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

下列範例會顯示預設訊息對應以及每一個都包含一個處理常式函式的一個替代的訊息對應：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一個範例顯示兩個替代的訊息對應。 預設訊息對應是空的。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="forward_notifications"></a>  FORWARD_NOTIFICATIONS

將轉送通知訊息給父視窗。

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>備註

指定此巨集做為訊息對應的一部分。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="message_handler"></a>  MESSAGE_HANDLER

訊息對應中定義的項目。

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>參數

*訊息*<br/>
[in]Windows 訊息。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

MESSAGE_HANDLER 會將 Windows 訊息對應至指定的處理常式函式。

必須定義在 MESSAGE_HANDLER 巨集中指定的任何函式如下所示：

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

訊息對應集`bHandled`設為 TRUE 之前`MessageHandler`呼叫。 如果`MessageHandler`完全不會處理訊息，它應該設定`bHandled`為 FALSE，以指出需要進一步處理的訊息。

> [!NOTE]
>  一定會開始使用的訊息對應[BEGIN_MSG_MAP](#begin_msg_map)。 然後，您可以宣告使用後續的替代訊息對應[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 每個訊息對應必須有一個執行個體 BEGIN_MSG_MAP 和 END_MSG_MAP。

除了 MESSAGE_HANDLER，您可以使用[COMMAND_HANDLER](#command_handler)並[NOTIFY_HANDLER](#notify_handler)對應[WM_COMMAND](/windows/desktop/menurc/wm-command)並[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)訊息分別。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="message_range_handler"></a>  MESSAGE_RANGE_HANDLER

類似於[MESSAGE_HANDLER](#message_handler)，但範圍的 Windows 訊息的單一處理常式函式的對應。

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>參數

*msgFirst*<br/>
[in]標記訊息的連續範圍的開頭。

*msgLast*<br/>
[in]標記結尾的連續範圍的訊息。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="notify_code_handler"></a>  NOTIFY_CODE_HANDLER

類似於[NOTIFY_HANDLER](#notify_handler)，但會將對應[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)訊息只根據通知程式碼。

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>參數

*cd*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="notify_handler"></a>  NOTIFY_HANDLER

訊息對應中定義的項目。

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[in]傳送訊息的控制項識別項。

*cd*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

對應 NOTIFY_HANDLER [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)至指定的處理常式函式，根據通知程式碼和控制項識別項的訊息。

必須定義在 NOTIFY_HANDLER 巨集中指定的任何函式如下所示：

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

訊息對應集`bHandled`設為 TRUE 之前`NotifyHandler`呼叫。 如果`NotifyHandler`完全不會處理訊息，它應該設定`bHandled`為 FALSE，以指出需要進一步處理的訊息。

> [!NOTE]
>  一定會開始使用的訊息對應[BEGIN_MSG_MAP](#begin_msg_map)。 然後，您可以宣告使用後續的替代訊息對應[ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)巨集標記訊息對應的結尾。 每個訊息對應必須有一個執行個體 BEGIN_MSG_MAP 和 END_MSG_MAP。

除了 NOTIFY_HANDLER，您可以使用[MESSAGE_HANDLER](#message_handler) WM_NOTIFY 訊息，而不是識別碼或程式碼對應。 在此情況下，`MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)`會將所有 WM_NOTIFY 訊息都導向`OnHandlerFunction`。

如需使用 ATL 中的訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="notify_id_handler"></a>  NOTIFY_ID_HANDLER

類似於[NOTIFY_HANDLER](#notify_handler)，但會將對應[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)訊息只會依據的控制項識別項。

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[in]傳送訊息的控制項識別項。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="notify_range_code_handler"></a>  NOTIFY_RANGE_CODE_HANDLER

類似於[NOTIFY_RANGE_HANDLER](#notify_range_handler)，但會將對應[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)特定通知的程式碼從一組控制項台中單一處理常式函式的訊息。

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[in]標記控制識別項的連續範圍的開頭。

*idLast*<br/>
[in]標記的控制項識別項的連續範圍的結尾。

*cd*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

此範圍取決於傳送訊息之控制項的識別項。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="notify_range_handler"></a>  NOTIFY_RANGE_HANDLER

類似於[NOTIFY_HANDLER](#notify_handler)，但會將對應[WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)單一處理常式函式從一組控制項台中的訊息。

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[in]標記控制識別項的連續範圍的開頭。

*idLast*<br/>
[in]標記的控制項識別項的連續範圍的結尾。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="remarks"></a>備註

此範圍取決於傳送訊息之控制項的識別項。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflect_notifications"></a>  REFLECT_NOTIFICATIONS

會反映回傳送給子視窗 （控制項） 的通知訊息。

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>備註

指定此巨集做為父視窗的訊息對應的一部分。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_command_code_handler"></a>  REFLECTED_COMMAND_CODE_HANDLER

類似於[COMMAND_CODE_HANDLER](#command_code_handler)，但反映從父視窗的命令會將對應。

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>參數

*程式碼*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_command_handler"></a>  REFLECTED_COMMAND_HANDLER

類似於[COMMAND_HANDLER](#command_handler)，但反映從父視窗的命令會將對應。

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[in]功能表項目、 控制項或加速器的識別項。

*程式碼*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_command_id_handler"></a>  REFLECTED_COMMAND_ID_HANDLER

類似於[COMMAND_ID_HANDLER](#command_id_handler)，但反映從父視窗的命令會將對應。

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[in]功能表項目、 控制項或加速器的識別項。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_command_range_code_handler"></a>  REFLECTED_COMMAND_RANGE_CODE_HANDLER

類似於[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)，但反映從父視窗的命令會將對應。

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[in]標記控制識別項的連續範圍的開頭。

*idLast*<br/>
[in]標記的控制項識別項的連續範圍的結尾。

*程式碼*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_command_range_handler"></a>  REFLECTED_COMMAND_RANGE_HANDLER

類似於[COMMAND_RANGE_HANDLER](#command_range_handler)，但反映從父視窗的命令會將對應。

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[in]標記控制識別項的連續範圍的開頭。

*idLast*<br/>
[in]標記的控制項識別項的連續範圍的結尾。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_notify_code_handler"></a>  REFLECTED_NOTIFY_CODE_HANDLER

類似於[NOTIFY_CODE_HANDLER](#notify_code_handler)，但會將對應從父視窗所反映的通知。

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>參數

*cd*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_notify_handler"></a>  REFLECTED_NOTIFY_HANDLER

類似於[NOTIFY_HANDLER](#notify_handler)，但會將對應從父視窗所反映的通知。

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[in]功能表項目、 控制項或加速器的識別項。

*cd*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_notify_id_handler"></a>  REFLECTED_NOTIFY_ID_HANDLER

類似於[NOTIFY_ID_HANDLER](#notify_id_handler)，但會將對應從父視窗所反映的通知。

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[in]功能表項目、 控制項或加速器的識別項。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_notify_range_code_handler"></a>  REFLECTED_NOTIFY_RANGE_CODE_HANDLER

類似於[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)，但會將對應從父視窗所反映的通知。

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[in]標記控制識別項的連續範圍的開頭。

*idLast*<br/>
[in]標記的控制項識別項的連續範圍的結尾。

*cd*<br/>
[in]通知的程式碼。

*func*<br/>
[in]訊息處理常式函式的名稱。

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="reflected_notify_range_handler"></a>  REFLECTED_NOTIFY_RANGE_HANDLER

類似於[NOTIFY_RANGE_HANDLER](#notify_range_handler)，但會將對應從父視窗所反映的通知。

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[in]標記控制識別項的連續範圍的開頭。

*idLast*<br/>
[in]標記的控制項識別項的連續範圍的結尾。

*func*<br/>
[in]訊息處理常式函式的名稱。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
