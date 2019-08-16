---
title: CAnimationVariable 類別
ms.date: 03/27/2019
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
ms.openlocfilehash: b6767ed42d66aff467ef36bd2a7b5234ad181ced
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507534"
---
# <a name="canimationvariable-class"></a>CAnimationVariable 類別

表示動畫變數。

## <a name="syntax"></a>語法

```
class CAnimationVariable;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|構造動畫變數物件。|
|[CAnimationVariable:: ~ CAnimationVariable](#_dtorcanimationvariable)|解構函式。 在終結 CAnimationVariable 物件時呼叫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|加入轉換。|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|將內部清單的轉換新增至分鏡腳本。|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|清除轉換。|
|[CAnimationVariable::Create](#create)|建立基礎動畫變數 COM 物件。|
|[CAnimationVariable::CreateTransitions](#createtransitions)|建立要套用至此動畫變數的所有轉換。|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|啟用或停用 IntegerValueChanged 事件。|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|啟用或停用 ValueChanged 事件。|
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|傳回預設值。|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|傳回父系動畫物件。|
|[CAnimationVariable::GetValue](#getvalue)|多載。 傳回動畫變數目前的值。|
|[CAnimationVariable::GetVariable](#getvariable)|傳回 IUIAnimationVariable COM 物件的指標。|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|設定預設值和釋放 IUIAnimationVariable COM 物件。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|設定動畫變數與動畫物件之間的關聯性。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否應該刪除相關的轉換物件。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|指定預設值, 這會傳播至 IUIAnimationVariable。|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|包含以動畫顯示此動畫變數的轉換清單。|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|封裝這個動畫變數的動畫物件指標。|
|[CAnimationVariable::m_variable](#m_variable)|儲存 IUIAnimationVariable COM 物件的指標。 如果尚未建立 COM 物件, 或如果建立失敗, 則為 Null。|

## <a name="remarks"></a>備註

CAnimationVariable 類別會封裝 IUIAnimationVariable COM 物件。 它也會保留要套用至分鏡腳本中之動畫變數的轉換清單。 CAnimationVariable 物件內嵌于動畫物件中, 可以在應用程式中代表動畫值、點、大小、色彩和矩形。

## <a name="inheritance-hierarchy"></a>繼承階層

`CAnimationVariable`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="_dtorcanimationvariable"></a>CAnimationVariable:: ~ CAnimationVariable

解構函式。 在終結 CAnimationVariable 物件時呼叫。

```
virtual ~CAnimationVariable();
```

##  <a name="addtransition"></a>CAnimationVariable:: AddTransition

加入轉換。

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>參數

*pTransition*<br/>
要加入之轉換的指標。

### <a name="remarks"></a>備註

呼叫這個方法時, 會將轉換加入至要套用至動畫變數的轉換內部清單。 已排程動畫時, 應清除此清單。

##  <a name="applytransitions"></a>CAnimationVariable:: ApplyTransitions

將內部清單的轉換新增至分鏡腳本。

```
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>參數

*pController*<br/>
父動畫控制器的指標。

*pStoryboard*<br/>
分鏡腳本的指標。

*bDependOnKeyframes*<br/>
若此方法應新增相依于主要畫面格的轉換, 則為 TRUE。

### <a name="remarks"></a>備註

這個方法會將內部清單的轉換新增至分鏡腳本。 它會從最上層程式碼呼叫數次, 以新增不依賴主要畫面格的轉換, 以及新增相依于關鍵畫面的轉換。 如果尚未建立基礎動畫變數 COM 物件, 這個方法會在這個階段建立它。

##  <a name="canimationvariable"></a>CAnimationVariable:: CAnimationVariable

構造動畫變數物件。

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>參數

*dblDefaultValue*<br/>
指定預設值。

### <a name="remarks"></a>備註

構造動畫變數物件, 並設定其預設值。 當變數未繪製動畫或無法繪製動畫時, 會使用預設值。

##  <a name="cleartransitions"></a>CAnimationVariable:: ClearTransitions

清除轉換。

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>參數

*bAutodestroy*<br/>
指定這個方法是否應刪除轉換物件。

### <a name="remarks"></a>備註

這個方法會將所有轉換從內部的轉換清單移除。 如果 bAutodestroy 為 TRUE, 或 m_bAutodestroyTransitions 為 TRUE, 則會刪除轉換。 否則呼叫端應該將轉換物件解除配置。

##  <a name="create"></a>CAnimationVariable:: Create

建立基礎動畫變數 COM 物件。

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>參數

*pManager*<br/>
動畫管理員的指標。

### <a name="return-value"></a>傳回值

如果已成功建立動畫變數, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會建立基礎動畫變數 COM 物件, 並設定其預設值。

##  <a name="createtransitions"></a>CAnimationVariable:: CreateTransitions

建立要套用至此動畫變數的所有轉換。

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>參數

