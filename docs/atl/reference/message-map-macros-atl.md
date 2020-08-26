---
title: '訊息對應宏 (ATL) '
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
ms.openlocfilehash: 9917f31dbb115552cf9dc9bde24f7b6921611750
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835294"
---
# <a name="message-map-macros-atl"></a>訊息對應宏 (ATL) 

這些宏會定義訊息對應和專案。

|名稱|描述|
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|標示替代訊息對應的開頭。|
|[BEGIN_MSG_MAP](#begin_msg_map)|標示預設訊息對應的開頭。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|連結至基類中的替代訊息對應。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|在類別的資料成員中，連結至替代的訊息對應。|
|[CHAIN_MSG_MAP](#chain_msg_map)|連結至基類中的預設訊息對應。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|在執行時間將連結至另一個類別中的訊息對應。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|在類別的資料成員中，連結到預設的訊息對應。|
|[COMMAND_CODE_HANDLER](#command_code_handler)|根據通知碼將 WM_COMMAND 訊息對應至處理常式函式。|
|[COMMAND_HANDLER](#command_handler)|根據通知碼以及功能表項目、控制項或快速鍵的識別碼，將 WM_COMMAND 訊息對應至處理常式函式。|
|[COMMAND_ID_HANDLER](#command_id_handler)|根據功能表項目、控制項或快速鍵的識別碼，將 WM_COMMAND 訊息對應至處理常式函數。|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|根據通知碼和連續的控制項識別碼範圍，將 WM_COMMAND 訊息對應至處理常式函數。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|根據控制項識別碼的連續範圍，將 WM_COMMAND 訊息對應至處理常式函數。|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|實作為空白的訊息對應。|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|針對未處理的訊息，提供預設的處理常式。|
|[END_MSG_MAP](#end_msg_map)|標記訊息對應的結尾。|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|將通知訊息轉送至父視窗。|
|[MESSAGE_HANDLER](#message_handler)|將 Windows 訊息對應至處理常式函數。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|將連續的 Windows 訊息範圍對應至處理常式函數。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|根據通知碼將 WM_NOTIFY 訊息對應至處理常式函式。|
|[NOTIFY_HANDLER](#notify_handler)|根據通知碼和控制項識別碼，將 WM_NOTIFY 訊息對應至處理常式函式。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|根據控制項識別碼，將 WM_NOTIFY 訊息對應至處理常式函數。|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|根據通知碼和連續的控制項識別碼範圍，將 WM_NOTIFY 訊息對應至處理常式函數。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|根據控制項識別碼的連續範圍，將 WM_NOTIFY 訊息對應至處理常式函數。|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|將通知訊息反映回傳送給它們的視窗。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|根據通知碼將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|根據通知碼以及功能表項目、控制項或快速鍵的識別碼，將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|根據功能表項目、控制項或快速鍵的識別碼，將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|根據通知碼和連續的控制項識別碼範圍，將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|根據控制項識別碼的連續範圍，將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|根據通知碼將反映的 WM_NOTIFY 訊息對應至處理常式函式。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|根據通知碼和控制項識別碼，將反映的 WM_NOTIFY 訊息對應至處理常式函式。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|根據控制項識別碼，將反映的 WM_NOTIFY 訊息對應至處理常式函數。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|根據通知碼和連續的控制項識別碼範圍，將反映的 WM_NOTIFY 訊息對應至處理常式函式。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|根據控制項識別碼的連續範圍，將反映的 WM_NOTIFY 訊息對應至處理常式函式。|

## <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a> ALT_MSG_MAP

標示替代訊息對應的開頭。

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>參數

*msgMapID*<br/>
在訊息對應識別碼。

### <a name="remarks"></a>備註

ATL 會依數位來識別每個訊息對應。 預設的訊息對應 (BEGIN_MSG_MAP 宏所宣告) 是由0所識別。 替代訊息對應是由 *msgMapID*識別。

訊息對應是用來處理傳送至視窗的訊息。 例如， [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 可讓您指定包含物件中訊息對應的識別碼。 [CContainedWindow：： WindowProc](ccontainedwindowt-class.md#windowproc) 接著會使用這個訊息對應，將自主視窗的訊息導向至適當的處理常式函式或其他訊息對應。 如需宣告處理常式函式的宏清單，請參閱 [BEGIN_MSG_MAP](#begin_msg_map)。

一律開始 BEGIN_MSG_MAP 的訊息對應。 然後，您可以宣告後續的替代訊息對應。

[END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 請注意，一律只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

下列範例會顯示預設的訊息對應和一個替代訊息對應，其中每個都包含一個處理函式：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一個範例顯示兩個替代的訊息對應。 預設的訊息對應是空的。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a> BEGIN_MSG_MAP

標示預設訊息對應的開頭。

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
在包含訊息對應之類別的名稱。

### <a name="remarks"></a>備註

[CWindowImpl：： WindowProc](cwindowimpl-class.md#windowproc) 會使用預設的訊息對應來處理傳送至視窗的訊息。 訊息對應會將訊息導向至適當的處理常式函式或其他訊息對應。

下列宏會將訊息對應至處理常式函數。 此函數必須在 *theClass*中定義。

|巨集|描述|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|將 Windows 訊息對應至處理常式函數。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|將連續的 Windows 訊息範圍對應至處理常式函數。|
|[COMMAND_HANDLER](#command_handler)|根據通知碼以及功能表項目、控制項或快速鍵的識別碼，將 WM_COMMAND 訊息對應至處理常式函式。|
|[COMMAND_ID_HANDLER](#command_id_handler)|根據功能表項目、控制項或快速鍵的識別碼，將 WM_COMMAND 訊息對應至處理常式函數。|
|[COMMAND_CODE_HANDLER](#command_handler)|根據通知碼將 WM_COMMAND 訊息對應至處理常式函式。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|根據功能表項目、控制項或快速鍵的識別碼，將 WM_COMMAND 訊息的連續範圍對應至處理常式函數。|
|[NOTIFY_HANDLER](#notify_handler)|根據通知碼和控制項識別碼，將 WM_NOTIFY 訊息對應至處理常式函式。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|根據控制項識別碼，將 WM_NOTIFY 訊息對應至處理常式函數。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|根據通知碼將 WM_NOTIFY 訊息對應至處理常式函式。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|根據控制項識別碼，將 WM_NOTIFY 訊息的連續範圍對應至處理常式函數。|

下列宏會將訊息導向至另一個訊息對應。 此處理程式稱為「連結」。

|巨集|描述|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|連結至基類中的預設訊息對應。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|在類別的資料成員中，連結到預設的訊息對應。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|連結至基類中的替代訊息對應。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|在類別的資料成員中，連結至替代的訊息對應。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|在執行時間將連結至另一個類別中的預設訊息對應。|

下列宏會從父視窗直接「反映」訊息。 例如，控制項通常會將通知訊息傳送至其父視窗進行處理，但父視窗可以將訊息反映回控制項。

|巨集|描述|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|根據通知碼以及功能表項目、控制項或快速鍵的識別碼，將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|根據功能表項目、控制項或快速鍵的識別碼，將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|根據通知碼將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|根據控制項識別碼的連續範圍，將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|根據通知碼和連續的控制項識別碼範圍，將反映的 WM_COMMAND 訊息對應至處理常式函式。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|根據通知碼和控制項識別碼，將反映的 WM_NOTIFY 訊息對應至處理常式函式。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|根據控制項識別碼，將反映的 WM_NOTIFY 訊息對應至處理常式函數。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|根據通知碼將反映的 WM_NOTIFY 訊息對應至處理常式函式。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|根據控制項識別碼的連續範圍，將反映的 WM_NOTIFY 訊息對應至處理常式函式。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|根據通知碼和連續的控制項識別碼範圍，將反映的 WM_NOTIFY 訊息對應至處理常式函式。|

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

當 `CMyExtWindow` 物件收到 WM_PAINT 訊息時，會將訊息導向至以 `CMyExtWindow::OnPaint` 進行實際處理。 如果 `OnPaint` 指出訊息需要進一步處理，則會在中將訊息導向至預設的訊息對應 `CMyBaseWindow` 。

除了預設的訊息對應之外，您還可以使用 [ALT_MSG_MAP](#alt_msg_map)定義替代的訊息對應。 一律開始 BEGIN_MSG_MAP 的訊息對應。 然後，您可以宣告後續的替代訊息對應。 下列範例會顯示預設的訊息對應和一個替代訊息對應，其中每個都包含一個處理函式：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一個範例顯示兩個替代的訊息對應。 預設的訊息對應是空的。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 請注意，一律只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a> CHAIN_MSG_MAP_ALT

在訊息對應中定義專案。

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>參數

*theChainClass*<br/>
在包含訊息對應之基底類別的名稱。

*msgMapID*<br/>
在訊息對應識別碼。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_ALT 將訊息導向基類中的替代訊息對應。 您必須已使用 [ALT_MSG_MAP (msgMapID) ](#alt_msg_map)來宣告此替代訊息對應。 若要將訊息導向至基類的預設訊息對應 ([BEGIN_MSG_MAP](#begin_msg_map)) 宣告，請使用 CHAIN_MSG_MAP。 如需範例，請參閱 [CHAIN_MSG_MAP](#chain_msg_map)。

> [!NOTE]
> 一律開始 BEGIN_MSG_MAP 的訊息對應。 然後，您可以使用 ALT_MSG_MAP 來宣告後續的替代訊息對應。 [END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 每個訊息對應都必須只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a> CHAIN_MSG_MAP_ALT_MEMBER

在訊息對應中定義專案。

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>參數

*theChainMember*<br/>
在包含訊息對應的資料成員名稱。

*msgMapID*<br/>
在訊息對應識別碼。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_ALT_MEMBER 將訊息導向至資料成員中的替代訊息對應。 您必須已使用 [ALT_MSG_MAP (msgMapID) ](#alt_msg_map)來宣告此替代訊息對應。 若要將訊息導向至資料成員的預設訊息對應 ([BEGIN_MSG_MAP](#begin_msg_map)) 宣告，請使用 CHAIN_MSG_MAP_MEMBER。 如需範例，請參閱 [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)。

> [!NOTE]
> 一律開始 BEGIN_MSG_MAP 的訊息對應。 然後，您可以使用 ALT_MSG_MAP 來宣告後續的替代訊息對應。 [END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 每個訊息對應都必須只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a> CHAIN_MSG_MAP

在訊息對應中定義專案。

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>參數

*theChainClass*<br/>
在包含訊息對應之基底類別的名稱。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP 將訊息導向至基類的預設訊息對應 (使用 [BEGIN_MSG_MAP](#begin_msg_map)) 宣告。 若要將訊息導向至基類的替代訊息對應 (使用 [ALT_MSG_MAP](#alt_msg_map)) 宣告，請使用 [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)。

> [!NOTE]
> 一律開始 BEGIN_MSG_MAP 的訊息對應。 然後，您可以使用 ALT_MSG_MAP 來宣告後續的替代訊息對應。 [END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 每個訊息對應都必須只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

此範例說明下列各項：

- 如果視窗程式使用的是 `CMyClass` 預設的訊息對應，且 `OnPaint` 未處理訊息，則會將訊息導向至 `CMyBaseClass` 預設的訊息對應以進行處理。

- 如果視窗程式使用中的第一個替代訊息對應 `CMyClass` ，則所有訊息都會導向至 `CMyBaseClass` 預設的訊息對應。

- 如果視窗程式使用的是 `CMyClass` 第二個替代訊息對應，且 `OnChar` 未處理訊息，則會將訊息導向中的指定替代訊息對應 `CMyBaseClass` 。 `CMyBaseClass` 必須已經使用 ALT_MSG_MAP (1) 宣告此訊息對應。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a> CHAIN_MSG_MAP_DYNAMIC

在訊息對應中定義專案。

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>參數

*dynaChainID*<br/>
在物件之訊息對應的唯一識別碼。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_DYNAMIC 會在執行時間將訊息導向至另一個物件中的預設訊息對應。 物件和它的訊息對應會與 *dynaChainID*相關聯，您可以透過 [CDynamicChain：： SetChainEntry](cdynamicchain-class.md#setchainentry)定義此物件。 您必須從衍生類別，才能 `CDynamicChain` 使用 CHAIN_MSG_MAP_DYNAMIC。 如需範例，請參閱 [CDynamicChain](../../atl/reference/cdynamicchain-class.md) 總覽。

> [!NOTE]
> 一律開始 [BEGIN_MSG_MAP](#begin_msg_map)的訊息對應。 然後，您可以使用 ALT_MSG_MAP 來宣告後續的替代訊息對應。 [END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 每個訊息對應都必須只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a> CHAIN_MSG_MAP_MEMBER

在訊息對應中定義專案。

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>參數

*theChainMember*<br/>
在包含訊息對應的資料成員名稱。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_MEMBER 將訊息導向至資料成員的預設訊息對應 (使用 [BEGIN_MSG_MAP](#begin_msg_map)) 宣告。 若要將訊息導向至資料成員的替代訊息對應 ([ALT_MSG_MAP](#alt_msg_map)) 宣告，請使用 [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)。

> [!NOTE]
> 一律開始 BEGIN_MSG_MAP 的訊息對應。 然後，您可以使用 ALT_MSG_MAP 來宣告後續的替代訊息對應。 [END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 每個訊息對應都必須只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

此範例說明下列各項：

- 如果視窗程式使用的是 `CMyClass` 預設的訊息對應，且 `OnPaint` 未處理訊息，則會將訊息導向至 `m_obj` 預設的訊息對應以進行處理。

- 如果視窗程式使用中的第一個替代訊息對應 `CMyClass` ，則所有訊息都會導向至 `m_obj` 預設的訊息對應。

- 如果視窗程式使用的是 `CMyClass` 第二個替代訊息對應，且 `OnChar` 未處理訊息，則會將訊息導向至指定的替代訊息對應 `m_obj` 。 類別 `CMyContainedClass` 必須已使用 ALT_MSG_MAP (1) 宣告此訊息對應。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="command_code_handler"></a><a name="command_code_handler"></a> COMMAND_CODE_HANDLER

類似于 [COMMAND_HANDLER](#command_handler)，但只會根據通知碼對應 [WM_COMMAND](/windows/win32/menurc/wm-command) 訊息。

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>參數

*code*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="command_handler"></a><a name="command_handler"></a> COMMAND_HANDLER

在訊息對應中定義專案。

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>參數

*id*<br/>
在功能表項目、控制項或快速鍵的識別碼。

*code*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="remarks"></a>備註

COMMAND_HANDLER 會根據通知碼和控制項識別碼，將 [WM_COMMAND](/windows/win32/menurc/wm-command) 訊息對應到指定的處理常式函式。 例如：

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

COMMAND_HANDLER 宏中指定的任何函數必須定義如下：

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

在呼叫之前，訊息對應會將設定 `bHandled` 為 TRUE `CommandHandler` 。 如果 `CommandHandler` 未完全處理訊息，則應設 `bHandled` 為 FALSE，表示訊息需要進一步處理。

> [!NOTE]
> 一律開始 [BEGIN_MSG_MAP](#begin_msg_map)的訊息對應。 然後，您可以使用 [ALT_MSG_MAP](#alt_msg_map)來宣告後續的替代訊息對應。 [END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 每個訊息對應都必須只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

除了 COMMAND_HANDLER 之外，您還可以使用 [MESSAGE_HANDLER](#message_handler) 來對應 WM_COMMAND 訊息，而不考慮識別碼或程式碼。 在此情況下， `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` 會將所有 WM_COMMAND 訊息導向至 `OnHandlerFunction` 。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="command_id_handler"></a><a name="command_id_handler"></a> COMMAND_ID_HANDLER

類似于 [COMMAND_HANDLER](#command_handler)，但是只會根據功能表項目、控制項或快速鍵的識別碼來對應 [WM_COMMAND](/windows/win32/menurc/wm-command) 訊息。

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>參數

*id*<br/>
在傳送訊息之功能表項目、控制項或快速鍵的識別碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a> COMMAND_RANGE_CODE_HANDLER

類似于 [COMMAND_RANGE_HANDLER](#command_range_handler)，但會將具有特定通知碼的訊息，從某個範圍的控制項 [WM_COMMAND](/windows/win32/menurc/wm-command) 對應至單一處理程式函式。

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>參數

*idFirst*<br/>
在標記連續控制項識別碼範圍的開頭。

*idLast*<br/>
在標記連續控制項識別碼範圍的結尾。

*code*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="remarks"></a>備註

此範圍是以傳送訊息之功能表項目、控制項或快速鍵的識別碼為基礎。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="command_range_handler"></a><a name="command_range_handler"></a> COMMAND_RANGE_HANDLER

類似于 [COMMAND_HANDLER](#command_handler)，但會將 [WM_COMMAND](/windows/win32/menurc/wm-command) 的訊息從某個控制項範圍對應到單一處理程式函式。

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>參數

*idFirst*<br/>
在標記連續控制項識別碼範圍的開頭。

*idLast*<br/>
在標記連續控制項識別碼範圍的結尾。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="remarks"></a>備註

此範圍是以傳送訊息之功能表項目、控制項或快速鍵的識別碼為基礎。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a> DECLARE_EMPTY_MSG_MAP

宣告空白的訊息對應。

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>備註

DECLARE_EMPTY_MSG_MAP 是一個方便的宏，會呼叫宏 [BEGIN_MSG_MAP](#begin_msg_map) 和 [END_MSG_MAP](#end_msg_map) 以建立空的訊息對應：

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a> DEFAULT_REFLECTION_HANDLER

提供子視窗的預設處理常式， (控制項) 將接收反映的訊息;處理常式會正確地將未處理的訊息傳遞至 `DefWindowProc` 。

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="end_msg_map"></a><a name="end_msg_map"></a> END_MSG_MAP

標記訊息對應的結尾。

```
END_MSG_MAP()
```

### <a name="remarks"></a>備註

請一律使用 [BEGIN_MSG_MAP](#begin_msg_map) 宏來標記訊息對應的開頭。 使用 [ALT_MSG_MAP](#alt_msg_map) 來宣告後續的替代訊息對應。

請注意，一律只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

下列範例會顯示預設的訊息對應和一個替代訊息對應，其中每個都包含一個處理函式：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一個範例顯示兩個替代的訊息對應。 預設的訊息對應是空的。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="forward_notifications"></a><a name="forward_notifications"></a> FORWARD_NOTIFICATIONS

將通知訊息轉送至父視窗。

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>備註

指定此宏做為訊息對應的一部分。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="message_handler"></a><a name="message_handler"></a> MESSAGE_HANDLER

在訊息對應中定義專案。

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>參數

*msg*<br/>
在Windows 訊息。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="remarks"></a>備註

MESSAGE_HANDLER 將 Windows 訊息對應到指定的處理常式函數。

MESSAGE_HANDLER 宏中指定的任何函數必須定義如下：

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

在呼叫之前，訊息對應會將設定 `bHandled` 為 TRUE `MessageHandler` 。 如果 `MessageHandler` 未完全處理訊息，則應設 `bHandled` 為 FALSE，表示訊息需要進一步處理。

> [!NOTE]
> 一律開始 [BEGIN_MSG_MAP](#begin_msg_map)的訊息對應。 然後，您可以使用 [ALT_MSG_MAP](#alt_msg_map)來宣告後續的替代訊息對應。 [END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 每個訊息對應都必須只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

除了 MESSAGE_HANDLER 之外，您還可以使用 [COMMAND_HANDLER](#command_handler) 和 [NOTIFY_HANDLER](#notify_handler) 分別對應 [WM_COMMAND](/windows/win32/menurc/wm-command) 和 [WM_NOTIFY](/windows/win32/controls/wm-notify) 訊息。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="message_range_handler"></a><a name="message_range_handler"></a> MESSAGE_RANGE_HANDLER

類似于 [MESSAGE_HANDLER](#message_handler)，但會將 Windows 訊息範圍對應至單一處理程式函式。

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>參數

*msgFirst*<br/>
在標記連續訊息範圍的開頭。

*msgLast*<br/>
在標記連續訊息範圍的結尾。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a> NOTIFY_CODE_HANDLER

類似于 [NOTIFY_HANDLER](#notify_handler)，但只會根據通知碼對應 [WM_NOTIFY](/windows/win32/controls/wm-notify) 訊息。

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>參數

*cd*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="notify_handler"></a><a name="notify_handler"></a> NOTIFY_HANDLER

在訊息對應中定義專案。

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>參數

*id*<br/>
在傳送訊息之控制項的識別碼。

*cd*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="remarks"></a>備註

NOTIFY_HANDLER 會根據通知碼和控制項識別碼，將 [WM_NOTIFY](/windows/win32/controls/wm-notify) 訊息對應到指定的處理常式函式。

NOTIFY_HANDLER 宏中指定的任何函數必須定義如下：

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

在呼叫之前，訊息對應會將設定 `bHandled` 為 TRUE `NotifyHandler` 。 如果 `NotifyHandler` 未完全處理訊息，則應設 `bHandled` 為 FALSE，表示訊息需要進一步處理。

> [!NOTE]
> 一律開始 [BEGIN_MSG_MAP](#begin_msg_map)的訊息對應。 然後，您可以使用 [ALT_MSG_MAP](#alt_msg_map)來宣告後續的替代訊息對應。 [END_MSG_MAP](#end_msg_map)宏會標示訊息對應的結尾。 每個訊息對應都必須只有一個 BEGIN_MSG_MAP 的實例和 END_MSG_MAP。

除了 NOTIFY_HANDLER 之外，您還可以使用 [MESSAGE_HANDLER](#message_handler) 來對應 WM_NOTIFY 訊息，而不考慮識別碼或程式碼。 在此情況下， `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` 會將所有 WM_NOTIFY 訊息導向至 `OnHandlerFunction` 。

如需在 ATL 中使用訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a> NOTIFY_ID_HANDLER

類似于 [NOTIFY_HANDLER](#notify_handler)，但是只會根據控制項識別碼對應 [WM_NOTIFY](/windows/win32/controls/wm-notify) 訊息。

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>參數

*id*<br/>
在傳送訊息之控制項的識別碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a> NOTIFY_RANGE_CODE_HANDLER

類似于 [NOTIFY_RANGE_HANDLER](#notify_range_handler)，但會將具有特定通知碼的訊息，從某個範圍的控制項 [WM_NOTIFY](/windows/win32/controls/wm-notify) 對應至單一處理程式函式。

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
在標記連續控制項識別碼範圍的開頭。

*idLast*<br/>
在標記連續控制項識別碼範圍的結尾。

*cd*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="remarks"></a>備註

此範圍是以傳送訊息之控制項的識別碼為基礎。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a> NOTIFY_RANGE_HANDLER

類似于 [NOTIFY_HANDLER](#notify_handler)，但會將 [WM_NOTIFY](/windows/win32/controls/wm-notify) 的訊息從某個控制項範圍對應到單一處理程式函式。

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
在標記連續控制項識別碼範圍的開頭。

*idLast*<br/>
在標記連續控制項識別碼範圍的結尾。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="remarks"></a>備註

此範圍是以傳送訊息之控制項的識別碼為基礎。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a> REFLECT_NOTIFICATIONS

會將通知訊息反映回子視窗， (控制傳送這些訊息的) 。

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>備註

指定此宏做為父視窗的訊息對應的一部分。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a> REFLECTED_COMMAND_CODE_HANDLER

類似于 [COMMAND_CODE_HANDLER](#command_code_handler)，但是會對應從父視窗反映的命令。

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>參數

*code*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a> REFLECTED_COMMAND_HANDLER

類似于 [COMMAND_HANDLER](#command_handler)，但是會對應從父視窗反映的命令。

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>參數

*id*<br/>
在功能表項目、控制項或快速鍵的識別碼。

*code*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a> REFLECTED_COMMAND_ID_HANDLER

類似于 [COMMAND_ID_HANDLER](#command_id_handler)，但是會對應從父視窗反映的命令。

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>參數

*id*<br/>
在功能表項目、控制項或快速鍵的識別碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a> REFLECTED_COMMAND_RANGE_CODE_HANDLER

類似于 [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)，但是會對應從父視窗反映的命令。

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
在標記連續控制項識別碼範圍的開頭。

*idLast*<br/>
在標記連續控制項識別碼範圍的結尾。

*code*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a> REFLECTED_COMMAND_RANGE_HANDLER

類似于 [COMMAND_RANGE_HANDLER](#command_range_handler)，但是會對應從父視窗反映的命令。

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
在標記連續控制項識別碼範圍的開頭。

*idLast*<br/>
在標記連續控制項識別碼範圍的結尾。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a> REFLECTED_NOTIFY_CODE_HANDLER

類似于 [NOTIFY_CODE_HANDLER](#notify_code_handler)，但對應的通知會反映自父視窗。

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>參數

*cd*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a> REFLECTED_NOTIFY_HANDLER

類似于 [NOTIFY_HANDLER](#notify_handler)，但對應的通知會反映自父視窗。

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>參數

*id*<br/>
在功能表項目、控制項或快速鍵的識別碼。

*cd*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a> REFLECTED_NOTIFY_ID_HANDLER

類似于 [NOTIFY_ID_HANDLER](#notify_id_handler)，但對應的通知會反映自父視窗。

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>參數

*id*<br/>
在功能表項目、控制項或快速鍵的識別碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a> REFLECTED_NOTIFY_RANGE_CODE_HANDLER

類似于 [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)，但對應的通知會反映自父視窗。

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
在標記連續控制項識別碼範圍的開頭。

*idLast*<br/>
在標記連續控制項識別碼範圍的結尾。

*cd*<br/>
在通知碼。

*func*<br/>
在訊息處理常式函數的名稱。

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a> REFLECTED_NOTIFY_RANGE_HANDLER

類似于 [NOTIFY_RANGE_HANDLER](#notify_range_handler)，但對應的通知會反映自父視窗。

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
在標記連續控制項識別碼範圍的開頭。

*idLast*<br/>
在標記連續控制項識別碼範圍的結尾。

*func*<br/>
在訊息處理常式函數的名稱。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
