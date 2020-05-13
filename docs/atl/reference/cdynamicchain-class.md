---
title: CDynamic鏈類
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
ms.openlocfilehash: 4a72b3b4308ed83dfdc4a2895a04d1fe9a177ce5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327025"
---
# <a name="cdynamicchain-class"></a>CDynamic鏈類

此類提供支援消息映射動態連結的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CDynamicChain
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C動態鏈:C動態鏈](#cdynamicchain)|建構函式。|
|[C動態鏈:*C動態鏈](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDynamic鏈:呼叫鏈](#callchain)|將 Windows 消息定向到另一個物件的消息映射。|
|[CDynamic鏈::刪除鏈入口](#removechainentry)|從集合中刪除消息映射項目。|
|[CDynamic鏈::設置鏈入口](#setchainentry)|向集合添加消息映射條目或修改現有條目。|

## <a name="remarks"></a>備註

`CDynamicChain`管理消息對應的集合,使 Windows 消息在運行時定向到另一個物件的消息映射。

要新增對消息映射動態連結的支援,請執行以下操作:

- 從 派生`CDynamicChain`類從 。 在消息映射中,指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)宏以連結到另一個對象的預設消息映射。

- 派生要從[CMessageMap](../../atl/reference/cmessagemap-class.md)連結到的每個類。 `CMessageMap`允許物件將其消息映射公開給其他物件。

- 調用`CDynamicChain::SetChainEntry`以標識要連結到的物件和消息映射。

例如,假設您的類定義如下:

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

然後,用戶端呼叫`CMyWindow::SetChainEntry`:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

連結`chainedObj`物件的位置,是從 派生的類別的`CMessageMap`實體 。 現在,如果`myCtl`收到`OnPaint`或`OnSetFocus`未處理的消息,視窗過程將消息定向到`chainedObj`默認消息映射。

關於郵件映射連結的詳細資訊,請參考文章「ATL 視窗類別」[中 。](../../atl/message-maps-atl.md)

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="cdynamicchaincallchain"></a><a name="callchain"></a>CDynamic鏈:呼叫鏈

將 Windows 消息定向到另一個物件的消息映射。

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
[在]與連結物件及其消息映射關聯的唯一標識碼。

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

### <a name="return-value"></a>傳回值

如果消息已完全處理,則為 TRUE;如果消息已完全處理,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

要調用`CallChain`視窗過程,必須在消息映射中指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)宏。 例如,請參閱[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概述。

`CallChain`需要對[SetChainEntry](#setchainentry)進行以前的調用,才能將*dwChainID*值與物件及其消息映射相關聯。

## <a name="cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a>C動態鏈:C動態鏈

建構函式。

```
CDynamicChain();
```

## <a name="cdynamicchaincdynamicchain"></a><a name="dtor"></a>C動態鏈:*C動態鏈

解構函式。

```
~CDynamicChain();
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="cdynamicchainremovechainentry"></a><a name="removechainentry"></a>CDynamic鏈::刪除鏈入口

從集合中刪除指定的消息映射。

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>參數

*dwChainID*<br/>
[在]與連結物件及其消息映射關聯的唯一標識碼。 您最初透過調用[SetChainEntry](#setchainentry)來定義此值。

### <a name="return-value"></a>傳回值

如果消息映射從集合成功刪除,則為 TRUE。 否則，FALSE。

## <a name="cdynamicchainsetchainentry"></a><a name="setchainentry"></a>CDynamic鏈::設置鏈入口

將指定的消息映射添加到集合中。

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>參數

*dwChainID*<br/>
[在]與連結物件及其消息映射關聯的唯一標識碼。

*pObject*<br/>
[在]指向聲明消息映射的鏈條對象的指標。 此物件必須派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[在]連結物件中消息映射的標識符。 默認值為 0,它識別使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)聲明的預設消息映射。 要指定使用[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)宣告的備用`msgMapID`訊息映射 , 請透過 。

### <a name="return-value"></a>傳回值

如果消息映射已成功添加到集合中,則為 TRUE。 否則，FALSE。

### <a name="remarks"></a>備註

如果集合中已存在*dwChainID*值,則其關聯的物件和消息映射將分別替換為*pObject*和*dwMsgMapID。* 否則,將添加新條目。

## <a name="see-also"></a>另請參閱

[CWindowImpl 類別](../../atl/reference/cwindowimpl-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
