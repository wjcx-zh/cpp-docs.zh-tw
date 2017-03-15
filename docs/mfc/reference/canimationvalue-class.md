---
title: "CAnimationValue 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CAnimationValue
- CAnimationValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationValue class
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 083c8be9a0d9d518d5353b6d02c0050944312805
ms.lasthandoff: 02/24/2017

---
# <a name="canimationvalue-class"></a>CAnimationValue 類別
實作有一個值的動畫物件功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CAnimationValue : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationValue::CAnimationValue](#canimationvalue)|多載。 建構 CAnimationValue 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimationValue::AddTransition](#addtransition)|將轉換套用至值。|  
|[CAnimationValue::GetValue](#getvalue)|多載。 擷取目前的值。|  
|[CAnimationValue::GetVariable](#getvariable)|提供封裝的動畫變數的存取。|  
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|設定預設值。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|將封裝的動畫變數放入清單。 (覆寫[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimationValue::operator 雙](#operator_double)|提供 CAnimationValue 與點之間的轉換。|  
|[CAnimationValue::operator INT32](#operator_int32)|提供 CAnimationValue 與 INT32 之間的轉換。|  
|[CAnimationValue::operator =](#operator_eq)|多載。 將 INT32 值指派給 CAnimationValue。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CAnimationValue::m_value](#m_value)|表示動畫值之封裝的動畫變數。|  
  
## <a name="remarks"></a>備註  
 CAnimationValue 類別會封裝單一 CAnimationVariable 物件，並可代表應用程式中單一動畫的值。 比方說，您可以使用這個類別的動畫的透明度 （淡出效果） 的角度 （若要旋轉的物件），或任何其他的情況下如果您需要建立動畫單一動畫值而定。 若要在應用程式中使用這個類別，只要具現化這個類別的物件、 將它新增至使用 CAnimationController::AddAnimationObject 動畫控制器，並呼叫還得針對每個轉換套用至值。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationValue`
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="a-nameaddtransitiona--canimationvalueaddtransition"></a><a name="addtransition"></a>CAnimationValue::AddTransition  
 將轉換套用至值。  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>參數  
 `pTransition`  
 轉換物件的指標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可將轉換加入至轉換套用至動畫變數的內部清單。 當您新增的轉換時，它們就會不會立即套用，並儲存在內部清單。 轉換會套用 （加入至腳本，以尋找特定的值） 當您呼叫 CAnimationController::AnimateGroup。  
  
##  <a name="a-namecanimationvaluea--canimationvaluecanimationvalue"></a><a name="canimationvalue"></a>CAnimationValue::CAnimationValue  
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
 `dblDefaultValue`  
 指定預設值。  
  
 `nGroupID`  
 指定群組識別碼。  
  
 `nObjectID`  
 指定物件識別碼。  
  
 `dwUserData`  
 指定使用者定義的資料。  
  
### <a name="remarks"></a>備註  
 建構 CAnimationValue 物件使用預設屬性︰ 預設值，群組識別碼和物件識別碼會設為 0。  
  
##  <a name="a-namegetanimationvariablelista--canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationValue::GetAnimationVariableList  
 將封裝的動畫變數放入清單。  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>參數  
 `lst`  
 函式傳回時，它包含 CAnimationVariable 代表動畫的值的指標。  
  
##  <a name="a-namegetvaluea--canimationvaluegetvalue"></a><a name="getvalue"></a>CAnimationValue::GetValue  
 擷取目前的值。  
  
```  
BOOL GetValue(DOUBLE& dblValue);  
BOOL GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>參數  
 `dblValue`  
 輸出。 函式傳回時包含動畫變數的目前值。  
  
 `nValue`  
 輸出。 函式傳回時包含動畫變數的目前值。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 擷取目前的值，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取目前的值。 這個實作會呼叫封裝的 COM 物件，如果呼叫失敗，這個方法會傳回在建構函式或使用 SetDefaultValue 先前所設定的預設值。  
  
##  <a name="a-namegetvariablea--canimationvaluegetvariable"></a><a name="getvariable"></a>CAnimationValue::GetVariable  
 提供封裝的動畫變數的存取。  
  
```  
CAnimationVariable& GetVariable();
```  
  
### <a name="return-value"></a>傳回值  
 封裝的動畫變數的參考。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法來存取封裝的動畫變數。 從 CAnimationVariable 即可存取基礎 IUIAnimationVariable 物件，如果尚未建立動畫變數的指標可以是 NULL。  
  
##  <a name="a-namemvaluea--canimationvaluemvalue"></a><a name="m_value"></a>CAnimationValue::m_value  
 表示動畫值之封裝的動畫變數。  
  
```  
CAnimationVariable m_value;  
```  
  
##  <a name="a-nameoperatordoublea--canimationvalueoperator-double"></a><a name="operator_double"></a>CAnimationValue::operator 雙  
 提供 CAnimationValue 與點之間的轉換。  
  
```  
operator DOUBLE();
```   
  
### <a name="return-value"></a>傳回值  
 動畫值之目前值。  
  
### <a name="remarks"></a>備註  
 提供 CAnimationValue 與點之間的轉換。 此方法在內部呼叫 GetValue，而且並不會檢查有錯誤。 如果 GetValue 失敗，傳回的值會包含先前在建構函式或設定與 SetDefaultValue 的預設值。  
  
##  <a name="a-nameoperatorint32a--canimationvalueoperator-int32"></a><a name="operator_int32"></a>CAnimationValue::operator INT32  
 提供 CAnimationValue 與 INT32 之間的轉換。  
  
```  
operator INT32();
```   
  
### <a name="return-value"></a>傳回值  
 目前的動畫值為整數值。  
  
### <a name="remarks"></a>備註  
 提供 CAnimationValue 與 INT32 之間的轉換。 此方法在內部呼叫 GetValue，而且並不會檢查有錯誤。 如果 GetValue 失敗，傳回的值會包含先前在建構函式或設定與 SetDefaultValue 的預設值。  
  
##  <a name="a-nameoperatoreqa--canimationvalueoperator"></a><a name="operator_eq"></a>CAnimationValue::operator =  
 將雙精度浮點數值指派給 CAnimationValue。  
  
```  
void operator=(DOUBLE dblVal);  
void operator=(INT32 nVal);
```  
  
### <a name="parameters"></a>參數  
 `dblVal`  
 指定要指派給動畫值的值。  
  
 `nVal`  
 指定要指派給動畫值的值。  
  
### <a name="remarks"></a>備註  
 將雙精度浮點數值指派給 CAnimationValue。 此值設定為封裝的動畫變數的預設值。 如果您已訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件，您需要重新啟用這些事件。  
  
##  <a name="a-namesetdefaultvaluea--canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationValue::SetDefaultValue  
 設定預設值。  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>參數  
 `dblDefaultValue`  
 指定預設值。  
  
### <a name="remarks"></a>備註  
 使用這個方法可以設定預設值。 尚未啟動動畫及/或基礎 COM 物件尚未建立時，預設值被傳回給應用程式。 如果已建立封裝在 CAnimationVarible 基礎 COM 物件，這個方法會重新建立它，因此您可能需要再次呼叫 EnableValueChanged/EnableIntegerValueChanged 方法。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

