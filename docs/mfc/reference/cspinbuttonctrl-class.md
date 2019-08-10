---
title: CSpinButtonCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
ms.openlocfilehash: da247524dae77627bbf041b83bc1534a75c3b073
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916695"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl 類別

提供 Windows 通用微調按鈕控制項的功能。

## <a name="syntax"></a>語法

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|建構 `CSpinButtonCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSpinButtonCtrl::Create](#create)|建立微調按鈕控制項, 並將其附加至`CSpinButtonCtrl`物件。|
|[CSpinButtonCtrl::CreateEx](#createex)|使用指定的 Windows 擴充樣式建立微調按鈕控制項, 並將其附加至`CSpinButtonCtrl`物件。|
|[CSpinButtonCtrl::GetAccel](#getaccel)|抓取微調按鈕控制項的加速資訊。|
|[CSpinButtonCtrl::GetBase](#getbase)|抓取微調按鈕控制項的目前基底。|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|抓取目前好友視窗的指標。|
|[CSpinButtonCtrl::GetPos](#getpos)|抓取微調按鈕控制項的目前位置。|
|[CSpinButtonCtrl::GetRange](#getrange)|抓取微調按鈕控制項的上限和下限 (範圍)。|
|[CSpinButtonCtrl::SetAccel](#setaccel)|設定微調按鈕控制項的加速。|
|[CSpinButtonCtrl::SetBase](#setbase)|設定微調按鈕控制項的基底。|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|設定微調按鈕控制項的好友視窗。|
|[CSpinButtonCtrl::SetPos](#setpos)|設定控制項的目前位置。|
|[CSpinButtonCtrl::SetRange](#setrange)|設定微調按鈕控制項的上限和下限 (範圍)。|

## <a name="remarks"></a>備註

「微調按鈕控制項」 (也稱為上下按鈕控制項) 是一對箭號按鈕, 使用者可以按一下以遞增或遞減值, 例如捲軸位置或顯示在附屬控制項中的數位。 與微調按鈕控制項相關聯的值稱為其目前位置。 微調按鈕控制項最常搭配附屬控制項使用, 稱為「好友視窗」。

這個控制項 (因此`CSpinButtonCtrl`類別) 僅適用于在 windows 95/98 和 windows NT 3.51 版和更新版本下執行的程式。

對使用者而言, 微調按鈕控制項和其合作者視窗通常看起來就像單一控制項。 您可以指定微調按鈕控制項自動在其 [好友] 視窗旁邊放置, 並自動將 [好友] 視窗的標題設定為其目前的位置。 您可以使用微調按鈕控制項搭配編輯控制項, 以提示使用者輸入數值。

按一下向上箭號會將目前的位置移至最大值, 然後按一下向下箭號會將目前的位置向最小。 根據預設, 最小值為 100, 最大值為0。 當最小值設定大於最大值設定時 (例如, 使用預設設定時), 按一下向上鍵會減少位置值, 然後按一下向下箭號就會增加。

不含「合作者視窗」功能的微調按鈕控制項, 做為一種簡化的捲軸。 例如, 索引標籤控制項有時會顯示微調按鈕控制項, 讓使用者可以將其他索引標籤滾動到視野中。

如需使用`CSpinButtonCtrl`的詳細資訊, 請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="create"></a>CSpinButtonCtrl:: Create

建立微調按鈕控制項, 並將其附加至`CSpinButtonCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定微調按鈕控制項的樣式。 將微調按鈕控制項樣式的任何組合套用至控制項。 這些樣式會在 Windows SDK 中的[上下按鈕控制項樣式](/windows/desktop/Controls/up-down-control-styles)中加以描述。

*rect*<br/>
指定微調按鈕控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構

*pParentWnd*<br/>
微調按鈕控制項的父視窗指標, 通常為`CDialog`。 不得為 Null。

*nID*<br/>
指定微調按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

您會先`CSpinButtonCtrl`以兩個步驟來建立物件, 呼叫此函式, `Create`然後呼叫, 它會建立微調按鈕控制項, `CSpinButtonCtrl`並將其附加至物件。

