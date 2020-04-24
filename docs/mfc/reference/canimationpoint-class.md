---
title: CAnimationPoint 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
ms.openlocfilehash: fcdd07efb46c97d27a9f1349c297688b5705f176
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755148"
---
# <a name="canimationpoint-class"></a>CAnimationPoint 類別

實作可以動畫顯示其座標的點功能。

## <a name="syntax"></a>語法

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[動畫點:動畫點](#canimationpoint)|已多載。 建構 CAnimationPoint 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫點::新增轉換](#addtransition)|添加 X 和 Y 座標的過渡。|
|[動畫點:取得預設值](#getdefaultvalue)|傳回 X 和 Y 座標的預設值。|
|[動畫點:取得價值](#getvalue)|返回當前值。|
|[動畫點:GetX](#getx)|提供 X 座標對 CAnimation 變數的訪問。|
|[動畫點:取得 Y](#gety)|提供對 Y 座標的 CAnimation 變數的訪問。|
|[動畫點::設定預設值](#setdefaultvalue)|設置預設值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[動畫點::取得動畫變數清單](#getanimationvariablelist)|將封裝的動畫變數放入清單中。 ( 覆[寫動畫基礎物件:抓取動畫變數列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[動畫點::運算符 CPoint](#operator_cpoint)|將 C動畫點轉換為 CPoint。|
|[動畫點::操作員*](#operator_eq)|將 ptSrc 分配給 C 動畫點。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[動畫點:m_xValue](#m_xvalue)|表示動畫點的 X 座標的封裝動畫變數。|
|[動畫點:m_yValue](#m_yvalue)|表示動畫點的 Y 座標的封裝動畫變數。|

## <a name="remarks"></a>備註

CAnimationPoint 類封裝了兩個 CAnimationvariable 物件,可以在應用程式中表示一個點。 例如,可以使用此類為螢幕上任何物件的位置(如文本字串、圓圈、點等)設置動畫。 要在應用程式中使用此類,只需實例化此類的物件,請使用 CAnimationController::addAnimationObject 將其添加到動畫控制器,並調用 AddTransition,以便應用於 X 和/或 Y 座標的每個轉換。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[動畫基礎物件](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationpointaddtransition"></a><a name="addtransition"></a>動畫點::新增轉換

添加 X 和 Y 座標的過渡。

```cpp
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>參數

*pX 轉換*<br/>
X 座標的轉換指標。

*pY 轉換*<br/>
Y 座標的轉換指標。

### <a name="remarks"></a>備註

呼叫此函數以將指定的過渡添加到要應用於 X 和 Y 座標的動畫變數的內部過渡清單中。 添加轉換時,不會立即應用這些轉換並存儲在內部清單中。 當您調用 CAnimationController::AnimateGroup 時,將應用轉換(添加到特定值的情節提要中)。 如果不需要將轉換應用於其中一個座標,則可以傳遞 NULL。

## <a name="canimationpointcanimationpoint"></a><a name="canimationpoint"></a>動畫點:動畫點

建構 CAnimationPoint 物件。

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*ptDefault*<br/>
指定預設點座標。

*n集團ID*<br/>
指定組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
指定使用者定義的數據。

### <a name="remarks"></a>備註

建構具有預設屬性的 CAnimationPoint 物件:預設點座標、組 ID 和物件 ID 設置為 0。

## <a name="canimationpointgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>動畫點::取得動畫變數清單

將封裝的動畫變數放入清單中。

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>參數

*Lst*<br/>
當函數返回時,它包含指向表示 X 和 Y 座標的兩個 CAnimation 變數物件的指標。

## <a name="canimationpointgetdefaultvalue"></a><a name="getdefaultvalue"></a>動畫點:取得預設值

傳回 X 和 Y 座標的預設值。

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>傳回值

包含預設值的點。

### <a name="remarks"></a>備註

調用此函數以檢索以前由建構函數或 SetDefaultValue 設置的預設值。

## <a name="canimationpointgetvalue"></a><a name="getvalue"></a>動畫點:取得價值

返回當前值。

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>參數

*ptValue*<br/>
輸出。 當此方法返回時,包含當前值。

### <a name="return-value"></a>傳回值

TRUE,如果成功檢索當前值;如果成功檢索當前值,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

調用此函數以檢索動畫點的當前值。 如果此方法失敗或 X 和 Y 座標的基礎 COM 物件尚未初始化,則 ptValue 包含預設值,該值以前在建構函數或 SetDefaultValue 中設置。

## <a name="canimationpointgetx"></a><a name="getx"></a>動畫點:GetX

提供 X 座標對 CAnimation 變數的訪問。

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>傳回值

表示 X 座標的封裝 CAnimation 變數的引用。

### <a name="remarks"></a>備註

可以調用此方法以直接訪問表示 X 座標的基礎 C動畫變數。

## <a name="canimationpointgety"></a><a name="gety"></a>動畫點:取得 Y

提供對 Y 座標的 CAnimation 變數的訪問。

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>傳回值

表示 Y 座標的封裝 CAnimation 變數的引用。

### <a name="remarks"></a>備註

可以調用此方法以直接訪問表示 Y 座標的基礎 C動畫變數。

## <a name="canimationpointm_xvalue"></a><a name="m_xvalue"></a>動畫點:m_xValue

表示動畫點的 X 座標的封裝動畫變數。

```
CAnimationVariable m_xValue;
```

## <a name="canimationpointm_yvalue"></a><a name="m_yvalue"></a>動畫點:m_yValue

表示動畫點的 Y 座標的封裝動畫變數。

```
CAnimationVariable m_yValue;
```

## <a name="canimationpointoperator-cpoint"></a><a name="operator_cpoint"></a>動畫點::運算符 CPoint

將 C動畫點轉換為 CPoint。

```
operator CPoint();
```

### <a name="return-value"></a>傳回值

CAnimationPoint 作為 CPoint 的當前值。

### <a name="remarks"></a>備註

此功能在內部調用 GetValue。 如果由於某種原因 GetValue 失敗,則返回的點將包含 X 和 Y 座標的預設值。

## <a name="canimationpointoperator"></a><a name="operator_eq"></a>動畫點::操作員*

將 ptSrc 分配給 C 動畫點。

```cpp
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>參數

*ptSrc*<br/>
指 CPoint 或 POINT。

### <a name="remarks"></a>備註

將 ptSrc 分配給 C 動畫點。 建議在動畫啟動之前執行此操作,因為此運算符呼叫 SetDefaultValue,如果已建立 X 和 Y 座標,則重新建立 X 和 Y 座標的基礎 COM 物件。 如果將此動畫物件訂閱到事件(Value已更改或整數值更改),則需要重新啟用這些事件。

## <a name="canimationpointsetdefaultvalue"></a><a name="setdefaultvalue"></a>動畫點::設定預設值

設置預設值。

```cpp
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>參數

*ptDefault*<br/>
指定預設點值。

### <a name="remarks"></a>備註

使用此函數可為動畫物件設置預設值。 此方法將預設值分配給動畫點的 X 和 Y 座標。 它還會重新創建基礎 COM 物件(如果已創建)。 如果將此動畫物件訂閱到事件(Value已更改或整數值更改),則需要重新啟用這些事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
