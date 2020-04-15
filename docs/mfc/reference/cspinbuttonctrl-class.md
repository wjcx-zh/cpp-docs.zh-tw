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
ms.openlocfilehash: 4230d43bad8bcc15bcb26aaf0357e70216909ba1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318131"
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
|[CSpinButtonCtrl::CspinButtonCtrl](#cspinbuttonctrl)|建構 `CSpinButtonCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSpinButtonCtrl::建立](#create)|創建旋轉按鈕控制項並將其附加到`CSpinButtonCtrl`物件。|
|[CSpinButtonCtrl::創建Ex](#createex)|使用指定的 Windows 擴充樣式創建旋轉按鈕控制項,並將`CSpinButtonCtrl`其附加到 物件。|
|[CSpinButtonctrl::GetAccel](#getaccel)|檢索旋轉按鈕控制件的加速資訊。|
|[CSpinButtonCtrl:取得基礎](#getbase)|檢索旋轉按鈕控件的當前底座。|
|[CSpinButtonctrl:GetBuddy](#getbuddy)|檢索指向當前好友視窗的指標。|
|[CSpinButtonctrl:getPos](#getpos)|檢索旋轉按鈕控制件的當前位置。|
|[CSpinButtonCtrl:取得範圍](#getrange)|檢索旋轉按鈕控制件的上限和下限(範圍)。|
|[CSpinButtonctrl::SetAccel](#setaccel)|設置旋轉按鈕控制項的加速度。|
|[CSpinButtonctrl::設定基](#setbase)|設置旋轉按鈕控制的基礎。|
|[CSpinButtonctrl::SetBuddy](#setbuddy)|設置旋轉按鈕控制件的好友視窗。|
|[CSpinButtonctrl::SetPos](#setpos)|設置控制項的目前位置。|
|[CSpinButtonctrl::設定範圍](#setrange)|設置旋轉按鈕控制項的上限和下限(範圍)。|

## <a name="remarks"></a>備註

"旋轉按鈕控制件"(也稱為向上向下控制項)是一對箭頭按鈕,用戶可以按下該按鈕以遞增或遞減值,例如滾動位置或配套控件中顯示的數位。 與旋轉按鈕控制項關聯的值稱為其當前位置。 旋轉按鈕控制項最常與稱為「好友視窗」的配套控制件一起使用。

此控制項(因此該`CSpinButtonCtrl`類別)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

對使用者,旋轉按鈕控制件及其好友視窗通常看起來像單個控制項。 您可以指定旋轉按鈕控制程式會自動將其定位在其好友視窗旁邊,並且它會自動將好友視窗的標題設置為其當前位置。 您可以將旋轉按鈕控制件與編輯控制項一起提示使用者輸入數位。

按下向上箭頭將當前位置向最大值移動,按下向下箭頭將當前位置向最小值移動。 默認情況下,最小值為 100,最大值為 0。 每當最小設置大於最大設置(例如,使用預設設置時),單擊向上箭頭會減小位置值,按一下向下箭頭會增加位置值。

沒有好友視窗的旋轉按鈕控制項可充當一種簡化的滾動條。 例如,選項卡控制項有時會顯示旋轉按鈕控制項,使用戶能夠將其他選項卡滾動到檢視中。

有關`CSpinButtonCtrl`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)[與使用 CspinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl::建立

創建旋轉按鈕控制項並將其附加到`CSpinButtonCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定旋轉按鈕控制件的樣式。 將旋轉按鈕控制樣式的任意組合應用於控制項。 這些樣式在 Windows SDK 中的[「向上向下控制樣式」](/windows/win32/Controls/up-down-control-styles)中描述。

*矩形*<br/>
指定旋轉按鈕控制項大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構

*pparentwnd*<br/>
指向旋轉按鈕控制的父視窗(通常為的指標`CDialog`) 的指標。 它不得為 NULL。

*nID*<br/>
指定旋轉按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

初始化成功時非零;否則 0。

### <a name="remarks"></a>備註

先分兩`CSpinButtonCtrl`個步驟構造對象,調用構造函數,然後`Create`調用 ,這將創建旋轉按鈕控制項並將`CSpinButtonCtrl`其附加到 物件。

要建立式延伸視窗樣式的旋轉按鈕控制項,請呼叫[CSpinButtonCtrl::createEx](#createex)而不是`Create`。

## <a name="cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl::創建Ex

創建控制項(子視窗),並將其與`CSpinButtonCtrl`物件關聯。

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
指定要創建的控制項的擴充樣式。 有關擴展視窗樣式的清單,請參閱 Windows SDK 中創建[WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定旋轉按鈕控制件的樣式。 將旋轉按鈕控制樣式的任意組合應用於控制項。 這些樣式在 Windows SDK 中的[「向上向下控制樣式」](/windows/win32/Controls/up-down-control-styles)中描述。

*矩形*<br/>
對[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用 Windows 擴充樣式WS_EX_指定擴展的 Windows 樣式。

## <a name="cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CspinButtonCtrl

建構 `CSpinButtonCtrl` 物件。

```
CSpinButtonCtrl();
```

## <a name="cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonctrl::GetAccel

檢索旋轉按鈕控制件的加速資訊。

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>參數

*nAccel*<br/>
*pAccel*指定的陣列中的元素數。

*pAccel*<br/>
指向接收加速資訊的[UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel)結構陣列的指標。

### <a name="return-value"></a>傳回值

檢索的加速器結構數。

## <a name="cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl:取得基礎

檢索旋轉按鈕控件的當前底座。

```
UINT GetBase() const;
```

### <a name="return-value"></a>傳回值

當前基值。

## <a name="cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonctrl:GetBuddy

檢索指向當前好友視窗的指標。

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>傳回值

指向當前好友視窗的指標。

## <a name="cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonctrl:getPos

檢索旋轉按鈕控制件的當前位置。

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>參數

*lpbError*<br/>
指向布爾值的指標,如果成功檢索該值,則設置為零;如果發生錯誤,則設置為非零。 如果此參數設定為 NULL,則不報告錯誤。

### <a name="return-value"></a>傳回值

第一個版本返回低階單詞中的 16 位當前位置。 如果發生錯誤,高階單詞為非零。

第二個版本返回 32 位元位置。

### <a name="remarks"></a>備註

處理返回的值時,控件會根據好友視窗的標題更新其當前位置。 如果沒有好友視窗或標題指定無效或範圍外值,則控件將返回錯誤。

## <a name="cspinbuttonctrlgetrange"></a><a name="getrange"></a>CSpinButtonCtrl:取得範圍

檢索旋轉按鈕控制件的上限和下限(範圍)。

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

*降低*<br/>
引用接收控制項下限的整數。

*上*<br/>
引用接收控制項上限的整數。

### <a name="return-value"></a>傳回值

第一個版本返回包含上限和下限的 32 位值。 低階詞是控件的上限,高階詞是下限。

### <a name="remarks"></a>備註

成員函數`GetRange32`檢索旋轉按鈕控制項的範圍作為32位整數。

## <a name="cspinbuttonctrlsetaccel"></a><a name="setaccel"></a>CSpinButtonctrl::SetAccel

設置旋轉按鈕控制項的加速度。

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>參數

*nAccel*<br/>
*pAccel*指定的[UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel)結構數。

*pAccel*<br/>
指向包含加速度資訊的UDACCEL結構陣列的指標。 元素應依遞增順序的成員排`nSec`序 。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="cspinbuttonctrlsetbase"></a><a name="setbase"></a>CSpinButtonctrl::設定基

設置旋轉按鈕控制的基礎。

```
int SetBase(int nBase);
```

### <a name="parameters"></a>參數

*nBase*<br/>
控件的新基值。 十進位可以是10,十進位也可以是16,十六進位為十六進制。

### <a name="return-value"></a>傳回值

如果成功,則上一個基值;如果給定無效基,則為零。

### <a name="remarks"></a>備註

基值確定好友視窗是以十進位數位還是十六進位數字顯示數位。 十六進位數字始終未簽名;十進位數位已簽名。

## <a name="cspinbuttonctrlsetbuddy"></a><a name="setbuddy"></a>CSpinButtonctrl::SetBuddy

設置旋轉按鈕控制件的好友視窗。

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>參數

*普恩德布迪*<br/>
指向新好友視窗的指標。

### <a name="return-value"></a>傳回值

指向上一個好友視窗的指標。

### <a name="remarks"></a>備註

旋轉控制項幾乎總是與另一個視窗(如編輯控制件)相關聯,該視窗顯示某些內容。 此另一個窗口稱為自旋控制件的「夥伴」。

## <a name="cspinbuttonctrlsetpos"></a><a name="setpos"></a>CSpinButtonctrl::SetPos

設置旋轉按鈕控制的當前位置。

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
控件的新位置。 此值必須位於控制項的上限和下限指定的範圍內。

### <a name="return-value"></a>傳回值

上一個位置(16 位元精`SetPos`度`SetPos32`, 為 32 位精度)。

### <a name="remarks"></a>備註

`SetPos32`設置 32 位位置。

## <a name="cspinbuttonctrlsetrange"></a><a name="setrange"></a>CSpinButtonctrl::設定範圍

設置旋轉按鈕控制項的上限和下限(範圍)。

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>參數

*N 下部*與*nUpper*<br/>
控件的上限和下限。 對於`SetRange`,兩個限制都不能大於UD_MAXVAL或小於UD_MINVAL;此外,兩個限制之間的差異不能超過UD_MAXVAL。 `SetRange32`對限制沒有限制;使用任何整數。

### <a name="remarks"></a>備註

成員函數`SetRange32`為旋轉按鈕控制項設置32位範圍。

> [!NOTE]
> 旋轉按鈕的預設範圍的最大設置為零 (0),最小設置為 100。 由於最大值小於最小值,按一下向上箭頭將減小位置,按下向下箭頭將增加該位置。 用於`CSpinButtonCtrl::SetRange`調整這些值。

## <a name="see-also"></a>另請參閱

[MFC 樣品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl 類別](../../mfc/reference/csliderctrl-class.md)