若要建立具有延伸視窗樣式的微調按鈕控制項, 請呼叫[CSpinButtonCtrl:: CreateEx](#createex) , 而不是`Create`。

##  <a name="createex"></a>CSpinButtonCtrl:: CreateEx

建立控制項 (子視窗), 並將它與`CSpinButtonCtrl`物件產生關聯。

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
指定所要建立之控制項的延伸樣式。 如需擴充 windows 樣式的清單, 請參閱 Windows SDK 中[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)的*dwExStyle*參數。

*dwStyle*<br/>
指定微調按鈕控制項的樣式。 將微調按鈕控制項樣式的任何組合套用至控制項。 這些樣式會在 Windows SDK 中的[上下按鈕控制項樣式](/windows/desktop/Controls/up-down-control-styles)中加以描述。

*rect*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考, 描述要建立之視窗的大小和位置, 以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx` , 而不是[Create](#create)來套用擴充的 windows 樣式 (由 Windows 擴充樣式指定于 WS_EX_ 的前面)。

##  <a name="cspinbuttonctrl"></a>CSpinButtonCtrl:: CSpinButtonCtrl

建構 `CSpinButtonCtrl` 物件。

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

抓取微調按鈕控制項的加速資訊。

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>參數

*nAccel*<br/>
*PAccel*所指定之陣列中的元素數目。

*pAccel*<br/>
接收加速資訊之[UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-udaccel)結構陣列的指標。

### <a name="return-value"></a>傳回值

抓取的快速鍵結構數目。

##  <a name="getbase"></a>CSpinButtonCtrl:: GetBase

抓取微調按鈕控制項的目前基底。

```
UINT GetBase() const;
```

### <a name="return-value"></a>傳回值

目前的基底值。

##  <a name="getbuddy"></a>CSpinButtonCtrl:: GetBuddy

抓取目前好友視窗的指標。

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>傳回值

目前好友視窗的指標。

##  <a name="getpos"></a>CSpinButtonCtrl:: GetPos

抓取微調按鈕控制項的目前位置。

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>參數

*lpbError*<br/>
布林值的指標, 如果成功抓取值, 則設定為零; 如果發生錯誤, 則為非零。 如果此參數設定為 Null, 則不會報告錯誤。

### <a name="return-value"></a>傳回值

第一個版本會傳回低序位字組中的16位目前位置。 如果發生錯誤, 則高序位單字為非零值。

第二個版本會傳回32位位置。

### <a name="remarks"></a>備註

當它處理傳回的值時, 控制項會根據好友視窗的標題來更新其目前的位置。 如果沒有任何合作者視窗, 或標題指定了無效或超出範圍的值, 控制項就會傳回錯誤。

##  <a name="getrange"></a>CSpinButtonCtrl:: GetRange

抓取微調按鈕控制項的上限和下限 (範圍)。

```
DWORD GetRange() const;

void GetRange(
    int& lower,
    int& upper) const;

void GetRange32(
    int& lower,
    int &upper) const;
```

### <a name="parameters"></a>參數

*零下*<br/>
參考可接收控制項下限的整數。

*upper*<br/>
參考可接收控制項上限的整數。

### <a name="return-value"></a>傳回值

第一個版本會傳回32位值, 其中包含上限和下限。 低序位字組是控制項的上限, 而高序位字則是較低的限制。

### <a name="remarks"></a>備註

此成員`GetRange32`函式會將微調按鈕控制項的範圍, 抓取為32位整數。

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

設定微調按鈕控制項的加速。

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>參數

*nAccel*<br/>
*PAccel*所指定的[UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-udaccel)結構數目。

*pAccel*<br/>
UDACCEL 結構陣列的指標, 其中包含加速資訊。 元素應根據`nSec`成員以遞增順序排序。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="setbase"></a>CSpinButtonCtrl:: SetBase

設定微調按鈕控制項的基底。

```
int SetBase(int nBase);
```

### <a name="parameters"></a>參數

*nBase*<br/>
控制項的新基底值。 十進位或16的十六進位可以是10。

### <a name="return-value"></a>傳回值

如果成功, 則為前一個基底值, 如果指定了不正確基底, 則為零。

### <a name="remarks"></a>備註

[基底] 值決定 [合作者] 視窗是否顯示十進位或十六進位數位的數位。 十六進位數位一律不帶正負號;十進位數已簽署。

##  <a name="setbuddy"></a>CSpinButtonCtrl:: SetBuddy

設定微調按鈕控制項的好友視窗。

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>參數

*pWndBuddy*<br/>
新的合作者視窗的指標。

### <a name="return-value"></a>傳回值

上一個好友視窗的指標。

### <a name="remarks"></a>備註

微調控制項幾乎一律會與另一個視窗 (例如編輯控制項) 相關聯, 以顯示某些內容。 這個另一個視窗稱為微調控制項的「好友」。

##  <a name="setpos"></a>CSpinButtonCtrl:: SetPos

設定微調按鈕控制項的目前位置。

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
控制項的新位置。 這個值必須在控制項的上限和下限所指定的範圍內。

### <a name="return-value"></a>傳回值

先前的位置 (的16位`SetPos`有效位數,, 32 位`SetPos32`有效位數)。

### <a name="remarks"></a>備註

`SetPos32`設定32位位置。

##  <a name="setrange"></a>CSpinButtonCtrl:: SetRange

設定微調按鈕控制項的上限和下限 (範圍)。

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>參數

*nLower*和*nUpper*<br/>
控制項的上限和下限。 若`SetRange`為, 則限制不能大於 UD_MAXVAL 或小於 UD_MINVAL; 此外, 這兩個限制之間的差異不能超過 UD_MAXVAL。 `SetRange32`限制不受限制;使用任何整數。

### <a name="remarks"></a>備註

成員函式`SetRange32`會設定微調按鈕控制項的32位範圍。

> [!NOTE]
>  微調按鈕的預設範圍會將最大值設定為零 (0), 並將最小值設定為100。 由於最大值小於最小值, 按一下向上箭號將會減少位置, 按一下向下箭號將會增加。 使用`CSpinButtonCtrl::SetRange`來調整這些值。

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl 類別](../../mfc/reference/csliderctrl-class.md)
