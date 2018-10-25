---
title: CHotKeyCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12aa039e0beede4f395da3de6eea4e6c956f9373
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074458"
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
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|建構 `CHotKeyCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHotKeyCtrl::Create](#create)|建立熱鍵控制項，並將它附加至`CHotKeyCtrl`物件。|
|[CHotKeyCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式中建立熱鍵控制項，並將它附加至`CHotKeyCtrl`物件。|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|從熱鍵控制項擷取的虛擬索引鍵的程式碼和修飾詞旗標的熱鍵。|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|擷取本機字元集中，指派給最忙碌的索引鍵的索引鍵名稱。|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|擷取索引鍵的名稱，本機字元集中，指派給指定的虛擬按鍵碼。|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|設定熱鍵控制項的作用的按鍵組合。|
|[CHotKeyCtrl::SetRules](#setrules)|定義的無效組合和預設的修飾詞組合的熱鍵控制項。|

## <a name="remarks"></a>備註

「 熱鍵控制項 」 是一個視窗，讓使用者可以建立快速鍵。 「 最忙碌的金鑰 」 是索引鍵的組合，使用者可以按下以快速執行的動作。 （例如，使用者可以建立快速鍵，啟動指定的視窗，並將它帶到疊置順序的頂端。）熱鍵控制項顯示使用者的選項，並確保使用者選取有效的按鍵組合。

這個控制項 (並因此`CHotKeyCtrl`類別) 僅適用於 Windows 95/98 和 Windows NT 版 3.51 下執行的程式和更新版本。

當使用者選擇的按鍵組合時，應用程式就可以從控制項擷取指定的按鍵組合，並使用 WM_SETHOTKEY 訊息在系統中設定熱鍵。 每當使用者按下便捷鍵之後，從任何系統的一部分，WM_SETHOTKEY 訊息中所指定視窗就會收到指定 SC_HOTKEY WM_SYSCOMMAND 訊息。 此訊息會啟動所收到的視窗。 熱鍵的應用程式，稱為 WM_SETHOTKEY 結束之前會保持有效。

這項機制是從經常性存取金鑰的支援取決於 WM_HOTKEY 訊息和 Windows 的不同[RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309)並[UnregisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646327)函式。

如需有關使用`CHotKeyCtrl`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)並[使用 CHotKeyCtrl](../../mfc/using-chotkeyctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="chotkeyctrl"></a>  CHotKeyCtrl::CHotKeyCtrl

建構 `CHotKeyCtrl` 物件。

```
CHotKeyCtrl();
```

##  <a name="create"></a>  CHotKeyCtrl::Create

建立熱鍵控制項，並將它附加至`CHotKeyCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*cheaderctrl:: Create*<br/>
指定熱鍵控制項的樣式。 適用於任何控制項樣式的組合。 請參閱[常見的控制項樣式](/windows/desktop/Controls/common-control-styles)Windows sdk for 的詳細資訊。

*rect*<br/>
指定熱鍵控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT 結構](../../mfc/reference/rect-structure1.md)。

*pParentWnd*<br/>
指定熱鍵控制項的父視窗，通常[CDialog](../../mfc/reference/cdialog-class.md)。 它必須不是 NULL。

*nID*<br/>
指定熱鍵控制項的識別碼。

### <a name="return-value"></a>傳回值

非零值，如果初始化成功;否則為 0。

### <a name="remarks"></a>備註

您建構`CHotKeyCtrl`兩個步驟中的物件。 首先，呼叫建構函式，然後呼叫`Create`，這會建立熱鍵控制項，並將它附加至`CHotKeyCtrl`物件。

