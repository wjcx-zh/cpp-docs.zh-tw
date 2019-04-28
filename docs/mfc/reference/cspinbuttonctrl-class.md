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
ms.openlocfilehash: 6f864a37c46158ab98776cd96d9f50d7cfaeb13d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324398"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl 類別

提供 Windows 通用微調按鈕控制項的功能。

## <a name="syntax"></a>語法

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|建構 `CSpinButtonCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSpinButtonCtrl::Create](#create)|建立使用微調按鈕控制項，並將它附加至`CSpinButtonCtrl`物件。|
|[CSpinButtonCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式中建立使用微調按鈕控制項，並將它附加至`CSpinButtonCtrl`物件。|
|[CSpinButtonCtrl::GetAccel](#getaccel)|擷取使用微調按鈕控制項的加速資訊。|
|[CSpinButtonCtrl::GetBase](#getbase)|擷取使用微調按鈕控制項的目前基底。|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|擷取目前的協同視窗的指標。|
|[CSpinButtonCtrl::GetPos](#getpos)|擷取使用微調按鈕控制項的目前位置。|
|[CSpinButtonCtrl::GetRange](#getrange)|擷取的上限和下限限制 （範圍） 使用微調按鈕控制項。|
|[CSpinButtonCtrl::SetAccel](#setaccel)|設定使用微調按鈕控制項加速。|
|[CSpinButtonCtrl::SetBase](#setbase)|設定為使用微調按鈕控制項的基底。|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|設定使用微調按鈕控制項的協同視窗。|
|[CSpinButtonCtrl::SetPos](#setpos)|設定控制項的目前位置。|
|[CSpinButtonCtrl::SetRange](#setrange)|設定上限與下限 （範圍） 的使用微調按鈕控制項。|

## <a name="remarks"></a>備註

「 微調按鈕控制項 」 （也稱為上下按鈕控制項） 是一對箭號按鈕，使用者可以按一下以遞增或遞減值，例如捲動位置或附屬控制項中顯示的數字。 微調按鈕控制項相關聯的值會呼叫其目前的位置。 微調按鈕控制項最常搭配附屬控制項稱為 「 協同視窗 」。

這個控制項 (並因此`CSpinButtonCtrl`類別) 僅適用於 Windows 95/98 和 Windows NT 版 3.51 下執行的程式和更新版本。

給使用者，微調按鈕控制項和協同視窗通常看起來像單一的控制項。 您可以指定的微調按鈕控制項自動定位本身及其協同視窗旁邊，以及它會自動設定為其目前位置的協同視窗的標題。 您可以使用與編輯控制項的使用微調按鈕控制項來提示使用者輸入數字。

按一下向上箭頭移往最大值，目前的位置，並按一下向下箭號移到最小值的目前位置。 根據預設，最小值為 100 而上限則為 0。 最小設定是超過最大值設定 （例如，當使用預設設定），按一下向上箭號減少任何時間的位置值，然後按一下向下箭號會遞增。

微調按鈕控制項而不需要協同視窗函式做為一種簡化的捲軸。 例如，索引標籤控制項有時會顯示微調按鈕控制項，讓使用者捲動至檢視的其他索引標籤。

如需有關使用`CSpinButtonCtrl`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)並[使用 CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="create"></a>  CSpinButtonCtrl::Create

建立使用微調按鈕控制項，並將它附加至`CSpinButtonCtrl`物件...

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定微調按鈕控制項的樣式。 套用至控制項的任何微調按鈕控制項的樣式的組合。 這些樣式所述[上下按鈕控制項的樣式](/windows/desktop/Controls/up-down-control-styles)Windows SDK 中。

*rect*<br/>
指定微調按鈕控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構

*pParentWnd*<br/>
微調按鈕控制項的父視窗，通常的指標`CDialog`。 它必須不是 NULL。

*nID*<br/>
指定微調按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

非零值，如果初始化成功;否則為 0。

### <a name="remarks"></a>備註

您建構`CSpinButtonCtrl`物件在兩個步驟中第一次，呼叫建構函式，並接著呼叫`Create`，這會建立微調按鈕控制項，並將它附加至`CSpinButtonCtrl`物件。

若要建立延伸的視窗樣式使用微調按鈕控制項，呼叫[CSpinButtonCtrl::CreateEx](#createex)而不是`Create`。

##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx

建立控制項 （子視窗），並將它與關聯`CSpinButtonCtrl`物件。

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
指定正在建立之控制項的延伸的樣式。 如需擴充的 windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*dwStyle*<br/>
指定微調按鈕控制項的樣式。 套用至控制項的任何微調按鈕控制項的樣式的組合。 這些樣式所述[上下按鈕控制項的樣式](/windows/desktop/Controls/up-down-control-styles)Windows SDK 中。

*rect*<br/>
參考[RECT](/previous-versions/dd162897\(v=vs.85\))結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。

*pParentWnd*<br/>
是控制項的父視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而非[建立](#create)套用延伸的 Windows 樣式的 Windows 延伸的樣式前置詞 WS_EX_ 所指定。

##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl

建構 `CSpinButtonCtrl` 物件。

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

擷取使用微調按鈕控制項的加速資訊。

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>參數

*nAccel*<br/>
所指定之陣列中的項目數*pAccel*。

*pAccel*<br/>
陣列的指標[UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel)接收加速資訊的結構。

### <a name="return-value"></a>傳回值

擷取的加速器結構數目。

##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase

擷取使用微調按鈕控制項的目前基底。

```
UINT GetBase() const;
```

### <a name="return-value"></a>傳回值

目前的基底值。

##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy

擷取目前的協同視窗的指標。

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>傳回值

目前的協同視窗的指標。

##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos

擷取使用微調按鈕控制項的目前位置。

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>參數

*lpbError*<br/>
布林值，設為零值的指標是已成功擷取或非零發生錯誤。 如果此參數設為 NULL 時，不會報告錯誤。

### <a name="return-value"></a>傳回值

第一個版本會傳回低序位字組中的 16 位元目前位置。 高序位文字不是零，如果發生錯誤。

第二個版本會傳回 32 位元位置。

### <a name="remarks"></a>備註

當它處理傳回的值時，控制項就會更新為基礎的協同視窗標題的目前位置。 如果沒有任何協同視窗，或標題指定為無效或超出範圍的值，控制項就會傳回錯誤。

##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange

擷取的上限和下限限制 （範圍） 使用微調按鈕控制項。

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

*lower*<br/>
接收控制項的下限為整數的參考。

*upper*<br/>
接收控制項的最高上限的整數的參考。

### <a name="return-value"></a>傳回值

第一個版本會傳回 32 位元值，包含上限與下限。 低序位文字控制項，上限而高序位文字較低的限制。

### <a name="remarks"></a>備註

此成員函式`GetRange32`擷取為 32 位元整數的微調按鈕控制項的範圍。

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

設定使用微調按鈕控制項加速。

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>參數

*nAccel*<br/>
數目[UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel)所指定的結構*pAccel*。

*pAccel*<br/>
UDACCEL 結構，其中包含加速資訊陣列的指標。 項目應該依照遞增順序是根據`nSec`成員。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase

設定為使用微調按鈕控制項的基底。

```
int SetBase(int nBase);
```

### <a name="parameters"></a>參數

*nBase*<br/>
新控制項的基底值。 它可以是十進位的 10 或 16 個十六進位。

### <a name="return-value"></a>傳回值

先前的基底值，如果成功或如果指定了無效的基底的零。

### <a name="remarks"></a>備註

基底值會決定是否協同視窗會顯示十進位或十六進位的數字的數字。 十六進位數字都不帶正負號;十進位數字會進行簽署。

##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy

設定使用微調按鈕控制項的協同視窗。

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>參數

*pWndBuddy*<br/>
新的協同視窗的指標。

### <a name="return-value"></a>傳回值

先前的協同視窗的指標。

### <a name="remarks"></a>備註

微調控制項幾乎都是與另一個視窗中，例如編輯控制項，會顯示某些內容相關聯。 這個其他視窗稱為 「 夥伴 」 的微調控制項。

##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos

設定使用微調按鈕控制項的目前位置。

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
控制項的新位置。 此值必須是在控制項上限與下限所指定的範圍。

### <a name="return-value"></a>傳回值

先前的位置 (16 位元的整數位數`SetPos`32 位元的有效位數`SetPos32`)。

### <a name="remarks"></a>備註

`SetPos32` 設定 32 位元位置。

##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange

設定上限與下限 （範圍） 的使用微調按鈕控制項。

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
上限與下限的控制項。 針對`SetRange`、 未限制可能會大於 UD_MAXVAL 或小於 UD_MINVAL; 此外，兩個限制之間的差異不能超過 UD_MAXVAL。 `SetRange32` 沒有任何限制置於限制;使用任何整數。

### <a name="remarks"></a>備註

此成員函式`SetRange32`設定微調按鈕控制項的 32 位元範圍。

> [!NOTE]
>  微調按鈕的預設範圍具有最大值為零 (0) 和最小值為 100。 因為最大值小於最小值，按一下向上箭號會減少的位置，並按一下向下箭號，將可增加它。 使用`CSpinButtonCtrl::SetRange`調整這些值。

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl 類別](../../mfc/reference/csliderctrl-class.md)
