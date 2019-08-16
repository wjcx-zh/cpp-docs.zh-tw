---
title: CHotKeyCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: 9818c32a7779d646ca5a9485a1331dfa393408ba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506153"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl 類別

提供 Windows 通用快速鍵控制項的功能。

## <a name="syntax"></a>語法

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHotKeyCtrl:: CHotKeyCtrl](#chotkeyctrl)|建構 `CHotKeyCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CHotKeyCtrl::Create](#create)|建立熱鍵控制項並將其附加至`CHotKeyCtrl`物件。|
|[CHotKeyCtrl::CreateEx](#createex)|建立具有指定之 Windows 擴充樣式的熱鍵控制項, 並將其附加至`CHotKeyCtrl`物件。|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|從熱鍵控制項抓取熱鍵的虛擬按鍵程式碼和輔助按鍵旗標。|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|抓取指派給熱鍵的本機字元集中的索引鍵名稱。|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|抓取本機字元集中, 指派給指定之虛擬按鍵程式碼的索引鍵名稱。|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|設定熱鍵控制項的快速鍵組合。|
|[CHotKeyCtrl::SetRules](#setrules)|定義熱鍵控制項的無效組合和預設的修飾片語合。|

## <a name="remarks"></a>備註

「熱鍵控制項」是可讓使用者建立熱鍵的視窗。 「熱鍵」是使用者可以按下的按鍵組合, 以快速執行動作。 (例如, 使用者可以建立啟用指定視窗的熱鍵, 並將其帶到 Z 順序的頂端)。熱鍵控制項會顯示使用者的選擇, 並確保使用者選取有效的按鍵組合。

這個控制項 (因此`CHotKeyCtrl`類別) 僅適用于在 windows 95/98 和 windows NT 3.51 版和更新版本下執行的程式。

當使用者選擇按鍵組合時, 應用程式可以從控制項抓取指定的按鍵組合, 並使用 WM_SETHOTKEY 訊息來設定系統中的熱鍵。 每當使用者按下熱鍵之後, 在系統的任何部分中, WM_SETHOTKEY 訊息中指定的視窗就會收到指定 SC_HOTKEY 的 WM_SYSCOMMAND 訊息。 此訊息會啟動接收它的視窗。 熱鍵會一直有效, 直到呼叫 WM_SETHOTKEY 的應用程式結束為止。

這項機制不同于與 WM_HOTKEY 訊息和 Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey)和[UnregisterHotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey)函式相依的熱鍵支援。

如需使用`CHotKeyCtrl`的詳細資訊, 請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="chotkeyctrl"></a>CHotKeyCtrl:: CHotKeyCtrl

建構 `CHotKeyCtrl` 物件。

```
CHotKeyCtrl();
```

##  <a name="create"></a>CHotKeyCtrl:: Create

建立熱鍵控制項並將其附加至`CHotKeyCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定快速鍵控制項的樣式。 套用控制項樣式的任何組合。 如需詳細資訊, 請參閱 Windows SDK 中的[常見控制項樣式](/windows/win32/Controls/common-control-styles)。

*rect*<br/>
指定熱鍵控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT 結構](/windows/win32/api/windef/ns-windef-rect)。

*pParentWnd*<br/>
指定快速鍵控制項的父視窗, 通常是[CDialog](../../mfc/reference/cdialog-class.md)。 不得為 Null。

*nID*<br/>
指定快速鍵控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

您可以使用`CHotKeyCtrl`兩個步驟來建立物件。 首先, 呼叫此函式, 然後`Create`呼叫, 它會建立熱鍵控制項並將其附加`CHotKeyCtrl`至物件。

如果您想要搭配控制項使用擴充的 windows 樣式, 請呼叫[CreateEx](#createex) , `Create`而不是。

##  <a name="createex"></a>CHotKeyCtrl:: CreateEx

呼叫這個函式以建立控制項 (子視窗), 並將它與`CHotKeyCtrl`物件產生關聯。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
指定所要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單, 請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定快速鍵控制項的樣式。 套用控制項樣式的任何組合。 如需詳細資訊, 請參閱 Windows SDK 中的[通用控制項樣式](/windows/win32/Controls/common-control-styles)。

*rect*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考, 描述要建立之視窗的大小和位置, 以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx` , 而不是[Create](#create)來套用擴充的 windows 樣式 (由 Windows 擴充樣式指定于**WS_EX_** 的前面)。

##  <a name="gethotkey"></a>CHotKeyCtrl:: GetHotKey

從快速鍵控制項抓取鍵盤快速鍵的虛擬按鍵程式碼和修飾詞旗標。

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>參數

*wVirtualKeyCode*<br/>
脫銷鍵盤快速鍵的虛擬按鍵程式碼。 如需標準虛擬按鍵代碼的清單, 請參閱 Winuser。

*wModifiers*<br/>
脫銷旗標的位元組合 (OR), 表示鍵盤快速鍵中的輔助按鍵。

修飾詞旗標如下所示:

|旗標|對應的索引鍵|
|----------|-----------------------|
|HOTKEYF_ALT|ALT 鍵|
|HOTKEYF_CONTROL|CTRL 鍵|
|HOTKEYF_EXT|擴充金鑰|
|HOTKEYF_SHIFT|SHIFT 鍵|

### <a name="return-value"></a>傳回值

在第一個多載方法中, 包含虛擬按鍵程式碼和修飾詞旗標的 DWORD。 低序位字組的低序位位元組包含虛擬按鍵程式碼, 低序位字組的高序位位元組包含修飾詞旗標, 而高序位字則為零。

### <a name="remarks"></a>備註

虛擬按鍵程式碼和輔助按鍵會定義鍵盤快速鍵。

##  <a name="gethotkeyname"></a>CHotKeyCtrl:: GetHotKeyName

呼叫這個成員函式以取得快速鍵的當地語系化名稱。

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>傳回值

目前所選取之快速鍵的當地語系化名稱。 如果沒有選取的熱鍵, `GetHotKeyName`則會傳回空字串。

### <a name="remarks"></a>備註

這個成員函式傳回的名稱來自鍵盤驅動程式。 您可以在當地語系化的 Windows 版本中安裝非當地語系化的鍵盤驅動程式, 反之亦然。

##  <a name="getkeyname"></a>CHotKeyCtrl:: GetKeyName

呼叫這個成員函式, 以取得指派給指定之虛擬按鍵程式碼之金鑰的當地語系化名稱。

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>參數

*vk*<br/>
虛擬按鍵程式碼。

*fExtended*<br/>
如果虛擬索引鍵程式碼是擴充的索引鍵, 則為 TRUE;否則為 FALSE。

### <a name="return-value"></a>傳回值

*Vk*參數所指定之索引鍵的當地語系化名稱。 如果索引鍵沒有對應的名稱, `GetKeyName`則會傳回空字串。

### <a name="remarks"></a>備註

此函式傳回的索引鍵名稱來自鍵盤驅動程式, 因此您可以在當地語系化的 Windows 版本中安裝非當地語系化的鍵盤驅動程式, 反之亦然。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>CHotKeyCtrl:: SetHotKey

設定熱鍵控制項的鍵盤快速鍵。

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>參數

*wVirtualKeyCode*<br/>
在鍵盤快速鍵的虛擬按鍵程式碼。 如需標準虛擬按鍵代碼的清單, 請參閱 Winuser。

*wModifiers*<br/>
在旗標的位元組合 (OR), 表示鍵盤快速鍵中的輔助按鍵。

修飾詞旗標如下所示:

|旗標|對應的索引鍵|
|----------|-----------------------|
|HOTKEYF_ALT|ALT 鍵|
|HOTKEYF_CONTROL|CTRL 鍵|
|HOTKEYF_EXT|擴充金鑰|
|HOTKEYF_SHIFT|SHIFT 鍵|

### <a name="remarks"></a>備註

虛擬按鍵程式碼和輔助按鍵會定義鍵盤快速鍵。

##  <a name="setrules"></a>CHotKeyCtrl:: SetRules

呼叫此函式可定義不正確組合, 以及常用於熱鍵控制項的預設輔助按鍵組合。

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>參數

*wInvalidComb*<br/>
指定無效索引鍵組合的旗標陣列。 它可以是下列值的組合:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE 未修改的金鑰

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT + ALT

- HKCOMB_SC SHIFT + CTRL

- HKCOMB_SCA SHIFT + CTRL + ALT

*wModifiers*<br/>
旗標的陣列, 指定當使用者輸入不正確組合時, 所要使用的按鍵組合。 如需輔助按鍵旗標的詳細資訊, 請參閱[GetHotKey](#gethotkey)。

### <a name="remarks"></a>備註

當使用者輸入不正確索引鍵組合 (如*wInvalidComb*中指定的旗標所定義) 時, 系統會使用 OR 運算子, 將使用者輸入的金鑰與*wModifiers*中指定的旗標結合。 產生的按鍵組合會轉換成字串, 然後在熱鍵控制項中顯示。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
