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
ms.openlocfilehash: e020e3e123bb5dc96a623e7a41896d75c611b81e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755083"
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
|[動畫值::動畫值](#canimationvalue)|已多載。 構造 CAnimationValue 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫值::新增轉換](#addtransition)|添加要應用於值的過渡。|
|[動畫值:取得價值](#getvalue)|已多載。 檢索當前值。|
|[動畫值::取得變數](#getvariable)|提供對封裝動畫變數的訪問。|
|[動畫值::設定預設值](#setdefaultvalue)|設置預設值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[動畫值::取得動畫變數清單](#getanimationvariablelist)|將封裝的動畫變數放入清單中。 ( 覆[寫動畫基礎物件:抓取動畫變數列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[動畫值::運算符 DOUBLE](#operator_double)|提供「動畫值」和「雙」之間的轉換。|
|[動畫值::操作員 INT32](#operator_int32)|提供 C動畫值和 INT32 之間的轉換。|
|[動畫值::操作員*](#operator_eq)|已多載。 將 INT32 值分配給 CAnimationValue。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[動畫值::m_value](#m_value)|表示動畫值的封裝動畫變數。|

## <a name="remarks"></a>備註

CAnimationValue 類封裝單個 CAnimationvariable 物件,可以在應用程式中表示單個動畫值。 例如,當需要根據單個動畫值創建動畫時,可以使用此類進行動畫透明度(淡入淡出效果)、角度(旋轉物件)或任何其他情況。 要在應用程式中使用此類,只需實例化此類的物件,請使用 CAnimationController::addAnimationObject 將其添加到動畫控制器,並調用要應用於該值的每個轉換的 AddTransition。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[動畫基礎物件](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationvalueaddtransition"></a><a name="addtransition"></a>動畫值::新增轉換

添加要應用於值的過渡。

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>參數

*p 轉換*<br/>
指向過渡物件的指標。

### <a name="remarks"></a>備註

呼叫此函數以向要應用於動畫變數的過渡的內部清單添加轉換。 添加轉換時,不會立即應用這些轉換並存儲在內部清單中。 當您調用 CAnimationController::AnimateGroup 時,將應用轉換(添加到特定值的情節提要中)。

## <a name="canimationvaluecanimationvalue"></a><a name="canimationvalue"></a>動畫值::動畫值

構造 CAnimationValue 物件。

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*dblDefault值*<br/>
指定預設值。

*n集團ID*<br/>
指定組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
指定使用者定義的數據。

### <a name="remarks"></a>備註

建構具有預設屬性的 CAnimationValue 物件:預設值、組 ID 和物件 ID 設置為 0。

## <a name="canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>動畫值::取得動畫變數清單

將封裝的動畫變數放入清單中。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>參數

*Lst*<br/>
當函數返回時,它包含一個指向表示動畫值的 CAnimation 變數的指標。

## <a name="canimationvaluegetvalue"></a><a name="getvalue"></a>動畫值:取得價值

檢索當前值。

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>參數

*dblValue*<br/>
輸出。 當函數返回時,它包含動畫變數的當前值。

*n值*<br/>
輸出。 當函數返回時,它包含動畫變數的當前值。

### <a name="return-value"></a>傳回值

如果成功檢索當前值,則為 TRUE;如果成功檢索當前值,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

調用此函數以檢索當前值。 此實現調用封裝的 COM 物件,如果調用失敗,此方法將返回以前在構造函數或 SetDefaultValue 中設置的預設值。

## <a name="canimationvaluegetvariable"></a><a name="getvariable"></a>動畫值::取得變數

提供對封裝動畫變數的訪問。

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>傳回值

對封裝動畫變數的引用。

### <a name="remarks"></a>備註

使用此方法訪問封裝的動畫變數。 從 CAnimationVariable 可以存取基礎 IUI動畫變數物件,如果尚未創建動畫變數,該物件的指標可以是 NULL。

## <a name="canimationvaluem_value"></a><a name="m_value"></a>動畫值::m_value

表示動畫值的封裝動畫變數。

```
CAnimationVariable m_value;
```

## <a name="canimationvalueoperator-double"></a><a name="operator_double"></a>動畫值::運算符 DOUBLE

提供「動畫值」和「雙」之間的轉換。

```
operator DOUBLE();
```

### <a name="return-value"></a>傳回值

動畫值的當前值。

### <a name="remarks"></a>備註

提供「動畫值」和「雙」之間的轉換。 此方法在內部調用 GetValue,不檢查錯誤。 如果 GetValue 失敗,則返回的值將包含以前在建構函數中設置的預設值或 SetDefaultValue 中設置的值。

## <a name="canimationvalueoperator-int32"></a><a name="operator_int32"></a>動畫值::操作員 INT32

提供 C動畫值和 INT32 之間的轉換。

```
operator INT32();
```

### <a name="return-value"></a>傳回值

動畫值的當前值(以整數形式)。

### <a name="remarks"></a>備註

提供 C動畫值和 INT32 之間的轉換。 此方法在內部調用 GetValue,不檢查錯誤。 如果 GetValue 失敗,則返回的值將包含以前在建構函數中設置的預設值或 SetDefaultValue 中設置的值。

## <a name="canimationvalueoperator"></a><a name="operator_eq"></a>動畫值::操作員*

將 DOUBLE 值分配給 CAnimationValue。

```cpp
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>參數

*德布爾瓦爾*<br/>
指定要分配給動畫值的值。

*恩瓦爾*<br/>
指定要分配給動畫值的值。

### <a name="remarks"></a>備註

將 DOUBLE 值分配給 CAnimationValue。 此值設置為封裝動畫變數的預設值。 如果將此動畫物件訂閱到事件(Value已更改或整數值更改),則需要重新啟用這些事件。

## <a name="canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a>動畫值::設定預設值

設置預設值。

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>參數

*dblDefault值*<br/>
指定預設值。

### <a name="remarks"></a>備註

使用此方法設置預設值。 尚未啟動動畫和/或尚未創建基礎 COM 物件時,預設值將返回到應用程式。 如果已在 CAnimation Varible 中封裝的基礎 COM 物件已創建,此方法將重新創建它,因此您可能需要再次呼叫啟用 Value 更改/啟用 IntegerValue 更改方法。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
