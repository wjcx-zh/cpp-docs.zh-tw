---
title: CDynamicChain 類別
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 4b68198c17d7bd030b88bc78ad4de1367c914703
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258997"
---
# <a name="cdynamicchain-class"></a>CDynamicChain 類別

這個類別提供支援動態鏈結的訊息對應的方法。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CDynamicChain
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|建構函式。|
|[CDynamicChain:: ~ CDynamicChain](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|會將導向至另一個物件的訊息對應的 Windows 訊息。|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|從集合中移除訊息的對應項目。|
|[CDynamicChain::SetChainEntry](#setchainentry)|將訊息對應項目加入至集合，或修改現有的項目。|

## <a name="remarks"></a>備註

`CDynamicChain` 管理訊息對應，讓 Windows 訊息導向，在執行階段，加入另一個物件的訊息對應的集合。

若要新增支援的訊息對應的動態鏈結，執行下列作業：

- 衍生您的類別，從`CDynamicChain`。 在訊息對應中，指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)鏈結至另一個物件的預設訊息對應巨集。

- 您想要鏈結至從每個的類別的衍生[CMessageMap](../../atl/reference/cmessagemap-class.md)。 `CMessageMap` 可讓物件公開給其他物件其訊息對應。

- 呼叫`CDynamicChain::SetChainEntry`以找出哪些物件和訊息對應您想要鏈結。

例如，假設您的類別定義，如下所示：

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

用戶端接著呼叫`CMyWindow::SetChainEntry`:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

何處`chainedObj`是鏈結的物件，而且是衍生自的類別的執行個體`CMessageMap`。 現在，如果`myCtl`收到的訊息，不會處理`OnPaint`或是`OnSetFocus`，視窗程序會指示訊息`chainedObj`的預設訊息對應。

如需訊息對應鏈結的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)文章 < ATL 視窗類別 >。

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="callchain"></a>  CDynamicChain::CallChain

Windows 會將訊息導向到另一個物件的訊息對應。

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

*dwChainID*<br/>
[in]鏈結的物件和其訊息對應相關聯的唯一識別碼。

*hWnd*<br/>
[in]接收訊息的視窗控制代碼。

*uMsg*<br/>
[in]傳送至視窗的訊息。

*wParam*<br/>
[in]其他特定訊息資訊。

*lParam*<br/>
[in]其他特定訊息資訊。

*lResult*<br/>
[out]訊息處理的結果。

### <a name="return-value"></a>傳回值

如果已完全處理訊息，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

視窗程序來叫用`CallChain`，您必須指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)訊息對應中的巨集。 如需範例，請參閱[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概觀。

`CallChain` 需要由先前呼叫[SetChainEntry](#setchainentry)建立關聯*dwChainID*物件，其訊息對應值。

##  <a name="cdynamicchain"></a>  CDynamicChain::CDynamicChain

建構函式。

```
CDynamicChain();
```

##  <a name="dtor"></a>  CDynamicChain:: ~ CDynamicChain

解構函式。

```
~CDynamicChain();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="removechainentry"></a>  CDynamicChain::RemoveChainEntry

從集合中移除指定的訊息對應。

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>參數

*dwChainID*<br/>
[in]鏈結的物件和其訊息對應相關聯的唯一識別碼。 您原本定義此值，透過呼叫[SetChainEntry](#setchainentry)。

### <a name="return-value"></a>傳回值

從集合中成功移除的訊息對應，其值為 TRUE。 否則為 FALSE。

##  <a name="setchainentry"></a>  CDynamicChain::SetChainEntry

將指定的訊息對應加入至集合。

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>參數

*dwChainID*<br/>
[in]鏈結的物件和其訊息對應相關聯的唯一識別碼。

*pObject*<br/>
[in]宣告訊息對應鏈結物件的指標。 這個物件必須衍生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[in]訊息對應中的鏈結的物件識別碼。 預設值為 0，用來識別宣告的預設訊息對應[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)。 若要指定替代的訊息對應，以宣告[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，傳遞`msgMapID`。

### <a name="return-value"></a>傳回值

訊息對應已成功新增至集合，其值為 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

如果*dwChainID*已經存在於集合中的值，取代其相關聯的物件和訊息對應*pObject*並*dwMsgMapID*分別。 否則，會加入新項目。

## <a name="see-also"></a>另請參閱

[CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