*pLibrary*<br/>
[IUIAnimationTransitionLibrary 介面](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指標, 它會定義標準轉換的程式庫。

### <a name="return-value"></a>傳回值

如果成功建立轉換, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當此方法需要建立已加入至變數內部轉換清單的轉換時, 會由架構呼叫。

##  <a name="enableintegervaluechangedevent"></a>CAnimationVariable:: EnableIntegerValueChangedEvent

啟用或停用 IntegerValueChanged 事件。

```
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>參數

*pController*<br/>
父控制器的指標。

*bEnable*<br/>
TRUE-啟用事件, FALSE-停用事件。

### <a name="remarks"></a>備註

當 ValueChanged 事件啟用時, 架構會呼叫虛擬方法 CAnimationController:: OnAnimationIntegerValueChanged。 您必須在衍生自 CAnimationController 的類別中覆寫它, 才能處理這個事件。 每當動畫變數的整數值變更時, 就會呼叫這個方法。

##  <a name="enablevaluechangedevent"></a>CAnimationVariable:: EnableValueChangedEvent

啟用或停用 ValueChanged 事件。

```
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>參數

*pController*<br/>
父控制器的指標。

*bEnable*<br/>
TRUE-啟用事件, FALSE-停用事件。

### <a name="remarks"></a>備註

當 ValueChanged 事件啟用時, 架構會呼叫虛擬方法 CAnimationController:: OnAnimationValueChanged。 您必須在衍生自 CAnimationController 的類別中覆寫它, 才能處理這個事件。 每當動畫變數的值變更時, 就會呼叫這個方法。

##  <a name="getdefaultvalue"></a>CAnimationVariable:: GetDefaultValue

傳回預設值。

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>傳回值

預設值。

### <a name="remarks"></a>備註

使用此函式可取得動畫變數的預設值。 預設值可以在 [函數] 或 [SetDefaultValue] 方法中設定。

##  <a name="getparentanimationobject"></a>CAnimationVariable:: GetParentAnimationObject

傳回父系動畫物件。

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>傳回值

如果已建立關聯性, 則為父動畫物件的指標, 否則為 Null。

### <a name="remarks"></a>備註

您可以呼叫這個方法, 以取得父動畫物件 (容器) 的指標。

##  <a name="getvalue"></a>CAnimationVariable:: GetValue

傳回動畫變數目前的值。

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>參數

*dblValue*<br/>
動畫變數的目前值。

*nValue*<br/>
動畫變數的目前值。

### <a name="return-value"></a>傳回值

如果已成功取得值, 或尚未建立基礎動畫變數, 則為 S_OK。 否則為 HRESULT 錯誤碼。

### <a name="remarks"></a>備註

您可以呼叫這個方法, 以取得動畫變數目前的值。 如果尚未建立基礎 COM 物件, 當函式傳回時, dblValue 會包含預設值。

##  <a name="getvariable"></a>CAnimationVariable:: GetVariable

傳回 IUIAnimationVariable COM 物件的指標。

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>傳回值

IUIAnimationVariable COM 物件的有效指標, 如果未建立動畫變數或無法建立, 則為 Null。

### <a name="remarks"></a>備註

使用此函式可存取基礎 IUIAnimationVariable COM 物件, 並在需要時直接呼叫其方法。

##  <a name="m_bautodestroytransitions"></a>CAnimationVariable:: m_bAutodestroyTransitions

指定是否應該刪除相關的轉換物件。

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>備註

將此值設定為 TRUE, 可在從轉換的內部清單中移除時, 強制刪除轉換物件。 如果此值為 FALSE, 則應該藉由呼叫應用程式來刪除轉換。 排定動畫之後, 一律會清除轉換清單。 預設值為 FALSE。

##  <a name="m_dbldefaultvalue"></a>CAnimationVariable:: m_dblDefaultValue

指定預設值, 這會傳播至 IUIAnimationVariable。

```
DOUBLE m_dblDefaultValue;
```

##  <a name="m_lsttransitions"></a>CAnimationVariable:: m_lstTransitions

包含以動畫顯示此動畫變數的轉換清單。

```
CObList m_lstTransitions;
```

##  <a name="m_pparentobject"></a>CAnimationVariable:: m_pParentObject

封裝這個動畫變數的動畫物件指標。

```
CAnimationBaseObject* m_pParentObject;
```

##  <a name="m_variable"></a>CAnimationVariable:: m_variable

儲存 IUIAnimationVariable COM 物件的指標。 如果尚未建立 COM 物件, 或如果建立失敗, 則為 Null。

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

##  <a name="setdefaultvalue"></a>CAnimationVariable:: SetDefaultValue

設定預設值和釋放 IUIAnimationVariable COM 物件。

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>參數

*dblDefaultValue*<br/>
指定新的預設值。

### <a name="remarks"></a>備註

使用此方法來重設預設值。 這個方法會釋放內部 IUIAnimationVariable COM 物件, 因此當重新建立動畫變數時, 基礎 COM 物件會取得新的預設值。 如果未建立代表動畫變數的 COM 物件, 或變數尚未進行動畫處理, 則會傳回預設值。

##  <a name="setparentanimationobject"></a>CAnimationVariable:: SetParentAnimationObject

設定動畫變數與動畫物件之間的關聯性。

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>參數

*pParentObject*<br/>
包含這個變數之動畫物件的指標。

### <a name="remarks"></a>備註

這個方法會在內部呼叫, 以便在動畫變數和封裝它的動畫物件之間建立一對一關聯性。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
