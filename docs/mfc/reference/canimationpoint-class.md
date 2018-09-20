---
title: CAnimationPoint 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b584902a1eb9b3c1aba27645e084ad6ea23cb72
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404835"
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
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|多載。 建構 CAnimationPoint 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|將轉換的 X 和 Y 座標。|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|傳回的預設值的 X 和 Y 座標。|
|[CAnimationPoint::GetValue](#getvalue)|傳回目前的值。|
|[CAnimationPoint::GetX](#getx)|提供存取 CAnimationVariable 的 X 座標。|
|[CAnimationPoint::GetY](#gety)|CAnimationVariable 可存取的 Y 座標。|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|設定預設值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|將封裝的動畫變數放入清單中。 (覆寫[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAnimationPoint::operator CPoint](#operator_cpoint)|將 CPoint CAnimationPoint。|
|[CAnimationPoint::operator =](#operator_eq)|給 CAnimationPoint ptSrc。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|表示 X 之封裝的動畫變數的動畫點座標。|
|[CAnimationPoint::m_yValue](#m_yvalue)|封裝的動畫變數，表示動畫點的 Y 座標。|

## <a name="remarks"></a>備註

CAnimationPoint 類別包含兩個 CAnimationVariable 物件，並可以代表應用程式中點。 例如，您可以使用這個類別以動畫顯示的位置 （例如文字字串、 圓形、 點等等），螢幕上的任何物件。 若要在應用程式中使用這個類別，只要具現化這個類別的物件、 將它新增至使用 CAnimationController::AddAnimationObject 的動畫控制器，並呼叫 AddTransition 針對每個轉換套用到 X 及/或 Y 座標。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationPoint::AddTransition

將轉換的 X 和 Y 座標。

```
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>參數

*pXTransition*<br/>
要轉換的 X 座標指標。

*pYTransition*<br/>
指標轉換的 Y 座標。

### <a name="remarks"></a>備註

呼叫此函式，將指定的轉換加入內部清單的轉換套用至動畫變數 x 和 Y 座標。 當您新增轉換時，它們就會不立即套用，並儲存在內部清單。 轉換會套用 （加入至特定值如分鏡腳本） 當您呼叫 CAnimationController::AnimateGroup。 如果您不需要將轉換套用到其中一個座標，您可以傳遞 NULL。

##  <a name="canimationpoint"></a>  CAnimationPoint::CAnimationPoint

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

*nGroupID*<br/>
指定群組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
指定使用者定義的資料。

### <a name="remarks"></a>備註

建構具有預設屬性的 CAnimationPoint 物件： 預設點座標，群組識別碼和物件識別碼會設定為 0。

##  <a name="getanimationvariablelist"></a>  CAnimationPoint::GetAnimationVariableList

將封裝的動畫變數放入清單中。

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>參數

*lst*<br/>
當函式傳回時，它會包含代表 X 和 Y 座標的兩個 CAnimationVariable 物件的指標。

##  <a name="getdefaultvalue"></a>  CAnimationPoint::GetDefaultValue

傳回的預設值的 X 和 Y 座標。

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>傳回值

點包含預設值。

### <a name="remarks"></a>備註

呼叫此函式可擷取預設值，也就先前設定的建構函式或 SetDefaultValue。

##  <a name="getvalue"></a>  CAnimationPoint::GetValue

傳回目前的值。

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>參數

*ptValue*<br/>
輸出。 這個方法傳回時，包含目前的值。

### <a name="return-value"></a>傳回值

為 TRUE，如果已成功擷取目前的值;否則為 FALSE。

### <a name="remarks"></a>備註

呼叫此函式以擷取動畫點的目前值。 如果此方法失敗或基礎 COM 物件 x 和 Y 座標尚未初始化，ptValue 會包含在建構函式或 SetDefaultValue 先前設定的預設值。

##  <a name="getx"></a>  CAnimationPoint::GetX

提供存取 CAnimationVariable 的 X 座標。

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>傳回值

參考封裝 CAnimationVariable 代表 X 座標。

### <a name="remarks"></a>備註

您可以呼叫此方法以直接存取基礎 CAnimationVariable 代表 X 座標。

##  <a name="gety"></a>  CAnimationPoint::GetY

CAnimationVariable 可存取的 Y 座標。

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>傳回值

表示 Y 座標的 CAnimationVariable 封裝參考。

### <a name="remarks"></a>備註

您可以呼叫此方法以直接存取基礎 CAnimationVariable 表示 Y 座標。

##  <a name="m_xvalue"></a>  CAnimationPoint::m_xValue

表示 X 之封裝的動畫變數的動畫點座標。

```
CAnimationVariable m_xValue;
```

##  <a name="m_yvalue"></a>  CAnimationPoint::m_yValue

封裝的動畫變數，表示動畫點的 Y 座標。

```
CAnimationVariable m_yValue;
```

##  <a name="operator_cpoint"></a>  CAnimationPoint::operator CPoint

將 CPoint CAnimationPoint。

```
operator CPoint();
```

### <a name="return-value"></a>傳回值

CAnimationPoint CPoint 為目前值。

### <a name="remarks"></a>備註

此函式會在內部呼叫 GetValue。 如果基於某些原因的 GetValue 失敗，傳回的點將會包含預設值 x 和 Y 座標。

##  <a name="operator_eq"></a>  CAnimationPoint::operator =

給 CAnimationPoint ptSrc。

```
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>參數

*ptSrc*<br/>
是指 CPoint 或點。

### <a name="remarks"></a>備註

給 CAnimationPoint ptSrc。 建議您執行的動畫開始之前此運算子會呼叫 SetDefaultValue，因為這會重新建立基礎 COM 物件 X 和 Y 座標如果尚未建立。 如果您訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。

##  <a name="setdefaultvalue"></a>  CAnimationPoint::SetDefaultValue

設定預設值。

```
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>參數

*ptDefault*<br/>
指定預設點值。

### <a name="remarks"></a>備註

此函式可用於設定動畫物件的預設值。 這個方法會指派預設值的動畫點的 X 和 Y 座標。 如果尚未建立，它也會重建基礎 COM 物件。 如果您訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
