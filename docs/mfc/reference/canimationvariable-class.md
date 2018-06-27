---
title: CAnimationVariable 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 207adbba4635b80ba7b60af53f920b1af376e93d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957295"
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
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|會建構一個動畫變數的物件。|  
|[CAnimationVariable:: ~ CAnimationVariable](#canimationvariable__~canimationvariable)|解構函式。 CAnimationVariable 物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationVariable::AddTransition](#addtransition)|新增轉換。|  
|[CAnimationVariable::ApplyTransitions](#applytransitions)|將轉換加入從分鏡腳本的內部清單。|  
|[CAnimationVariable::ClearTransitions](#cleartransitions)|清除轉換。|  
|[CAnimationVariable::Create](#create)|建立基礎動畫變數 COM 物件。|  
|[CAnimationVariable::CreateTransitions](#createtransitions)|建立要套用至這個動畫變數的所有轉換。|  
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|啟用或停用 IntegerValueChanged 事件。|  
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|啟用或停用 ValueChanged 事件。|  
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|傳回預設值。|  
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|傳回父系動畫物件。|  
|[CAnimationVariable::GetValue](#getvalue)|多載。 傳回目前動畫變數的值。|  
|[CAnimationVariable::GetVariable](#getvariable)|讓指標回到 IUIAnimationVariable COM 物件。|  
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|設定預設值，並釋放 IUIAnimationVariable COM 物件。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|設定動畫變數的動畫物件之間的關聯性。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否應該刪除相關的轉換物件。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|指定預設值會傳播到 IUIAnimationVariable。|  
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|包含一份繪製這個動畫變數的轉換。|  
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|封裝這個動畫變數的動畫物件指標。|  
|[CAnimationVariable::m_variable](#m_variable)|儲存 IUIAnimationVariable COM 物件的指標。 如果尚未棒的是，建立 COM 物件，或無法建立 NULL。|  
  
## <a name="remarks"></a>備註  
 CAnimationVariable 類別 IUIAnimationVariable COM 物件的封裝。 它也包含之轉換套用至分鏡腳本動畫變數的清單。 CAnimationVariable 物件內嵌在應用程式的動畫值，點、 大小、 色彩和矩形可以表示的動畫物件。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CAnimationVariable`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationvariable"></a>  CAnimationVariable:: ~ CAnimationVariable  
 解構函式。 CAnimationVariable 物件終結時呼叫。  
  
```  
virtual ~CAnimationVariable();
```  
  
##  <a name="addtransition"></a>  CAnimationVariable::AddTransition  
 新增轉換。  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>參數  
 *pTransition*  
 若要加入的轉換指標。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是將轉換新增至內部轉換套用至動畫變數的清單。 已排定動畫時，應該會清除此清單。  
  
##  <a name="applytransitions"></a>  CAnimationVariable::ApplyTransitions  
 將轉換加入從分鏡腳本的內部清單。  
  
```  
void ApplyTransitions(
    CAnimationController* pController,  
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>參數  
 *pController*  
 父動畫控制器指標。  
  
 *pStoryboard*  
 分鏡腳本指標。  
  
 *bDependOnKeyframes*  
 如果為 TRUE，此方法應將取決於主要畫面格的轉換。  
  
### <a name="remarks"></a>備註  
 此方法會將轉換從分鏡腳本的內部清單。 它會從呼叫的最上層的程式碼數次新增轉換取決於主要畫面格，並將取決於主要畫面格的轉換。 如果尚未建立基礎動畫變數的 COM 物件，這個方法會建立它在這個階段。  
  
##  <a name="canimationvariable"></a>  CAnimationVariable::CAnimationVariable  
 會建構一個動畫變數的物件。  
  
```  
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```  
  
### <a name="parameters"></a>參數  
 *dblDefaultValue*  
 指定預設值。  
  
### <a name="remarks"></a>備註  
 建構一個動畫變數的物件，並設定其預設值。 當變數沒有顯示動畫，或無法以動畫顯示，將使用預設值。  
  
##  <a name="cleartransitions"></a>  CAnimationVariable::ClearTransitions  
 清除轉換。  
  
```  
void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>參數  
 *bAutodestroy*  
 指定此方法是否應該刪除 transition 物件。  
  
### <a name="remarks"></a>備註  
 這個方法會移除之轉換的內部清單中的所有轉換。 如果 bAutodestroy 為 TRUE，或 m_bAutodestroyTransitions 為 TRUE，則轉換會刪除。 否則呼叫端應該取消配置的轉換物件。  
  
##  <a name="create"></a>  CAnimationVariable::Create  
 建立基礎動畫變數 COM 物件。  
  
```  
virtual BOOL Create(IUIAnimationManager* pManager);
```  
  
### <a name="parameters"></a>參數  
 *pManager*  
 動畫管理員指標。  
  
### <a name="return-value"></a>傳回值  
 如果已成功建立動畫變數，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法會建立基礎動畫變數的 COM 物件，並設定其預設值。  
  
##  <a name="createtransitions"></a>  CAnimationVariable::CreateTransitions  
 建立要套用至這個動畫變數的所有轉換。  
  
```  
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>參數  
*pLibrary*  
 指標[IUIAnimationTransitionLibrary 介面](https://msdn.microsoft.com/library/windows/desktop/dd371897)，其定義的標準轉換程式庫。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 建立轉換，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 需要建立的變數之轉換的內部清單已加入的轉換時，這個方法是由架構呼叫。  
  
##  <a name="enableintegervaluechangedevent"></a>  CAnimationVariable::EnableIntegerValueChangedEvent  
 啟用或停用 IntegerValueChanged 事件。  
  
```  
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 *pController*  
 父控制器指標。  
  
 *bEnable*  
 TRUE-啟用 FALSE-停用事件的事件。  
  
### <a name="remarks"></a>備註  
 啟用 ValueChanged 事件時，架構會呼叫虛擬方法 CAnimationController::OnAnimationIntegerValueChanged。 您必須衍生自 CAnimationController，為了處理這個事件類別中覆寫它。 每次變更動畫變數的整數值時，會呼叫這個方法。  
  
##  <a name="enablevaluechangedevent"></a>  CAnimationVariable::EnableValueChangedEvent  
 啟用或停用 ValueChanged 事件。  
  
```  
void EnableValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 *pController*  
 父控制器指標。  
  
 *bEnable*  
 TRUE-啟用 FALSE-停用事件的事件。  
  
### <a name="remarks"></a>備註  
 啟用 ValueChanged 事件時，架構會呼叫虛擬方法 CAnimationController::OnAnimationValueChanged。 您必須衍生自 CAnimationController，為了處理這個事件類別中覆寫它。 每次變更動畫變數的值時，會呼叫這個方法。  
  
##  <a name="getdefaultvalue"></a>  CAnimationVariable::GetDefaultValue  
 傳回預設值。  
  
```  
DOUBLE GetDefaultValue() const;  
```  
  
### <a name="return-value"></a>傳回值  
 預設值。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來取得動畫變數的預設值。 在建構函式或 SetDefaultValue 方法，可以設定預設值。  
  
##  <a name="getparentanimationobject"></a>  CAnimationVariable::GetParentAnimationObject  
 傳回父系動畫物件。  
  
```  
CAnimationBaseObject* GetParentAnimationObject();
```  
  
### <a name="return-value"></a>傳回值  
 指向父動畫物件，如果已建立關聯性，否則為 NULL。  
  
### <a name="remarks"></a>備註  
 這個方法可以呼叫以擷取父動畫物件 （容器） 的指標。  
  
##  <a name="getvalue"></a>  CAnimationVariable::GetValue  
 傳回目前動畫變數的值。  
  
```  
HRESULT GetValue(DOUBLE& dblValue);  
HRESULT GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>參數  
 *dblValue*  
 目前動畫變數的值。  
  
 *n 值*  
 目前動畫變數的值。  
  
### <a name="return-value"></a>傳回值  
 如果成功，取得值，或尚未建立基礎動畫變數為 S_OK。 否則 HRESULT 錯誤碼。  
  
### <a name="remarks"></a>備註  
 這個方法可以呼叫以擷取目前動畫變數的值。 如果尚未建立基礎 COM 物件，dblValue 會在函式會傳回時包含預設值。  
  
##  <a name="getvariable"></a>  CAnimationVariable::GetVariable  
 讓指標回到 IUIAnimationVariable COM 物件。  
  
```  
IUIAnimationVariable* GetVariable();
```  
  
### <a name="return-value"></a>傳回值  
 IUIAnimationVariable COM 物件，或 NULL 動畫變數並未建立，則無法建立有效的指標。  
  
### <a name="remarks"></a>備註  
 使用這個函數來存取基礎 IUIAnimationVariable COM 物件，並視需要直接呼叫其方法。  
  
##  <a name="m_bautodestroytransitions"></a>  CAnimationVariable::m_bAutodestroyTransitions  
 指定是否應該刪除相關的轉換物件。  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
### <a name="remarks"></a>備註  
 正在移除從內部轉換的清單時，請將此值設 true 會強制刪除轉換物件。 如果此值為 FALSE，會轉換必須先刪除藉由呼叫應用程式。 已排定動畫後，便一律會清除之轉換的清單。 預設值為 FALSE。  
  
##  <a name="m_dbldefaultvalue"></a>  CAnimationVariable::m_dblDefaultValue  
 指定預設值會傳播到 IUIAnimationVariable。  
  
```  
DOUBLE m_dblDefaultValue;  
```  
  
##  <a name="m_lsttransitions"></a>  CAnimationVariable::m_lstTransitions  
 包含一份繪製這個動畫變數的轉換。  
  
```  
CObList m_lstTransitions;  
```  
  
##  <a name="m_pparentobject"></a>  CAnimationVariable::m_pParentObject  
 封裝這個動畫變數的動畫物件指標。  
  
```  
CAnimationBaseObject* m_pParentObject;  
```  
  
##  <a name="m_variable"></a>  CAnimationVariable::m_variable  
 儲存 IUIAnimationVariable COM 物件的指標。 如果尚未棒的是，建立 COM 物件，或無法建立 NULL。  
  
```  
ATL::CComPtr<IUIAnimationVariable> m_variable;  
```  
  
##  <a name="setdefaultvalue"></a>  CAnimationVariable::SetDefaultValue  
 設定預設值，並釋放 IUIAnimationVariable COM 物件。  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>參數  
 *dblDefaultValue*  
 指定新的預設值。  
  
### <a name="remarks"></a>備註  
 使用這個方法來重設預設值。 這個方法會釋放內部 IUIAnimationVariable COM 物件，因此當動畫變數會重新建立時，基礎 COM 物件取得新的預設值。 如果未建立 COM 物件，表示動畫變數，或如果變數沒有顯示動畫，則 GetValue 會傳回預設值。  
  
##  <a name="setparentanimationobject"></a>  CAnimationVariable::SetParentAnimationObject  
 設定動畫變數的動畫物件之間的關聯性。  
  
```  
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```  
  
### <a name="parameters"></a>參數  
 *pParentObject*  
 包含此變數的動畫物件指標。  
  
### <a name="remarks"></a>備註  
 若要建立動畫變數封裝它的動畫物件之間的一對一關聯性是在內部呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
