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
ms.openlocfilehash: 157812fa6625869c86dd8a27156a2970a3dc8d4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326221"
---
# <a name="message-map-macros-atl"></a>訊息對應巨集 (ATL)

這些宏定義消息映射和條目。

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|標記備用消息映射的開頭。|
|[BEGIN_MSG_MAP](#begin_msg_map)|標記預設消息映射的開頭。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|鏈到基類中的備用消息映射。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|鏈到類的數據成員中的備用消息映射。|
|[CHAIN_MSG_MAP](#chain_msg_map)|鏈到基類中的預設消息映射。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|在運行時將消息映射鏈到另一個類中的消息映射。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|鏈到類的數據成員中的預設消息映射。|
|[COMMAND_CODE_HANDLER](#command_code_handler)|根據通知代碼將WM_COMMAND消息映射到處理程式函數。|
|[COMMAND_HANDLER](#command_handler)|根據通知代碼和功能表項、控制件或快捷鍵的標識符將WM_COMMAND消息映射到處理程式函數。|
|[COMMAND_ID_HANDLER](#command_id_handler)|根據功能表項、控制項或快捷鍵的標識符將WM_COMMAND消息映射到處理程式函數。|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|根據通知代碼和連續的控制標識符範圍將WM_COMMAND消息映射到處理程式函數。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|根據連續的控制標識符範圍將WM_COMMAND消息映射到處理程式函數。|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|實現空消息映射。|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|為未以其他方式處理的反射消息提供默認處理程式。|
|[END_MSG_MAP](#end_msg_map)|標記消息映射的末尾。|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|將通知消息轉發到父視窗。|
|[MESSAGE_HANDLER](#message_handler)|將 Windows 消息映射到處理程式函數。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|將連續範圍的 Windows 消息映射到處理程式函數。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|根據通知代碼將WM_NOTIFY消息映射到處理程式函數。|
|[NOTIFY_HANDLER](#notify_handler)|根據通知代碼和控制標識碼將WM_NOTIFY消息映射到處理程式函數。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|根據控制項識別碼將WM_NOTIFY消息映射到處理程式函數。|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|根據通知代碼和連續的控制標識符範圍將WM_NOTIFY消息映射到處理程式函數。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|根據連續的控制標識符範圍將WM_NOTIFY消息映射到處理程式函數。|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|將通知消息反射回發送通知的消息。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|根據通知代碼將反射WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|根據通知代碼和功能表項、控制項或快捷鍵的標識符將反映WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|根據功能表項、控件或快速鍵的標識符將反射WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|根據通知代碼和連續的控制標識符範圍將反映WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|根據連續的控制標識符範圍將反射WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|根據通知代碼將反射WM_NOTIFY消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|根據通知代碼和控制標識符將反射WM_NOTIFY消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|根據控件識別碼將反射WM_NOTIFY消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|根據通知代碼和連續的控制標識符範圍將反射WM_NOTIFY消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|根據連續的控制標識符範圍將反映WM_NOTIFY消息映射到處理程式函數。|

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a>ALT_MSG_MAP

標記備用消息映射的開頭。

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>參數

*msgMapID*<br/>
[在]消息映射標識碼。

### <a name="remarks"></a>備註

ATL 通過數字標識每個消息映射。 默認消息映射(使用BEGIN_MSG_MAP宏聲明)由 0 標識。 *msgMapID*標識了備用消息映射。

消息對應用於處理發送到視窗的消息。 例如[,CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)允許您在包含物件中指定消息映射的標識符。 [然後,CContainedWindow:windowProc](ccontainedwindowt-class.md#windowproc)使用此消息映射將包含的視窗的消息定向到相應的處理程式函數或其他消息映射。 有關聲明處理程式函數的巨集清單,請參閱[BEGIN_MSG_MAP](#begin_msg_map)。

始終以BEGIN_MSG_MAP開始消息映射。 然後,您可以聲明後續的備用消息映射。

[END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 請注意,始終有一個BEGIN_MSG_MAP和END_MSG_MAP實例。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

下面的範例顯示預設訊息對應和一個備用訊息映射,每個訊息映射包含處理程式函數:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一個示例顯示兩個備用消息映射。 默認消息映射為空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a>BEGIN_MSG_MAP

標記預設消息映射的開頭。

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
[在]包含消息映射的類的名稱。

### <a name="remarks"></a>備註

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc)使用預設消息映射來處理發送到視窗的消息。 消息映射將消息定向到相應的處理程式函數或其他消息映射。

以下宏將消息映射到處理程式函數。 此函數必須在*類*中定義。

|巨集|描述|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|將 Windows 消息映射到處理程式函數。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|將連續範圍的 Windows 消息映射到處理程式函數。|
|[COMMAND_HANDLER](#command_handler)|根據通知代碼和功能表項、控制件或快捷鍵的標識符將WM_COMMAND消息映射到處理程式函數。|
|[COMMAND_ID_HANDLER](#command_id_handler)|根據功能表項、控制項或快捷鍵的標識符將WM_COMMAND消息映射到處理程式函數。|
|[COMMAND_CODE_HANDLER](#command_handler)|根據通知代碼將WM_COMMAND消息映射到處理程式函數。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|根據功能表項、控制項或快捷鍵的標識符將WM_COMMAND消息的連續範圍映射到處理程式函數。|
|[NOTIFY_HANDLER](#notify_handler)|根據通知代碼和控制標識碼將WM_NOTIFY消息映射到處理程式函數。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|根據控制項識別碼將WM_NOTIFY消息映射到處理程式函數。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|根據通知代碼將WM_NOTIFY消息映射到處理程式函數。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|根據控制項識別碼將WM_NOTIFY訊息的連續範圍映射到處理程式函數。|

以下宏將消息定向到另一個消息映射。 此過程稱為"連結"。

|巨集|描述|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|鏈到基類中的預設消息映射。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|鏈到類的數據成員中的預設消息映射。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|鏈到基類中的備用消息映射。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|鏈到類的數據成員中的備用消息映射。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|在運行時將預設消息映射鏈到另一個類中。|

以下宏直接從父視窗"反射"消息。 例如,控件通常向其父視窗發送通知消息進行處理,但父視窗可以將消息反射回控件。

|巨集|描述|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|根據通知代碼和功能表項、控制項或快捷鍵的標識符將反映WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|根據功能表項、控件或快速鍵的標識符將反射WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|根據通知代碼將反射WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|根據連續的控制標識符範圍將反射WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|根據通知代碼和連續的控制標識符範圍將反映WM_COMMAND消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|根據通知代碼和控制標識符將反射WM_NOTIFY消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|根據控件識別碼將反射WM_NOTIFY消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|根據通知代碼將反射WM_NOTIFY消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|根據連續的控制標識符範圍將反映WM_NOTIFY消息映射到處理程式函數。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|根據通知代碼和連續的控制標識符範圍將反射WM_NOTIFY消息映射到處理程式函數。|

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

當`CMyExtWindow`物件收到WM_PAINT消息時,消息將定向`CMyExtWindow::OnPaint`到 進行實際處理。 如果`OnPaint`指示郵件需要進一步處理,則消息將定向到`CMyBaseWindow`中的 默認消息映射。

除了預設消息映射之外,還可以使用[ALT_MSG_MAP](#alt_msg_map)定義備用消息映射。 始終以BEGIN_MSG_MAP開始消息映射。 然後,您可以聲明後續的備用消息映射。 下面的範例顯示預設訊息對應和一個備用訊息映射,每個訊息映射包含處理程式函數:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一個示例顯示兩個備用消息映射。 默認消息映射為空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 請注意,始終有一個BEGIN_MSG_MAP和END_MSG_MAP實例。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

定義消息映射中的條目。

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>參數

*鏈類*<br/>
[在]包含消息映射的基類的名稱。

*msgMapID*<br/>
[在]消息映射標識碼。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_ALT將消息定向到基類中的備用消息映射。 您必須已使用[ALT_MSG_MAP (msgMapID)](#alt_msg_map)聲明此備用消息映射。 要將消息定向到基類的預設消息映射(使用[BEGIN_MSG_MAP](#begin_msg_map)聲明),請使用CHAIN_MSG_MAP。 例如,請參閱[CHAIN_MSG_MAP](#chain_msg_map)。

> [!NOTE]
> 始終以BEGIN_MSG_MAP開始消息映射。 然後,您可以使用ALT_MSG_MAP聲明後續備用消息映射。 [END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 每個消息映射必須具有BEGIN_MSG_MAP和END_MSG_MAP的一個實例。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER

定義消息映射中的條目。

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>參數

*鏈會員*<br/>
[在]包含消息映射的數據成員的名稱。

*msgMapID*<br/>
[在]消息映射標識碼。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_ALT_MEMBER將消息定向到數據成員中的備用消息映射。 您必須已使用[ALT_MSG_MAP (msgMapID)](#alt_msg_map)聲明此備用消息映射。 要將消息定向到數據成員的預設消息映射(使用[BEGIN_MSG_MAP](#begin_msg_map)聲明),請使用CHAIN_MSG_MAP_MEMBER。 例如,請參閱[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)。

> [!NOTE]
> 始終以BEGIN_MSG_MAP開始消息映射。 然後,您可以使用ALT_MSG_MAP聲明後續備用消息映射。 [END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 每個消息映射必須具有BEGIN_MSG_MAP和END_MSG_MAP的一個實例。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a>CHAIN_MSG_MAP

定義消息映射中的條目。

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>參數

*鏈類*<br/>
[在]包含消息映射的基類的名稱。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP將消息定向到基類的預設消息映射(用[BEGIN_MSG_MAP](#begin_msg_map)聲明)。 要將訊息移射( 用[ALT_MSG_MAP](#alt_msg_map)宣告 ) , 請使用[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)。

> [!NOTE]
> 始終以BEGIN_MSG_MAP開始消息映射。 然後,您可以使用ALT_MSG_MAP聲明後續備用消息映射。 [END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 每個消息映射必須具有BEGIN_MSG_MAP和END_MSG_MAP的一個實例。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

此範例說明以下內容:

- 如果視窗過程使用`CMyClass`''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''' `OnPaint` `CMyBaseClass`

- 如果視窗過程使用`CMyClass`中 的第一個備用消息映射,則所有消息都`CMyBaseClass`定向 到 默認消息映射。

- 如果視窗過程使用`CMyClass`的第二個備用消息映射,`OnChar`並且不處理消息,則消息將定向到`CMyBaseClass`中的指定備用消息映射。 `CMyBaseClass`必須已用 ALT_MSG_MAP (1) 聲明此消息映射。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC

定義消息映射中的條目。

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>參數

*迪納鏈代碼*<br/>
[在]物件的消息對應的唯一標識符。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_DYNAMIC在運行時將消息定向到另一個對象的預設消息映射。 物件及其消息映射與*dynaChainID*相關聯,通過[CDynamicChain:setChainEntry](cdynamicchain-class.md#setchainentry)進行定義。 為了使用CHAIN_MSG_MAP_DYNAMIC,必須派生`CDynamicChain`類。 例如,請參閱[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概述。

> [!NOTE]
> 始終以[BEGIN_MSG_MAP](#begin_msg_map)開始消息映射。 然後,您可以使用ALT_MSG_MAP聲明後續備用消息映射。 [END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 每個消息映射必須具有BEGIN_MSG_MAP和END_MSG_MAP的一個實例。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER

定義消息映射中的條目。

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>參數

*鏈會員*<br/>
[在]包含消息映射的數據成員的名稱。

### <a name="remarks"></a>備註

CHAIN_MSG_MAP_MEMBER將消息定向到數據成員的預設消息映射(使用[BEGIN_MSG_MAP](#begin_msg_map)聲明)。 要將訊息移射為資料成員的備用訊息映射(用[ALT_MSG_MAP](#alt_msg_map)宣告),請使用[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)。

> [!NOTE]
> 始終以BEGIN_MSG_MAP開始消息映射。 然後,您可以使用ALT_MSG_MAP聲明後續備用消息映射。 [END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 每個消息映射必須具有BEGIN_MSG_MAP和END_MSG_MAP的一個實例。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

此範例說明以下內容:

- 如果視窗過程使用`CMyClass`''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''' `OnPaint` `m_obj`

- 如果視窗過程使用`CMyClass`中 的第一個備用消息映射,則所有消息都`m_obj`定向 到 默認消息映射。

- 如果視窗過程使用`CMyClass`的第二個備用消息映射,`OnChar`並且不處理消息,則消息將定向`m_obj`到 指定的備用消息映射。 類`CMyContainedClass`必須用ALT_MSG_MAP(1)聲明此消息映射。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="command_code_handler"></a><a name="command_code_handler"></a>COMMAND_CODE_HANDLER

與[COMMAND_HANDLER](#command_handler)類似 ,但僅根據通知代碼映射[WM_COMMAND](/windows/win32/menurc/wm-command)消息。

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>參數

*代碼*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="command_handler"></a><a name="command_handler"></a>COMMAND_HANDLER

定義消息映射中的條目。

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>參數

*id*<br/>
[在]選單項、控件或快捷鍵的標識符。

*代碼*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="remarks"></a>備註

COMMAND_HANDLER根據通知代碼和控制識別碼將[WM_COMMAND](/windows/win32/menurc/wm-command)消息映射到指定的處理程式函數。 例如：

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

COMMAND_HANDLER宏中指定的任何函數必須定義如下:

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

在呼叫之前`CommandHandler`,`bHandled`訊息映射集到 TRUE。 如果未`CommandHandler`完全處理消息,則應將其設置`bHandled`為 FALSE 以指示郵件需要進一步處理。

> [!NOTE]
> 始終以[BEGIN_MSG_MAP](#begin_msg_map)開始消息映射。 然後,您可以使用[ALT_MSG_MAP](#alt_msg_map)聲明後續備用消息映射。 [END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 每個消息映射必須具有BEGIN_MSG_MAP和END_MSG_MAP的一個實例。

除了COMMAND_HANDLER之外,您還可以使用[MESSAGE_HANDLER](#message_handler)來映射WM_COMMAND消息,而不考慮標識符或代碼。 在這種情況下,`MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)`將所有WM_COMMAND訊息定到`OnHandlerFunction`。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="command_id_handler"></a><a name="command_id_handler"></a>COMMAND_ID_HANDLER

與[COMMAND_HANDLER](#command_handler)類似,但僅根據菜單項、控件或快速鍵的標識符映射[WM_COMMAND](/windows/win32/menurc/wm-command)消息。

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>參數

*id*<br/>
[在]發送消息的功能表項、控制項或快捷鍵的標識碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER

與[COMMAND_RANGE_HANDLER](#command_range_handler)類似,但使用具有特定通知代碼[的消息WM_COMMAND](/windows/win32/menurc/wm-command)消息從一系列控件映射到單個處理程式函數。

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[在]標記連續控制標識符範圍的開始。

*idLast*<br/>
[在]標記連續控制標識符範圍的結束。

*代碼*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="remarks"></a>備註

此範圍基於發送消息的功能表項、控制項或快捷鍵的標識符。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="command_range_handler"></a><a name="command_range_handler"></a>COMMAND_RANGE_HANDLER

與[COMMAND_HANDLER](#command_handler)類似,但將[WM_COMMAND](/windows/win32/menurc/wm-command)消息從一系列控件映射到單個處理程式函數。

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[在]標記連續控制標識符範圍的開始。

*idLast*<br/>
[在]標記連續控制標識符範圍的結束。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="remarks"></a>備註

此範圍基於發送消息的功能表項、控制項或快捷鍵的標識符。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

聲明空消息映射。

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>備註

DECLARE_EMPTY_MSG_MAP是一個方便的宏,用於調用宏[BEGIN_MSG_MAP,](#begin_msg_map)[並END_MSG_MAP](#end_msg_map)創建空消息映射:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

為將接收反射消息的子視窗(控制件)提供默認處理程式;處理程式將正確將未處理的訊息傳遞`DefWindowProc`。

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="end_msg_map"></a><a name="end_msg_map"></a>END_MSG_MAP

標記消息映射的末尾。

```
END_MSG_MAP()
```

### <a name="remarks"></a>備註

始終使用[BEGIN_MSG_MAP](#begin_msg_map)宏來標記消息映射的開頭。 使用[ALT_MSG_MAP](#alt_msg_map)聲明後續備用消息映射。

請注意,始終有一個BEGIN_MSG_MAP和END_MSG_MAP實例。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

下面的範例顯示預設訊息對應和一個備用訊息映射,每個訊息映射包含處理程式函數:

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一個示例顯示兩個備用消息映射。 默認消息映射為空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="forward_notifications"></a><a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

將通知消息轉發到父視窗。

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>備註

將此宏指定為消息映射的一部分。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="message_handler"></a><a name="message_handler"></a>MESSAGE_HANDLER

定義消息映射中的條目。

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>參數

*味精*<br/>
[在]「視窗」訊息。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="remarks"></a>備註

MESSAGE_HANDLER將 Windows 消息映射到指定的處理程式函數。

MESSAGE_HANDLER宏中指定的任何函數必須定義如下:

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

在呼叫之前`MessageHandler`,`bHandled`訊息映射集到 TRUE。 如果未`MessageHandler`完全處理消息,則應將其設置`bHandled`為 FALSE 以指示郵件需要進一步處理。

> [!NOTE]
> 始終以[BEGIN_MSG_MAP](#begin_msg_map)開始消息映射。 然後,您可以使用[ALT_MSG_MAP](#alt_msg_map)聲明後續備用消息映射。 [END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 每個消息映射必須具有BEGIN_MSG_MAP和END_MSG_MAP的一個實例。

除了MESSAGE_HANDLER之外,您還可以使用[COMMAND_HANDLER](#command_handler)和[NOTIFY_HANDLER](#notify_handler)分別映射[WM_COMMAND](/windows/win32/menurc/wm-command)和[WM_NOTIFY](/windows/win32/controls/wm-notify)消息。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="message_range_handler"></a><a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER

與[MESSAGE_HANDLER](#message_handler)類似,但將一系列 Windows 消息映射到單個處理程式函數。

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>參數

*msgFirst*<br/>
[在]標記連續消息範圍的開始。

*msgLast*<br/>
[在]標記連續消息範圍的結束。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER

與[NOTIFY_HANDLER](#notify_handler)類似,但僅根據通知代碼映射[WM_NOTIFY](/windows/win32/controls/wm-notify)消息。

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>參數

*cd*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="notify_handler"></a><a name="notify_handler"></a>NOTIFY_HANDLER

定義消息映射中的條目。

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[在]發送消息的控制項的標識碼。

*cd*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="remarks"></a>備註

NOTIFY_HANDLER根據通知代碼和控制識別碼將[WM_NOTIFY](/windows/win32/controls/wm-notify)消息映射到指定的處理程式函數。

NOTIFY_HANDLER宏中指定的任何函數必須定義如下:

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

在呼叫之前`NotifyHandler`,`bHandled`訊息映射集到 TRUE。 如果未`NotifyHandler`完全處理消息,則應將其設置`bHandled`為 FALSE 以指示郵件需要進一步處理。

> [!NOTE]
> 始終以[BEGIN_MSG_MAP](#begin_msg_map)開始消息映射。 然後,您可以使用[ALT_MSG_MAP](#alt_msg_map)聲明後續備用消息映射。 [END_MSG_MAP](#end_msg_map)宏標記消息映射的結尾。 每個消息映射必須具有BEGIN_MSG_MAP和END_MSG_MAP的一個實例。

除了NOTIFY_HANDLER之外,您還可以使用[MESSAGE_HANDLER](#message_handler)映射WM_NOTIFY消息,而不考慮標識符或代碼。 在這種情況下,`MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)`將所有WM_NOTIFY訊息定到`OnHandlerFunction`。

有關在 ATL 中使用訊息映射的詳細資訊,請參閱[訊息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a>NOTIFY_ID_HANDLER

與[NOTIFY_HANDLER](#notify_handler)類似,但僅根據控制項識別符映射[WM_NOTIFY](/windows/win32/controls/wm-notify)消息。

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[在]發送消息的控制項的標識碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER

與[NOTIFY_RANGE_HANDLER](#notify_range_handler)類似 ,但將具有特定通知代碼[WM_NOTIFY](/windows/win32/controls/wm-notify)消息從一系列控件映射到單個處理程式函數。

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[在]標記連續控制標識符範圍的開始。

*idLast*<br/>
[在]標記連續控制標識符範圍的結束。

*cd*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="remarks"></a>備註

此範圍基於發送消息的控制項的標識碼。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER

與[NOTIFY_HANDLER](#notify_handler)類似,但將[WM_NOTIFY](/windows/win32/controls/wm-notify)消息從一系列控件映射到單個處理程式函數。

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[在]標記連續控制標識符範圍的開始。

*idLast*<br/>
[在]標記連續控制標識符範圍的結束。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="remarks"></a>備註

此範圍基於發送消息的控制項的標識碼。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

將通知消息反射回發送它們的子視窗(控件)。

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>備註

將此宏指定為父視窗的消息映射的一部分。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER

與[COMMAND_CODE_HANDLER](#command_code_handler)類似,但映射從父視窗反射的命令。

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>參數

*代碼*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER

與[COMMAND_HANDLER](#command_handler)類似,但映射從父視窗反射的命令。

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[在]選單項、控件或快捷鍵的標識符。

*代碼*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER

與[COMMAND_ID_HANDLER](#command_id_handler)類似,但映射從父視窗反射的命令。

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[在]選單項、控件或快捷鍵的標識符。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER

與[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)類似,但映射從父視窗反射的命令。

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[在]標記連續控制標識符範圍的開始。

*idLast*<br/>
[在]標記連續控制標識符範圍的結束。

*代碼*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER

與[COMMAND_RANGE_HANDLER](#command_range_handler)類似,但映射從父視窗反射的命令。

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[在]標記連續控制標識符範圍的開始。

*idLast*<br/>
[在]標記連續控制標識符範圍的結束。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER

與[NOTIFY_CODE_HANDLER](#notify_code_handler)類似,但映射從父視窗反映的通知。

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>參數

*cd*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

與[NOTIFY_HANDLER](#notify_handler)類似,但映射從父視窗反映的通知。

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[在]選單項、控件或快捷鍵的標識符。

*cd*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER

與[NOTIFY_ID_HANDLER](#notify_id_handler)類似,但映射從父視窗反映的通知。

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>參數

*id*<br/>
[在]選單項、控件或快捷鍵的標識符。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER

與[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)類似,但映射從父視窗反映的通知。

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[在]標記連續控制標識符範圍的開始。

*idLast*<br/>
[在]標記連續控制標識符範圍的結束。

*cd*<br/>
[在]通知代碼。

*func*<br/>
[在]消息處理程式函數的名稱。

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER

與[NOTIFY_RANGE_HANDLER](#notify_range_handler)類似,但映射從父視窗反映的通知。

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>參數

*idFirst*<br/>
[在]標記連續控制標識符範圍的開始。

*idLast*<br/>
[在]標記連續控制標識符範圍的結束。

*func*<br/>
[在]消息處理程式函數的名稱。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