如果您想要使用擴充的 windows 樣式和控制項，呼叫[CreateEx](#createex)而不是`Create`。

##  <a name="createex"></a>  CHotKeyCtrl::CreateEx

呼叫此函式來建立控制項 （子視窗），但其關聯`CHotKeyCtrl`物件。

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
指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*cheaderctrl:: Create*<br/>
指定熱鍵控制項的樣式。 適用於任何控制項樣式的組合。 如需詳細資訊，請參閱 <<c0> [ 常見的控制項樣式](/windows/desktop/Controls/common-control-styles)Windows SDK 中。

*rect*<br/>
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。

*pParentWnd*<br/>
是控制項的父視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而非[建立](#create)套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。

##  <a name="gethotkey"></a>  CHotKeyCtrl::GetHotKey

從熱鍵控制項擷取的虛擬索引鍵的程式碼和修飾詞旗標的鍵盤快速鍵。

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>參數

*wVirtualKeyCode*<br/>
[out]鍵盤快速鍵的虛擬按鍵碼。 如需標準虛擬按鍵碼的清單，請參閱 Winuser.h。

*wModifiers*<br/>
[out]位元組合 (OR) 旗標，表示修飾詞中的索引鍵的鍵盤快速鍵。

輔助鍵旗標如下所示：

|旗標|對應的索引鍵|
|----------|-----------------------|
|HOTKEYF_ALT|ALT 鍵|
|HOTKEYF_CONTROL|CTRL 鍵|
|HOTKEYF_EXT|擴充的索引鍵|
|HOTKEYF_SHIFT|Shift 鍵|

### <a name="return-value"></a>傳回值

在第一個多載方法，DWORD，其中包含虛擬索引鍵的程式碼和修飾詞旗標。 低序位字組的低序位位元組包含虛擬按鍵碼、 低序位字組的高序位位元組包含輔助鍵旗標和高序位字為零。

### <a name="remarks"></a>備註

虛擬按鍵碼和輔助按鍵一起定義的鍵盤快速鍵。

##  <a name="gethotkeyname"></a>  CHotKeyCtrl::GetHotKeyName

呼叫此成員函式，以取得熱鍵的當地語系化的名稱。

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>傳回值

目前選取的熱鍵當地語系化的名稱。 如果沒有任何選取的快速鍵，`GetHotKeyName`傳回空字串。

### <a name="remarks"></a>備註

此成員函式所傳回的名稱來自於鍵盤驅動程式。 您可以將非當地語系化的鍵盤驅動程式安裝在當地語系化版本的 Windows，反之亦然。

##  <a name="getkeyname"></a>  CHotKeyCtrl::GetKeyName

呼叫此成員函式，以取得指派給指定的虛擬按鍵碼的索引鍵的當地語系化的名稱。

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>參數

*vk*<br/>
虛擬按鍵碼。

*fExtended*<br/>
如果虛擬按鍵碼是擴充的索引鍵，用來為 TRUE，否則為 FALSE。

### <a name="return-value"></a>傳回值

所指定的索引鍵的當地語系化的名稱*vk*參數。 如果金鑰沒有對應的名稱，`GetKeyName`傳回空字串。

### <a name="remarks"></a>備註

此函數會傳回索引鍵名稱來自鍵盤驅動程式，因此您可以將非當地語系化的鍵盤驅動程式安裝在當地語系化版本的 Windows，反之亦然。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>  CHotKeyCtrl::SetHotKey

設定熱鍵控制項的鍵盤快速鍵。

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>參數

*wVirtualKeyCode*<br/>
[in]鍵盤快速鍵的虛擬按鍵碼。 如需標準虛擬按鍵碼的清單，請參閱 Winuser.h。

*wModifiers*<br/>
[in]位元組合 (OR) 旗標，表示修飾詞中的索引鍵的鍵盤快速鍵。

輔助鍵旗標如下所示：

|旗標|對應的索引鍵|
|----------|-----------------------|
|HOTKEYF_ALT|ALT 鍵|
|HOTKEYF_CONTROL|CTRL 鍵|
|HOTKEYF_EXT|擴充的索引鍵|
|HOTKEYF_SHIFT|Shift 鍵|

### <a name="remarks"></a>備註

虛擬按鍵碼和輔助按鍵一起定義的鍵盤快速鍵。

##  <a name="setrules"></a>  CHotKeyCtrl::SetRules

呼叫此函式可定義的無效組合和預設的修飾詞組合的熱鍵控制項。

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>參數

*wInvalidComb*<br/>
指定無效的索引鍵組合旗標的陣列。 它可以是下列值的組合：

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE 未經修改的索引鍵

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT + ALT 鍵

- HKCOMB_SC SHIFT + CTRL

- HKCOMB_SCA SHIFT + CTRL + ALT

*wModifiers*<br/>
旗標的陣列，指定在使用者輸入無效的組合時所要使用的按鍵組合。 如需有關輔助鍵旗標的詳細資訊，請參閱[GetHotKey](#gethotkey)。

### <a name="remarks"></a>備註

當使用者輸入無效的按鍵組合，定義中指定的旗標*wInvalidComb*，系統會使用 OR 運算子結合使用者輸入具有在指定的旗標的索引鍵*wModifiers*. 產生的組合鍵已轉換成字串，而且接著會顯示在熱鍵控制項。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)

