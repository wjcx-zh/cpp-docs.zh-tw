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
ms.openlocfilehash: 51cc4732ee8ad5f954e5bd758484cec74cf00fe6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377056"
---
# <a name="canimationvariable-class"></a>CAnimationVariable 類別

表示動畫變數。

## <a name="syntax"></a>語法

```
class CAnimationVariable;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[動畫變數::動畫變數](#canimationvariable)|構造動畫變數物件。|
|[動畫變數::~C動畫變數](#_dtorcanimationvariable)|解構函式。 在銷毀 CAnimation 變數物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫變數::新增轉換](#addtransition)|添加轉換。|
|[動畫變數::應用轉換](#applytransitions)|將從內部清單轉換為情節提要。|
|[動畫變數::清除轉換](#cleartransitions)|清除轉換。|
|[動畫變數::建立](#create)|創建基礎動畫變數 COM 物件。|
|[動畫變數::建立轉換](#createtransitions)|創建要應用於此動畫變數的所有轉換。|
|[動畫變數::啟用整數值變更事件](#enableintegervaluechangedevent)|啟用或禁用整數值更改事件。|
|[動畫變數::啟用價值變更事件](#enablevaluechangedevent)|啟用或停用"值更改"事件。|
|[動畫變數:取得預設值](#getdefaultvalue)|返回預設值。|
|[動畫變數::取得父動畫物件](#getparentanimationobject)|返回父動畫物件。|
|[動畫變數:取得價值](#getvalue)|已多載。 返回動畫變數的當前值。|
|[動畫變數:抓取變數](#getvariable)|返回指向 IUI動畫可變 COM 物件的指標。|
|[動畫變數::設定預設值](#setdefaultvalue)|設置預設值並釋放 IUI動畫可變 COM 物件。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[動畫變數::設定父動畫物件](#setparentanimationobject)|設置動畫變數和動畫對象之間的關係。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[動畫變數::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否應刪除相關的過渡物件。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[動畫變數::m_dblDefaultValue](#m_dbldefaultvalue)|指定將傳播為 IUI動畫變數的預設值。|
|[動畫變數::m_lstTransitions](#m_lsttransitions)|包含為此動畫變數設置動畫的過渡清單。|
|[C動畫變數::m_pParentObject](#m_pparentobject)|指向封裝此動畫變數的動畫物件的指標。|
|[動畫變數::m_variable](#m_variable)|存儲指向 IUI動畫可變 COM 物件的指標。 如果尚未建立 COM 物件,或者建立失敗,則為 NULL。|

## <a name="remarks"></a>備註

C動畫變數類封裝IUI動畫變數COM物件。 它還包含要應用於情節提要中的動畫變數的過渡清單。 CAnimationVariable 物件嵌入到動畫物件中,可以在應用程式中表示動畫值、點、大小、顏色和矩形。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CAnimationVariable`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a>動畫變數::~C動畫變數

解構函式。 在銷毀 CAnimation 變數物件時調用。

```
virtual ~CAnimationVariable();
```

## <a name="canimationvariableaddtransition"></a><a name="addtransition"></a>動畫變數::新增轉換

添加轉換。

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>參數

*p 轉換*<br/>
指向要添加的過渡的指標。

### <a name="remarks"></a>備註

呼叫此方法是為了向要應用於動畫變數的過渡的內部清單添加過渡。 計劃動畫時,應清除此清單。

## <a name="canimationvariableapplytransitions"></a><a name="applytransitions"></a>動畫變數::應用轉換

將從內部清單轉換為情節提要。

```
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>參數

*pController*<br/>
指向父動畫控制器的指標。

*板*<br/>
指向情節提要的指標。

*bDependon 關鍵幀*<br/>
TRUE,如果此方法應添加依賴於關鍵幀的過渡。

### <a name="remarks"></a>備註

此方法將從內部清單轉換為情節提要。 它多次從頂級代碼調用以添加不依賴於關鍵幀的過渡,並添加依賴於關鍵幀的過渡。 如果尚未創建基礎動畫變數 COM 物件,則此方法將在此階段創建它。

## <a name="canimationvariablecanimationvariable"></a><a name="canimationvariable"></a>動畫變數::動畫變數

構造動畫變數物件。

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>參數

*dblDefault值*<br/>
指定預設值。

### <a name="remarks"></a>備註

建構動畫變數物件並設置其預設值。 當變數未進行動畫處理或無法進行動畫處理時,將使用預設值。

## <a name="canimationvariablecleartransitions"></a><a name="cleartransitions"></a>動畫變數::清除轉換

清除轉換。

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>參數

*b 自動銷毀*<br/>
指定此方法是否應刪除過渡物件。

### <a name="remarks"></a>備註

此方法從內部轉換清單中刪除所有轉換。 如果 bAuto銷毀為 TRUE,或者m_bAutodestroyTransitions為 TRUE,則刪除轉換。 否則,調用方應取消分配轉換物件。

## <a name="canimationvariablecreate"></a><a name="create"></a>動畫變數::建立

創建基礎動畫變數 COM 物件。

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>參數

*p經理*<br/>
指向動畫管理器的指標。

### <a name="return-value"></a>傳回值

如果動畫變數已成功創建,則為 TRUE;如果動畫變數已成功創建,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

此方法創建基礎動畫變數 COM 物件並設置其預設值。

## <a name="canimationvariablecreatetransitions"></a><a name="createtransitions"></a>動畫變數::建立轉換

創建要應用於此動畫變數的所有轉換。

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>參數

*p庫*<br/>
指向[IUIAnimation 轉換庫介面](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)的指標,該介面定義標準轉換庫。

### <a name="return-value"></a>傳回值

如果成功創建轉換,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

當框架需要創建已添加到變數的內部轉換清單中的轉換時,框架會調用此方法。

## <a name="canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>動畫變數::啟用整數值變更事件

啟用或禁用整數值更改事件。

```
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>參數

