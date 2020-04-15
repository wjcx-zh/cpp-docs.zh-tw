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
ms.openlocfilehash: a822f36d6b6fd49301d8240324e27f0ad9ce52e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326714"
---
# <a name="cmessagemap-class"></a>CMessageMap 類別

此類允許物件的消息映射由另一個對象訪問。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMessageMap::P視窗訊息](#processwindowmessage)|訪問派生類中`CMessageMap`的消息映射。|

## <a name="remarks"></a>備註

`CMessageMap`是一個抽象基類,允許物件的消息映射被另一個對象訪問。 為了使物件公開其消息映射,其類必須派生自`CMessageMap`。

ATL`CMessageMap`用於支援包含的視窗和動態消息映射連結。 例如,任何包含[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)物件的類別都必須派`CMessageMap`生自 。 以下代碼取自[SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)範例。 以[CComControl,](../../atl/reference/ccomcontrol-class.md)`CAtlEdit`類別自動派`CMessageMap`生自 。

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

因為包含的視窗會在`m_EditCtrl`包含類別中使用訊息映射,`CAtlEdit`請選擇`CMessageMap`生自 。

有關訊息映射的詳細資訊,請參閱文章「ATL 視窗類別」中[的消息對應](../../atl/message-maps-atl.md)。

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a>CMessageMap::P視窗訊息

訪問*dwMsgMapID*在`CMessageMap`派生類中標識的消息映射。

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
[在]接收消息的視窗的句柄。

*烏姆斯格*<br/>
[在]發送到視窗的消息。

*wParam*<br/>
[在]其他特定於消息的資訊。

*lParam*<br/>
[在]其他特定於消息的資訊。

*lResult*<br/>
[出]消息處理的結果。

*dwMsgMapID*<br/>
[在]將處理消息的消息映射的標識符。 默認消息映射(使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)聲明)由 0 標識。 使用[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的替代訊息映`msgMapID`射由 識別 。

### <a name="return-value"></a>傳回值

如果消息已完全處理,則為 TRUE;如果消息已完全處理,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

由[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)物件的視窗過程或動態連結到消息映射的物件的視窗過程調用。

## <a name="see-also"></a>另請參閱

[CDynamic鏈類](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[類別概觀](../../atl/atl-class-overview.md)
