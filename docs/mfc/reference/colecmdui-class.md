---
title: COleCmdUI 類別
ms.date: 09/12/2018
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
ms.openlocfilehash: 1b7a6b21a3ad778b4a5ca345b1aaf42875810e4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376272"
---
# <a name="colecmdui-class"></a>COleCmdUI 類別

實作 MFC 的方法以更新與應用程式 `IOleCommandTarget`驅動功能相關聯之使用者介面物件的狀態。

## <a name="syntax"></a>語法

```
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleCmdUI:COleCmdUI](#colecmdui)|建構 `COleCmdUI` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleCmdUI:啟用](#enable)|設置或清除啟用命令標誌。|
|[COleCmdUI::設定檢查](#setcheck)|設置開/關切換命令的狀態。|
|[COleCmdUI::設定文字](#settext)|傳回指令的文字名稱或狀態字串。|

## <a name="remarks"></a>備註

在未為 DocObjects 啟用的應用程式中,當使用者在應用程式中查看功能表時,MFC 會處理UPDATE_COMMAND_UI。 每個通知都給定一個[CCmdUI](../../mfc/reference/ccmdui-class.md)物件,可以對其進行操作以反映特定命令的狀態。 但是,當為 DocObjects 啟用應用程式時,MFC 會`COleCmdUI`處理UPDATE_OLE_COMMAND_UI通知 並分配物件。

`COleCmdUI`允許 DocObject 接收源自其容器使用者介面的命令(如 FileNew、Open、Print 等),並允許容器接收源自 DocObject 用戶介面的命令。 儘管`IDispatch`可用於調度相同的命令,但提供了一`IOleCommandTarget`種 更簡單的查詢和執行方法,因為它依賴於一組標準的命令(通常沒有參數,並且不涉及類型資訊)。 `COleCmdUI`可用於啟用、更新和設置 DocObject 使用者介面命令的其他屬性。 當您要呼叫這個指令時,請致電[COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)。

關於文件物件的詳細資訊,請參閱[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)與[CDocObjectServer 專案](../../mfc/reference/cdocobjectserveritem-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CmDUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>需求

**標題:** afxdocobj.h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI:COleCmdUI

建構與特定`COleCmdUI`使用者介面命令關聯的物件。

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>參數

*rgCmds*<br/>
與給定 GUID 關聯的受支援命令的清單。 結構`OLECMD`將命令與命令標誌關聯。

*cCmds*<br/>
*rgCmds*中命令的計數。

*p組*<br/>
指向標識一組命令的 GUID 的指標。

### <a name="remarks"></a>備註

該`COleCmdUI`物件提供用於更新 DocObject 用戶介面物件的程式設計介面,如功能表項或控制欄按鈕。 使用者介面物件可以`COleCmdUI`通過 該物件啟用、禁用、檢查和/或清除。

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI:啟用

呼叫此函數將`COleCmdUI`物件的命令標誌設置為OLECOMDF_ENABLED,該標誌告訴介面命令可用並啟用,或者清除命令標誌。

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>參數

*邦*<br/>
指示應啟用還是禁用與`COleCmdUI`對象關聯的命令。 非零啟用命令;0 禁用該命令。

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI::設定檢查

調用此函數以設置開/關切換命令的狀態。

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>參數

*N檢查*<br/>
確定要設置開/關切換命令的狀態的值。 值為：

|值|描述|
|-----------|-----------------|
|**1**|將命令設置為"打開」。|
|**2**|將命令設置為不確定;無法確定狀態,因為此命令的屬性在相關選擇中處於開/關狀態。|
|任何其他值|將命令設置為關閉。|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI::設定文字

呼叫此函數以傳回指令的文字名稱或狀態字串。

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
指向要與命令一起使用的文本的指標。

## <a name="see-also"></a>另請參閱

[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
