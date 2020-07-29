---
title: COleCmdUI 類別
ms.date: 07/24/2020
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
ms.openlocfilehash: c21d9b504656e6bba5ca693e57958743bb1b8309
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233206"
---
# <a name="colecmdui-class"></a>COleCmdUI 類別

實作 MFC 的方法以更新與應用程式 `IOleCommandTarget`驅動功能相關聯之使用者介面物件的狀態。

## <a name="syntax"></a>語法

```cpp
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|建構 `COleCmdUI` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleCmdUI：： Enable](#enable)|設定或清除 [啟用命令] 旗標。|
|[COleCmdUI：： SetCheck](#setcheck)|設定開啟/關閉切換命令的狀態。|
|[COleCmdUI：： SetText](#settext)|傳回命令的文字名稱或狀態字串。|

## <a name="remarks"></a>備註

在未啟用 DocObjects 的應用程式中，當使用者在應用程式中流覽功能表時，MFC 會處理 UPDATE_COMMAND_UI 通知。 每個通知都會提供一個可操作的[CCmdUI](../../mfc/reference/ccmdui-class.md)物件，以反映特定命令的狀態。 不過，當您的應用程式啟用 DocObjects 時，MFC 會處理 UPDATE_OLE_COMMAND_UI 通知並指派 `COleCmdUI` 物件。

`COleCmdUI`允許 DocObject 接收源自其容器的使用者介面（例如 FileNew、開啟、列印等等）的命令，並允許容器接收源自于 DocObject 之使用者介面的命令。 雖然 `IDispatch` 可用來分派相同的命令，但 `IOleCommandTarget` 提供更簡單的查詢和執行方式，因為它依賴一組標準的命令（通常不含引數），而且不會涉及任何型別資訊。 `COleCmdUI`可以用來啟用、更新及設定 DocObject 使用者介面命令的其他屬性。 當您想要叫用命令時，請呼叫[COleServerDoc：： OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)。

如需 DocObjects 的詳細資訊，請參閱[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>需求

**標頭：** afxdocob。h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI::COleCmdUI

構造 `COleCmdUI` 與特定使用者介面命令相關聯的物件。

```cpp
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>參數

*rgCmds*<br/>
與指定 GUID 相關聯的支援命令清單。 結構會將 `OLECMD` 命令與命令旗標產生關聯。

*cCmds*<br/>
*RgCmds*中的命令計數。

*pGroup*<br/>
識別一組命令之 GUID 的指標。

### <a name="remarks"></a>備註

`COleCmdUI`物件提供了程式設計介面，可用來更新 DocObject 的使用者介面物件，例如功能表項目或控制列按鈕。 使用者介面物件可以透過物件來啟用、停用、檢查和/或清除 `COleCmdUI` 。

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI：： Enable

呼叫此函式可將物件的命令旗標設定 `COleCmdUI` 為 OLECOMDF_ENABLED，這會告訴介面命令可供使用並啟用，或清除命令旗標。

```cpp
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>參數

*bOn*<br/>
指出是否 `COleCmdUI` 應啟用或停用與物件相關聯的命令。 非零值會啟用命令;0會停用命令。

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI：： SetCheck

呼叫此函式可設定 on/off 切換命令的狀態。

```cpp
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>參數

*nCheck*<br/>
值，決定要設定開啟/關閉切換命令的狀態。 值為：

|值|描述|
|-----------|-----------------|
|**1**|將命令設定為 on。|
|**2**|將命令設定為未定;無法判斷狀態，因為此命令的屬性位於相關選取專案的開啟和關閉狀態。|
|任何其他值|將命令設定為 off。|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI：： SetText

呼叫此函式可傳回命令的文字名稱或狀態字串。

```cpp
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
要搭配命令使用之文字的指標。

## <a name="see-also"></a>另請參閱

[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
