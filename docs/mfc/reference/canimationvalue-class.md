---
title: CAnimationValue 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
ms.openlocfilehash: 86a2caa8946bcafeabf85687a24b2430ecefe790
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338684"
---
# <a name="canimationvalue-class"></a>CAnimationValue 類別

實作有一個值的動畫物件功能。

## <a name="syntax"></a>語法

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|多載。 建構 CAnimationValue 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|加入要套用至值的轉換。|
|[CAnimationValue::GetValue](#getvalue)|多載。 擷取目前的值。|
|[CAnimationValue::GetVariable](#getvariable)|提供封裝的動畫變數的存取。|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|設定預設值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|將封裝的動畫變數放入清單中。 (覆寫[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAnimationValue::operator 雙精度浮點數](#operator_double)|提供 CAnimationValue 和雙精度浮點數之間的轉換。|
|[CAnimationValue::operator INT32](#operator_int32)|提供 CAnimationValue 和 INT32 之間的轉換。|
|[CAnimationValue::operator=](#operator_eq)|多載。 給 CAnimationValue INT32 值。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|表示動畫值之封裝的動畫變數。|

## <a name="remarks"></a>備註

CAnimationValue 類別會封裝單一 CAnimationVariable 物件，並可代表應用程式中單一動畫的值。 例如，您可以使用這個類別的動畫的透明度 （淡出效果），角度 （以旋轉的物件），或任何其他情況時，您必須建立依據單一動畫值的動畫。 若要在應用程式中使用這個類別，只要具現化這個類別的物件、 將它新增至使用 CAnimationController::AddAnimationObject 的動畫控制器，並呼叫 AddTransition 針對每個轉換套用至值。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationValue::AddTransition

加入要套用至值的轉換。

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>參數

*pTransition*<br/>
轉換物件的指標。

### <a name="remarks"></a>備註

呼叫此函式可將轉換加入至轉換套用至動畫變數的內部清單。 當您新增轉換時，它們就會不立即套用，並儲存在內部清單。 轉換會套用 （加入至特定值如分鏡腳本） 當您呼叫 CAnimationController::AnimateGroup。

##  <a name="canimationvalue"></a>  CAnimationValue::CAnimationValue

建構 CAnimationValue 物件。

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*dblDefaultValue*<br/>
指定預設值。

*nGroupID*<br/>
指定群組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
指定使用者定義的資料。

### <a name="remarks"></a>備註

建構具有預設屬性的 CAnimationValue 物件： 預設值，群組識別碼和物件識別碼會設定為 0。

##  <a name="getanimationvariablelist"></a>  CAnimationValue::GetAnimationVariableList

將封裝的動畫變數放入清單中。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>參數

*lst*<br/>
函式傳回時，它會包含 CAnimationVariable 表示動畫的值的指標。

##  <a name="getvalue"></a>  CAnimationValue::GetValue

擷取目前的值。

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>參數

*dblValue*<br/>
輸出。 此函式傳回時包含動畫變數的目前值。

*nValue*<br/>
輸出。 此函式傳回時包含動畫變數的目前值。

### <a name="return-value"></a>傳回值

如果已順利擷取目前的值，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

呼叫此函式可擷取目前的值。 這個實作會呼叫封裝的 COM 物件，和如果呼叫失敗，此方法會傳回在建構函式或 SetDefaultValue 先前設定的預設值。

##  <a name="getvariable"></a>  CAnimationValue::GetVariable

提供封裝的動畫變數的存取。

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>傳回值

封裝的動畫變數的參考。

### <a name="remarks"></a>備註

您可以使用這個方法來存取封裝的動畫變數。 CAnimationVariable 從您取得基礎 IUIAnimationVariable 物件，其指標可以是 NULL，如果尚未建立動畫變數的存取權。

##  <a name="m_value"></a>  CAnimationValue::m_value

表示動畫值之封裝的動畫變數。

```
CAnimationVariable m_value;
```

##  <a name="operator_double"></a>  CAnimationValue::operator 雙精度浮點數

提供 CAnimationValue 和雙精度浮點數之間的轉換。

```
operator DOUBLE();
```

### <a name="return-value"></a>傳回值

目前動畫值的值。

### <a name="remarks"></a>備註

提供 CAnimationValue 和雙精度浮點數之間的轉換。 這個方法會在內部呼叫 GetValue，而且並不會檢查有錯誤。 如果 GetValue 就會失敗，傳回的值會包含先前設定在建構函式或 SetDefaultValue 的預設值。

##  <a name="operator_int32"></a>  CAnimationValue::operator INT32

提供 CAnimationValue 和 INT32 之間的轉換。

```
operator INT32();
```

### <a name="return-value"></a>傳回值

目前的動畫值，成為整數值。

### <a name="remarks"></a>備註

提供 CAnimationValue 和 INT32 之間的轉換。 這個方法會在內部呼叫 GetValue，而且並不會檢查有錯誤。 如果 GetValue 就會失敗，傳回的值會包含先前設定在建構函式或 SetDefaultValue 的預設值。

##  <a name="operator_eq"></a>  CAnimationValue::operator=

將雙精度浮點數值指派給 CAnimationValue 中。

```
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>參數

*dblVal*<br/>
指定要指派給動畫值的值。

*nVal*<br/>
指定要指派給動畫值的值。

### <a name="remarks"></a>備註

將雙精度浮點數值指派給 CAnimationValue 中。 此值設定為封裝的動畫變數的預設值。 如果您訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。

##  <a name="setdefaultvalue"></a>  CAnimationValue::SetDefaultValue

設定預設值。

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>參數

*dblDefaultValue*<br/>
指定預設值。

### <a name="remarks"></a>備註

這個方法可用於設定預設值。 尚未啟動動畫和/或基礎 COM 物件尚未建立時，預設值被傳回應用程式。 如果已經建立封裝在 CAnimationVarible 基礎 COM 物件，這個方法會重新建立它，因此您可能需要再次呼叫 EnableValueChanged/EnableIntegerValueChanged 方法。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
