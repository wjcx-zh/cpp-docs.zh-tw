---
title: CDockState 類別
ms.date: 11/04/2016
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
ms.openlocfilehash: b8c4b80d7182795d8919adb64491d506325976ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391175"
---
# <a name="cdockstate-class"></a>CDockState 類別

序列化的 `CObject` 類別，這個類別會在持續性記憶體 (檔案) 中載入、卸載或清除一個或多個停駐控制列的狀態。

## <a name="syntax"></a>語法

```
class CDockState : public CObject
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDockState::Clear](#clear)|清除停駐狀態資訊。|
|[CDockState::GetVersion](#getversion)|擷取儲存的版本號碼列狀態。|
|[CDockState::LoadState](#loadstate)|擷取狀態資訊從登錄或。INI 檔案。|
|[CDockState::SaveState](#savestate)|將狀態資訊儲存至登錄或 INI 檔。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|若要儲存的指標陣列停駐狀態資訊，與每個控制列的一個項目。|

## <a name="remarks"></a>備註

停駐狀態包含大小和列和停駐的位置。 當擷取預存停駐狀態，`CDockState`檢查列的位置，如果目前的畫面設定值，看不到 列`CDockState`調整列的位置，讓它會顯示。 主要目的`CDockState`是保存的數個控制列的整個狀態，並允許該狀態儲存和載入至登錄，應用程式的其中一個。INI 檔案，或以二進位格式的一部分`CArchive`物件的內容。

列可以是任何可停駐控制項列，包括工具列、 狀態列、 或對話方塊列。 `CDockState` 物件會寫入和讀取檔案，以透過來回`CArchive`物件。

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate)擷取所有框架視窗的狀態資訊`CControlBar`物件，並將其放入`CDockState`物件。 然後，您可以撰寫的內容`CDockState`至儲存體使用的物件[Serialize](../../mfc/reference/cobject-class.md#serialize)或是[CDockState::SaveState](#savestate)。 如果您稍後想要還原在框架視窗中的控制列的狀態，您可以載入的狀態與`Serialize`或是[CDockState::LoadState](#loadstate)，然後使用[CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate)套用已儲存框架視窗的控制列的狀態。

如需有關如何停駐控制列的詳細資訊，請參閱文章[控制列](../../mfc/control-bars.md)，[工具列：停駐和浮動](../../mfc/docking-and-floating-toolbars.md)，並[框架 Windows](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>需求

**標頭：** afxadv.h

##  <a name="clear"></a>  CDockState::Clear

呼叫此函式來清除所有停駐的資訊儲存在`CDockState`物件。

```
void Clear();
```

### <a name="remarks"></a>備註

這包括不僅是否列停駐，但列的大小和位置，以及它可見。

##  <a name="getversion"></a>  CDockState::GetVersion

呼叫此函式可擷取儲存的版本號碼列狀態。

```
DWORD GetVersion();
```

### <a name="return-value"></a>傳回值

1，否則預存的列資訊已超過目前列檢視狀態。2 如果預存的列資訊等同於目前列狀態。

### <a name="remarks"></a>備註

版本支援讓修改過的列，來加入新的持續性屬性，而且仍然能夠偵測並載入列的舊版本所建立的永續性狀態。

##  <a name="loadstate"></a>  CDockState::LoadState

呼叫此函式可從登錄擷取狀態資訊或。INI 檔案。

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
指向以 null teminated 字串，指定的初始設定檔案或儲存狀態資訊的 Windows 登錄機碼中的區段的名稱。

### <a name="remarks"></a>備註

設定檔名稱是應用程式的區段。INI 檔案或登錄，其中包含的橫條的狀態資訊。 您可以將控制列的狀態資訊儲存至登錄或。INI 檔案`SaveState`。

##  <a name="m_arrbarinfo"></a>  CDockState::m_arrBarInfo

A`CPtrArray`亦即已儲存的狀態資訊在每個控制列的預存的控制列資訊的指標陣列`CDockState`物件。

```
CPtrArray m_arrBarInfo;
```

##  <a name="savestate"></a>  CDockState::SaveState

呼叫此函式，以將狀態資訊儲存至登錄或。INI 檔案。

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
指向以 null teminated 字串，指定的初始設定檔案或儲存狀態資訊的 Windows 登錄機碼中的區段的名稱。

### <a name="remarks"></a>備註

設定檔名稱是應用程式的區段。INI 檔案或登錄，其中包含控制列的狀態資訊。 `SaveState` 也會儲存目前的螢幕大小。 您可以從登錄擷取控制列資訊或。INI 檔案`LoadState`。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
