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
ms.openlocfilehash: 1c76bcda6465ca86b8da4778d3653cb23001b78b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375557"
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
|[CDockState:清除](#clear)|清除停靠狀態資訊。|
|[CDockState:取得版本](#getversion)|檢索存儲條狀態的版本號。|
|[CDockState::載入狀態](#loadstate)|從註冊表或 檢索狀態資訊。INI 檔。|
|[CDockState::儲存狀態](#savestate)|將狀態資訊保存到註冊表或 INI 檔。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[克多克州:m_arrBarInfo](#m_arrbarinfo)|指向存儲的停靠狀態資訊的指標數組,每個控制欄有一個條目。|

## <a name="remarks"></a>備註

停靠狀態包括條形的大小和位置,以及是否停靠。 檢索儲存的停靠狀態時,`CDockState`檢查條形圖的位置,如果當前螢幕設置不可見,`CDockState`則 縮放條形的位置,使其可見。 主要目的是`CDockState`保持多個控制列的整個狀態,並允許儲存該狀態並將其載入到註冊表,應用程式的 。INI 檔,或作為物件內容的`CArchive`一部分的二進位形式。

該欄可以是任何可停靠的控制欄,包括工具列、狀態列或對話方塊列。 `CDockState`對象`CArchive`以對對象寫入和讀取到檔案或從檔案讀取。

[CFrameWnd:GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate)檢索所有幀`CControlBar`視窗 物件的狀態資訊並將其放入物件`CDockState`中。 然後,您可以使用`CDockState`[序列化](../../mfc/reference/cobject-class.md#serialize)或[CDockState:::保存狀態](#savestate)將物件的內容寫入存儲。 如果以後要還原框架視窗中控制欄的狀態,則可以使用`Serialize`或[CDockState:LoadState](#loadstate)載入狀態,然後使用[CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate)將保存的狀態應用於幀視窗的控制欄。

有關停靠控制列的詳細資訊,請參閱[文章「控制件欄](../../mfc/control-bars.md)」、[工具列:停靠和浮動](../../mfc/docking-and-floating-toolbars.md),以及[框架視窗](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>需求

**標題:** afxadv.h

## <a name="cdockstateclear"></a><a name="clear"></a>CDockState:清除

調用此函數以清除存儲在物件中的所有`CDockState`停靠資訊。

```
void Clear();
```

### <a name="remarks"></a>備註

這不僅包括柱線是否停靠,還包括條形的大小和位置以及它是否可見。

## <a name="cdockstategetversion"></a><a name="getversion"></a>CDockState:取得版本

調用此函數以檢索存儲的條形狀態的版本號。

```
DWORD GetVersion();
```

### <a name="return-value"></a>傳回值

如果存儲的條形資訊早於當前條形狀態,則為 1;2 如果儲存的條形資訊與當前條形狀態相同。

### <a name="remarks"></a>備註

版本支援使修訂後的柱線能夠添加新的持久屬性,並且仍然能夠檢測和載入由早期版本的條形創建的持續狀態。

## <a name="cdockstateloadstate"></a><a name="loadstate"></a>CDockState::載入狀態

調用此函數從註冊表或 檢索狀態資訊。INI 檔。

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
指向一個空事件字串,該字串指定初始化檔中的節的名稱或存儲狀態資訊的 Windows 註冊表中的鍵。

### <a name="remarks"></a>備註

設定檔名稱是應用程式的部分。INI 檔或包含條形的狀態資訊的註冊表。 您可以將控制器資訊儲存到註冊表或 。INI`SaveState`檔案與 。

## <a name="cdockstatem_arrbarinfo"></a><a name="m_arrbarinfo"></a>克多克州:m_arrBarInfo

物件`CPtrArray`,它是指向在物件中保存狀態資訊的每個控制件欄的存儲控制欄資訊`CDockState`的指標陣列。

```
CPtrArray m_arrBarInfo;
```

## <a name="cdockstatesavestate"></a><a name="savestate"></a>CDockState::儲存狀態

呼叫此函數以將狀態資訊儲存到註冊表或 。INI 檔。

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
指向一個空事件字串,該字串指定初始化檔中的節的名稱或存儲狀態資訊的 Windows 註冊表中的鍵。

### <a name="remarks"></a>備註

設定檔名稱是應用程式的部分。INI 檔或包含控制欄狀態資訊的註冊表。 `SaveState`還保存當前螢幕大小。 可以從註冊表或 檢索控件欄資訊。INI`LoadState`檔案與 。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
