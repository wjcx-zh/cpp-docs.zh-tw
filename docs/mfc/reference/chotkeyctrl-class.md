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
ms.openlocfilehash: a79cc0ab2c01633f96430477aa536a60385461e9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750809"
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
|[CHotKeyctrl:: CHotkeyCtrl](#chotkeyctrl)|建構 `CHotKeyCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHotKeyCtrl::建立](#create)|創建熱鍵控制件並將其附加到`CHotKeyCtrl`物件。|
|[CHotKeyctrl::建立Ex](#createex)|使用指定的 Windows 擴充樣式創建熱鍵控制項,並將`CHotKeyCtrl`其附加到 物件。|
|[CHotKeyctrl:取得HotKey](#gethotkey)|從熱鍵控制元件檢索熱鍵的虛擬金鑰代碼和修改器標誌。|
|[CHotKeyctrl:取得Hotkey名稱](#gethotkeyname)|檢索分配給熱鍵的本地字元集中的鍵名稱。|
|[CHotKeyctrl:取得鍵名稱](#getkeyname)|檢索分配給指定虛擬金鑰代碼的本地字元集中的密鑰名稱。|
|[CHotKeyctrl::設定HotKey](#sethotkey)|設置熱鍵控制的熱鍵組合。|
|[CHotKeyctrl::設定規則](#setrules)|定義熱鍵控制件的無效組合和預設修改器組合。|

## <a name="remarks"></a>備註

"熱鍵控制件"是允許使用者創建熱鍵的視窗。 "熱鍵"是使用者可以按快速執行操作的鍵組合。 (例如,用戶可以創建一個熱鍵,該熱鍵可啟動給定的視窗並將其帶到 Z 順序的頂部。熱鍵控制項顯示使用者的選擇,並確保使用者選擇有效的密鑰組合。

此控制項(因此該`CHotKeyCtrl`類別)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

當使用者選擇密鑰組合后,應用程式可以從控件中檢索指定的密鑰組合,並使用WM_SETHOTKEY消息在系統中設置熱鍵。 此後,每當使用者從系統的任何部分按下熱鍵時,WM_SETHOTKEY消息中指定的視窗都會收到指定SC_HOTKEYWM_SYSCOMMAND消息。 此消息將啟動接收它的視窗。 熱鍵在調用WM_SETHOTKEY的應用程式退出之前保持有效。

此機制不同於依賴於WM_HOTKEY消息和 Windows[註冊HotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey)和[取消註冊 HotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey)功能的熱鍵支援。

有關`CHotKeyCtrl`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)[與使用 CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a>CHotKeyctrl:: CHotkeyCtrl

建構 `CHotKeyCtrl` 物件。

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a>CHotKeyCtrl::建立

創建熱鍵控制件並將其附加到`CHotKeyCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定熱鍵控件的樣式。 應用控件樣式的任意組合。 有關詳細資訊,請參閱 Windows SDK 中的[通用控制元件樣式](/windows/win32/Controls/common-control-styles)。

*矩形*<br/>
指定熱鍵控制的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT 結構](/windows/win32/api/windef/ns-windef-rect)。

*pparentwnd*<br/>
指定熱鍵控制的父視窗,通常為[CDialog](../../mfc/reference/cdialog-class.md)。 它不得為 NULL。

*nID*<br/>
指定熱鍵控制項的識別碼。

### <a name="return-value"></a>傳回值

非零,如果初始化成功;否則 0。

### <a name="remarks"></a>備註

分兩步`CHotKeyCtrl`構造物件。 首先調用構造函數,然後調用`Create`,這將創建熱鍵控件並將其附加`CHotKeyCtrl`到 物件。

如果要將延伸視窗樣式與控制項一起使用,請呼叫[CreateEx](#createex)`Create`而不是 。

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a>CHotKeyctrl::建立Ex

呼叫此函數以建立控制項(子視窗),並將其與`CHotKeyCtrl`物件關聯。

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
指定要創建的控制項的擴充樣式。 有關擴展 Windows 樣式的清單,請參閱 Windows SDK 中[創建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定熱鍵控件的樣式。 應用控件樣式的任意組合。 有關詳細資訊,請參閱 Windows SDK 中的[通用控制元件樣式](/windows/win32/Controls/common-control-styles)。

*矩形*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用擴展的 Windows 樣式,該樣式由 Windows 擴充樣式前言**WS_EX_** 指定。

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a>CHotKeyctrl:取得HotKey

從熱鍵控件檢索鍵盤快捷方式的虛擬鍵代碼和修改器標誌。

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>參數

*w虛擬金鑰碼*<br/>
[出]鍵盤快速鍵的虛擬鍵碼。 有關標準虛擬金鑰代碼的清單,請參閱 Winuser.h。

*w 修飾器*<br/>
[出]指示鍵盤快捷鍵中修改器鍵的字面組合 (OR)。

變更器標誌如下所示:

|旗標|對應鍵|
|----------|-----------------------|
|HOTKEYF_ALT|ALT 鍵|
|HOTKEYF_CONTROL|CTRL 金鑰|
|HOTKEYF_EXT|延伸金鑰|
|HOTKEYF_SHIFT|換檔鍵|

### <a name="return-value"></a>傳回值

在第一個重載方法中,包含虛擬密鑰代碼和修改器標誌的 DWORD。 低階字的低階位元組包含虛擬鍵碼,低階單詞的高階位元組包含修飾符標誌,高階字為零。

### <a name="remarks"></a>備註

虛擬鍵代碼和修改器鍵一起定義鍵盤快速鍵。

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a>CHotKeyctrl:取得Hotkey名稱

調用此成員函數獲取熱鍵的本地化名稱。

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>傳回值

當前選定的熱鍵的當地語系化名稱。 如果沒有選定的熱鍵,則`GetHotKeyName`返回一個空字串。

### <a name="remarks"></a>備註

此成員函數返回的名稱來自鍵盤驅動程式。 您可以在當地語系化版本的 Windows 中安裝非當地語系化的鍵盤驅動程式,反之亦然。

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a>CHotKeyctrl:取得鍵名稱

呼叫此成員函數獲取分配給指定虛擬密鑰代碼的密鑰的本地化名稱。

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>參數

*vk*<br/>
虛擬金鑰代碼。

*f 延伸*<br/>
如果虛擬密鑰代碼是擴展密鑰,則 TRUE;否則 FALSE。

### <a name="return-value"></a>傳回值

*vk*參數指定的鍵的當地語系化名稱。 如果鍵沒有映射的名稱,則`GetKeyName`返回一個空字串。

### <a name="remarks"></a>備註

此功能傳回的鍵名稱來自鍵盤驅動程式,因此您可以在當地語系化版本的 Windows 中安裝非本地化鍵盤驅動程式,反之亦然。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a>CHotKeyctrl::設定HotKey

設置熱鍵控件的鍵盤快捷方式。

```cpp
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>參數

*w虛擬金鑰碼*<br/>
[在]鍵盤快速鍵的虛擬鍵碼。 有關標準虛擬金鑰代碼的清單,請參閱 Winuser.h。

*w 修飾器*<br/>
[在]指示鍵盤快捷鍵中修改器鍵的字面組合 (OR)。

變更器標誌如下所示:

|旗標|對應鍵|
|----------|-----------------------|
|HOTKEYF_ALT|ALT 鍵|
|HOTKEYF_CONTROL|CTRL 金鑰|
|HOTKEYF_EXT|延伸金鑰|
|HOTKEYF_SHIFT|換檔鍵|

### <a name="remarks"></a>備註

虛擬鍵代碼和修改器鍵一起定義鍵盤快速鍵。

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a>CHotKeyctrl::設定規則

調用此函數以定義熱鍵控制件的無效組合和預設修改器組合。

```cpp
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>參數

*w 無效康布*<br/>
指定無效鍵組合的標誌陣列。 它可以是以下值的組合:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL_ALT

- HKCOMB_NONE未變更的鍵

- HKCOMB_S班次

- HKCOMB_SA SHIFT_ALT

- HKCOMB_SC班位_CTRL

- HKCOMB_SCA班位_CTRL_ALT

*w 修飾器*<br/>
標記陣列,指定使用者輸入無效組合時要使用的鍵組合。 有關修改標記的詳細資訊,請參閱[GetHotKey](#gethotkey)。

### <a name="remarks"></a>備註

當使用者輸入無效的鍵組合(由*wInvalidComb*中指定的標誌定義)時,系統使用 OR 運算符將使用者輸入的鍵與*w 修改器*中指定的標誌合併。 生成的鍵組合將轉換為字串,然後顯示在熱鍵控件中。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
