---
title: CAnimationRect 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
ms.openlocfilehash: 273ea2b548d35722ebf937d2db2b589fef5e69fa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755131"
---
# <a name="canimationrect-class"></a>CAnimationRect 類別

實作可以動畫顯示其邊緣的矩形功能。

## <a name="syntax"></a>語法

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[動畫重器::動畫Rect](#canimationrect)|已多載。 構造動畫矩形物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫重器::新增轉換](#addtransition)|添加左、上、右和下座標的過渡。|
|[動畫重器::取得底部](#getbottom)|提供對表示底部座標的 CAnimation 變數的訪問。|
|[動畫重: :取得預設值](#getdefaultvalue)|返回矩形邊界的預設值。|
|[動畫重器::取得左](#getleft)|提供對表示左座標的 CAnimation 變數的訪問。|
|[動畫重: :獲得正確](#getright)|提供對表示正確座標的 CAnimation 變數的訪問。|
|[動畫重器::取得頂部](#gettop)|提供對表示頂部座標的 CAnimation 變數的訪問。|
|[動畫重器::取得價值](#getvalue)|返回當前值。|
|[動畫重定::設定預設值](#setdefaultvalue)|設置預設值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[動畫重: :抓取動畫變數清單](#getanimationvariablelist)|將封裝的動畫變數放入清單中。 ( 覆[寫動畫基礎物件:抓取動畫變數列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[動畫重器::操作員 RECT](#operator_rect)|將 C 動畫 Rect 轉換為 RECT。|
|[動畫重器::運算符*](#operator_eq)|將矩形分配給 CAnimationRect。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[動畫::m_bFixedSize](#m_bfixedsize)|指定矩形是否具有固定大小。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[動畫重器::m_bottomValue](#m_bottomvalue)|表示動畫矩形底部邊界的封裝動畫變數。|
|[動畫::m_leftValue](#m_leftvalue)|表示動畫矩形左邊界的封裝動畫變數。|
|[動畫重器::m_rightValue](#m_rightvalue)|表示動畫矩形右邊界的封裝動畫變數。|
|[動畫重器::m_szInitial](#m_szinitial)|指定動畫矩形的初始大小。|
|[動畫重器::m_topValue](#m_topvalue)|表示動畫矩形的「頂部」邊界的封裝動畫變數。|

## <a name="remarks"></a>備註

CAnimationRect 類封裝了四個 CAnimationvariable 物件,可以在應用程式中表示一個矩形。 要在應用程式中使用此類,只需實例化此類的物件,請使用 CAnimationController::addAnimationObject 將其添加到動畫控制器,並調用 AddTransition,以便應用於左、右上和下座標的每個轉換。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[動畫基礎物件](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationrectaddtransition"></a><a name="addtransition"></a>動畫重器::新增轉換

添加左、上、右和下座標的過渡。

```cpp
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>參數

*p 左轉換*<br/>
指定左側的過渡。

*p 上轉換*<br/>
指定頂部的過渡。

*pRight 轉換*<br/>
指定右側的過渡。

*p 底轉換*<br/>
指定下邊的過渡。

### <a name="remarks"></a>備註

呼叫此函數以將指定的過渡添加到要應用於每個矩形邊的動畫變數的內部過渡清單中。 添加轉換時,不會立即應用這些轉換並存儲在內部清單中。 當您調用 CAnimationController::AnimateGroup 時,將應用轉換(添加到特定值的情節提要中)。 如果不需要對矩形的一個邊應用過渡,則可以傳遞 NULL。

## <a name="canimationrectcanimationrect"></a><a name="canimationrect"></a>動畫重器::動畫Rect

建構 CAnimationRect 物件。

```
CAnimationRect();

CAnimationRect(
    const CRect& rect,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    const CPoint& pt,
    const CSize& sz,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    int nLeft,
    int nTop,
    int nRight,
    int nBottom,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*矩形*<br/>
指定預設矩形。

*n集團ID*<br/>
指定組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
指定使用者定義的數據。

*pt*<br/>
左上角的座標。

*深圳*<br/>
矩形的大小。

*N 左*<br/>
指定左繫定的座標。

*nTop*<br/>
指定上綁定的座標。

*nRight*<br/>
指定右繫定的座標。

*N 下角*<br/>
指定下綁定的座標。

### <a name="remarks"></a>備註

對象建構的預設值為左、上、右和下,對象 ID 和組 ID,將設置為 0。 可以使用 SetDefaultValue 和 SetID 在運行時稍後更改它們。

## <a name="canimationrectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>動畫重: :抓取動畫變數清單

將封裝的動畫變數放入清單中。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>參數

*Lst*<br/>
當函數返回時,它包含指向表示矩形座標的四個 CAnimation 變數物件的指標。

## <a name="canimationrectgetbottom"></a><a name="getbottom"></a>動畫重器::取得底部

提供對表示底部座標的 CAnimation 變數的訪問。

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>傳回值

表示底部座標的封裝 CAnimation 變數的引用。

### <a name="remarks"></a>備註

您可以調用此方法來直接訪問表示底部座標的基礎 C動畫變數。

## <a name="canimationrectgetdefaultvalue"></a><a name="getdefaultvalue"></a>動畫重: :取得預設值

返回矩形邊界的預設值。

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>傳回值

包含左、右、上和下預設值的 CRect 值。

### <a name="remarks"></a>備註

調用此函數以檢索以前由建構函數或 SetDefaultValue 設置的預設值。

## <a name="canimationrectgetleft"></a><a name="getleft"></a>動畫重器::取得左

提供對表示左座標的 CAnimation 變數的訪問。

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>傳回值

表示左座標的封裝 CAnimation 變數的引用。

### <a name="remarks"></a>備註

您可以調用此方法以直接訪問表示左側座標的基礎 C動畫變數。

## <a name="canimationrectgetright"></a><a name="getright"></a>動畫重: :獲得正確

提供對表示正確座標的 CAnimation 變數的訪問。

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>傳回值

對表示正確座標的封裝的 CAnimation 的引用。

### <a name="remarks"></a>備註

您可以調用此方法來直接訪問表示正確座標的基礎 C動畫變數。

## <a name="canimationrectgettop"></a><a name="gettop"></a>動畫重器::取得頂部

提供對表示頂部座標的 CAnimation 變數的訪問。

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>傳回值

表示頂部座標的封裝 CAnimation 變數的引用。

### <a name="remarks"></a>備註

您可以調用此方法來直接訪問表示頂部座標的基礎 C動畫變數。

## <a name="canimationrectgetvalue"></a><a name="getvalue"></a>動畫重器::取得價值

返回當前值。

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>參數

*矩形*<br/>
輸出。 當此方法返回時,包含當前值。

### <a name="return-value"></a>傳回值

TRUE,如果成功檢索當前值;如果成功檢索當前值,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

呼叫此函數以檢索動畫矩形的當前值。 如果此方法失敗或左、上、右和下的基礎 COM 物件尚未初始化,則 rect 包含預設值,該值以前在構造函數或 SetDefaultValue 中設置。

## <a name="canimationrectm_bfixedsize"></a><a name="m_bfixedsize"></a>動畫::m_bFixedSize

指定矩形是否具有固定大小。

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>備註

如果此成員為 true,則矩形的大小是固定的,並且每次根據固定大小移動左上角時都會重新計算右和下值。 將此值設定為 TRUE 以輕鬆地在螢幕上移動矩形。 在這種情況下,將忽略應用於右座標和底部座標的過渡。 當您建構物件和/或呼叫 SetDefaultValue 時,大小儲存在內部。 默認情況下,此成員設置為 FALSE。

## <a name="canimationrectm_bottomvalue"></a><a name="m_bottomvalue"></a>動畫重器::m_bottomValue

表示動畫矩形底部邊界的封裝動畫變數。

```
CAnimationVariable m_bottomValue;
```

## <a name="canimationrectm_leftvalue"></a><a name="m_leftvalue"></a>動畫::m_leftValue

表示動畫矩形左邊界的封裝動畫變數。

```
CAnimationVariable m_leftValue;
```

## <a name="canimationrectm_rightvalue"></a><a name="m_rightvalue"></a>動畫重器::m_rightValue

表示動畫矩形右邊界的封裝動畫變數。

```
CAnimationVariable m_rightValue;
```

## <a name="canimationrectm_szinitial"></a><a name="m_szinitial"></a>動畫重器::m_szInitial

指定動畫矩形的初始大小。

```
CSize m_szInitial;
```

## <a name="canimationrectm_topvalue"></a><a name="m_topvalue"></a>動畫重器::m_topValue

表示動畫矩形的「頂部」邊界的封裝動畫變數。

```
CAnimationVariable m_topValue;
```

## <a name="canimationrectoperator-rect"></a><a name="operator_rect"></a>動畫重器::操作員 RECT

將 C 動畫 Rect 轉換為 RECT。

```
operator RECT();
```

### <a name="return-value"></a>傳回值

動畫矩形作為 RECT 的當前值。

### <a name="remarks"></a>備註

此功能在內部調用 GetValue。 如果由於某種原因 GetValue 失敗,則返回的 RECT 將包含所有矩形座標的預設值。

## <a name="canimationrectoperator"></a><a name="operator_eq"></a>動畫重器::運算符*

將矩形分配給 CAnimationRect。

```cpp
void operator=(const RECT& rect);
```

### <a name="parameters"></a>參數

*矩形*<br/>
動畫矩形的新值。

### <a name="remarks"></a>備註

建議在動畫啟動之前執行此操作,因為此運算符稱為 SetDefaultValue,如果已創建顏色元件,則重新創建顏色元件的基礎 COM 物件。 如果將此動畫物件訂閱到事件(Value已更改或整數值更改),則需要重新啟用這些事件。

## <a name="canimationrectsetdefaultvalue"></a><a name="setdefaultvalue"></a>動畫重定::設定預設值

設置預設值。

```cpp
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>參數

*矩形*<br/>
為左、上、右和下指定新的預設值。

### <a name="remarks"></a>備註

使用此函數可為動畫物件設置預設值。 此方法將預設值分配給矩形的邊界。 它還會重新創建基礎 COM 物件(如果已創建)。 如果將此動畫物件訂閱到事件(Value已更改或整數值更改),則需要重新啟用這些事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
