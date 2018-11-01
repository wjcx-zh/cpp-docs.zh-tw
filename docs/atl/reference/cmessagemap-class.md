---
title: CMessageMap 類別
ms.date: 11/04/2016
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
ms.openlocfilehash: 325851b75cef340fe5dcc762df54c40ded1ed704
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534078"
---
# <a name="cmessagemap-class"></a>CMessageMap 類別

這個類別可讓物件的訊息對應是由另一個物件的存取。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|存取中的訊息對應`CMessageMap`-衍生的類別。|

## <a name="remarks"></a>備註

`CMessageMap` 是抽象的基底類別，可讓物件的訊息對應至另一個物件來存取。 為了讓物件公開其訊息對應，其類別必須衍生自`CMessageMap`。

使用 ATL`CMessageMap`支援包含 windows 和動態的訊息對應鏈結。 例如，任何類別包含[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)物件必須衍生自`CMessageMap`。 下列程式碼取自[SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)範例。 透過[CComControl](../../atl/reference/ccomcontrol-class.md)，則`CAtlEdit`類別會自動衍生自`CMessageMap`。

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

因為自主的視窗中， `m_EditCtrl`，在包含的類別中，將訊息對應`CAtlEdit`衍生自`CMessageMap`。

如需訊息對應的詳細資訊，請參閱[訊息對應](../../atl/message-maps-atl.md)文章 < ATL 視窗類別 >。

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="processwindowmessage"></a>  CMessageMap::ProcessWindowMessage

存取所識別的訊息對應*dwMsgMapID*在`CMessageMap`-衍生的類別。

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

*dwMsgMapID*<br/>
[in]訊息對應會處理訊息的識別碼。 預設訊息對應中，以宣告[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，由 0。 替代訊息對應，以宣告[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，由`msgMapID`。

### <a name="return-value"></a>傳回值

如果訊息處理，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

呼叫的視窗程序[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)物件或物件的以動態方式鏈結至訊息對應。

## <a name="see-also"></a>另請參閱

[CDynamicChain 類別](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[類別概觀](../../atl/atl-class-overview.md)