*pController*<br/>
指向父控制器的指標。

*b 啟用*<br/>
TRUE - 啟用事件,FALSE - 禁用事件。

### <a name="remarks"></a>備註

啟用 Value"更改"事件後,框架將調用虛擬方法 C動畫控制器::在動畫中值已更改。 您需要在從 CAnimationController 派生的類中重寫它,以便處理此事件。 每次更改動畫變數的整數值時,都會調用此方法。

## <a name="canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>動畫變數::啟用價值變更事件

啟用或停用"值更改"事件。

```
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>參數

*pController*<br/>
指向父控制器的指標。

*b 啟用*<br/>
TRUE - 啟用事件,FALSE - 禁用事件。

### <a name="remarks"></a>備註

啟用 Value"更改"事件後,框架將調用虛擬方法 C動畫控制器::打開動畫值。 您需要在從 CAnimationController 派生的類中重寫它,以便處理此事件。 每次更改動畫變數的值時,都會調用此方法。

## <a name="canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a>動畫變數:取得預設值

返回預設值。

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>傳回值

預設值。

### <a name="remarks"></a>備註

使用此函數獲取動畫變數的預設值。 默認值可以在建構函數中設置,也可以通過 SetDefaultValue 方法設置。

## <a name="canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a>動畫變數::取得父動畫物件

返回父動畫物件。

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>傳回值

指向父動畫物件的指標(如果已建立關係,則為 NULL)。

### <a name="remarks"></a>備註

可以調用此方法來檢索指向父動畫物件(容器)的指標。

## <a name="canimationvariablegetvalue"></a><a name="getvalue"></a>動畫變數:取得價值

返回動畫變數的當前值。

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>參數

*dblValue*<br/>
動畫變數的當前值。

*n值*<br/>
動畫變數的當前值。

### <a name="return-value"></a>傳回值

S_OK如果該值成功獲得,或者尚未創建基礎動畫變數。 否則,HRESULT 錯誤代碼。

### <a name="remarks"></a>備註

可以調用此方法來檢索動畫變數的當前值。 如果未創建基礎 COM 物件,則當函數返回時,dblValue 將包含預設值。

## <a name="canimationvariablegetvariable"></a><a name="getvariable"></a>動畫變數:抓取變數

返回指向 IUI動畫可變 COM 物件的指標。

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>傳回值

指向 IUIAnimationvariable COM 物件的有效指標,或 NULL(如果未建立動畫變數或無法創建)。

### <a name="remarks"></a>備註

使用此函數可以造訪基礎IUI動畫可變COM物件,並在需要時直接調用其方法。

## <a name="canimationvariablem_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>動畫變數::m_bAutodestroyTransitions

指定是否應刪除相關的過渡物件。

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>備註

將此值設定為 TRUE,以強制刪除過渡物件,當它們從內部轉換清單中刪除時。 如果此值為 FALSE,則應透過呼叫應用程式刪除轉換。 計畫動畫后,始終清除轉換清單。 預設值為 FALSE。

## <a name="canimationvariablem_dbldefaultvalue"></a><a name="m_dbldefaultvalue"></a>動畫變數::m_dblDefaultValue

指定將傳播為 IUI動畫變數的預設值。

```
DOUBLE m_dblDefaultValue;
```

## <a name="canimationvariablem_lsttransitions"></a><a name="m_lsttransitions"></a>動畫變數::m_lstTransitions

包含為此動畫變數設置動畫的過渡清單。

```
CObList m_lstTransitions;
```

## <a name="canimationvariablem_pparentobject"></a><a name="m_pparentobject"></a>C動畫變數::m_pParentObject

指向封裝此動畫變數的動畫物件的指標。

```
CAnimationBaseObject* m_pParentObject;
```

## <a name="canimationvariablem_variable"></a><a name="m_variable"></a>動畫變數::m_variable

存儲指向 IUI動畫可變 COM 物件的指標。 如果尚未建立 COM 物件,或者建立失敗,則為 NULL。

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

## <a name="canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a>動畫變數::設定預設值

設置預設值並釋放 IUI動畫可變 COM 物件。

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>參數

*dblDefault值*<br/>
指定新的預設值。

### <a name="remarks"></a>備註

使用此方法重置預設值。 此方法釋放內部 IUI動畫可變 COM 物件,因此在重新創建動畫變數時,基礎 COM 物件獲取新的預設值。 如果未創建表示動畫變數的 COM 物件,或者該變數尚未進行動畫處理,則 GetValue 會返回預設值。

## <a name="canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a>動畫變數::設定父動畫物件

設置動畫變數和動畫對象之間的關係。

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>參數

*p 父物件*<br/>
指向包含此變數的動畫物件的指標。

### <a name="remarks"></a>備註

此方法在內部調用,以建立動畫變數和封裝它的動畫對象之間的一對一關係。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
