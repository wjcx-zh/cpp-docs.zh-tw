---
title: CAnimationBaseObject 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db9f7a66b60d70231628ded5dc096bad702bf088
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355600"
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject 類別
所有動畫物件的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CAnimationBaseObject : public CObject;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|多載。 建構的動畫物件。|  
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|解構函式。 動畫物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|加入分鏡腳本與封裝的動畫變數的轉換。|  
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|移除所有相關的轉換。|  
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|判斷動畫物件是否包含特定動畫變數。|  
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|建立動畫物件相關聯的轉換。|  
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|卸離的動畫物件，從父動畫控制器。|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|設定整數值已變更的事件處理常式。|  
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|設定值變更的事件處理常式。|  
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|會告知相關的轉換是否自動終結。|  
|[CAnimationBaseObject::GetGroupID](#getgroupid)|傳回目前的群組識別碼。|  
|[CAnimationBaseObject::GetObjectID](#getobjectid)|傳回目前的物件識別碼。|  
|[CAnimationBaseObject::GetUserData](#getuserdata)|傳回使用者定義資料。|  
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|設定旗標，會自動終結轉換的訂單。|  
|[CAnimationBaseObject::SetID](#setid)|設定新的識別碼。|  
|[CAnimationBaseObject::SetUserData](#setuserdata)|設定使用者定義的資料。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|會收集包含的動畫變數的指標。|  
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|建立動畫物件和其容器中所包含的動畫變數之間的關聯性。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|指定是否應該自動終結相關的轉換。|  
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|儲存使用者定義的資料。|  
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|指定的動畫物件的群組識別碼。|  
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|指定的動畫物件的物件識別碼。|  
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|父動畫控制器指標。|  
  
## <a name="remarks"></a>備註  
 這個類別會實作所有動畫物件的基本方法。 動畫物件可以代表值、 點、 大小、 矩形或應用程式，以及任何自訂的實體中的色彩。 動畫物件會儲存在動畫群組 （請參閱 CAnimationGroup）。 每個群組可以個別動畫顯示，而且可以被視為分鏡腳本的類比。 動畫物件會封裝一或多個動畫變數 （請參閱 CAnimationVariable），根據其邏輯表示法。 例如，CAnimationRect 包含四個動畫變數的矩形的每一端的一個變數。 每個動畫物件的類別會公開多載還得方法，應該用來將轉換套用至封裝的動畫變數。 動畫物件，可識別的物件識別碼 （選擇性） 和群組識別碼。 群組識別碼會在需要放置動畫物件至正確的群組，但如果未指定群組識別碼，物件會放置在預設群組識別碼為 0。 如果您呼叫具有不同的 GroupID SetID，動畫物件將移到另一個群組 （如有必要，建立新的群組）。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationBaseObject`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationbaseobject"></a>  CAnimationBaseObject:: ~ CAnimationBaseObject  
 解構函式。 動畫物件終結時呼叫。  
  
```  
virtual ~CAnimationBaseObject();
```  
  
##  <a name="applytransitions"></a>  CAnimationBaseObject::ApplyTransitions  
 加入分鏡腳本與封裝的動畫變數的轉換。  
  
```  
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 分鏡腳本指標。  
  
 `bDependOnKeyframes`  
 False 這個方法會加入只在不相依於主要畫面格的轉換。  
  
### <a name="return-value"></a>傳回值  
 如果已成功加入轉換，則為 TRUE。  
  
### <a name="remarks"></a>備註  
 新增相關的轉換，已加入至分鏡腳本的 （在衍生類別中的多載方法），還得使用。  
  
##  <a name="canimationbaseobject"></a>  CAnimationBaseObject::CAnimationBaseObject  
 建構的動畫物件。  
  
```  
CAnimationBaseObject();

 
CAnimationBaseObject(
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>參數  
 `nGroupID`  
 指定的群組識別碼。  
  
 `nObjectID`  
 指定物件識別碼。  
  
 `dwUserData`  
 使用者定義資料，可以與動畫物件相關聯，並稍後在執行階段擷取。  
  
### <a name="remarks"></a>備註  
 建構動畫物件，並指派預設物件識別碼 (0) 和群組識別碼 (0)。  
  
##  <a name="cleartransitions"></a>  CAnimationBaseObject::ClearTransitions  
 移除所有相關的轉換。  
  
```  
virtual void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>參數  
 `bAutodestroy`  
 指定是否自動終結轉換物件，或只從相關的清單中移除它們。  
  
### <a name="remarks"></a>備註  
 移除所有相關的轉換和終結它們 bAutodestroy 或 m_bAutodestroyTransitions 旗標為 TRUE。 轉換不會在堆疊上配置時，才應該會自動終結。 如果上述的旗標為 FALSE，轉換只會從相關的轉換的內部清單中移除。  
  
##  <a name="containsvariable"></a>  CAnimationBaseObject::ContainsVariable  
 判斷動畫物件是否包含特定動畫變數。  
  
```  
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>參數  
 `pVariable`  
 動畫變數的指標。  
  
### <a name="return-value"></a>傳回值  
 如果動畫變數包含在與動畫物件，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法可以用來判斷動畫物件中是否包含指定 pVariable 動畫變數。 動畫物件，根據其類型，可能會包含數個動畫變數。 例如，CAnimationColor 包含三個變數，其中每個色彩元件 （紅色、 綠色和藍色）。 當動畫變數的值變更時，Windows 動畫 API 傳送 ValueChanged 或 IntegerValueChanged 事件 （如果啟用），以及此事件的參數是介面 IUIAnimationVariable 動畫變數的指標。 這個方法可協助來取得以動畫的指標，從包含的 COM 物件的指標。  
  
##  <a name="createtransitions"></a>  CAnimationBaseObject::CreateTransitions  
 建立動畫物件相關聯的轉換。  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 建立轉換，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 衍生的動畫物件中封裝的動畫變數的清單進行迴圈，並建立每個動畫變數與相關聯的轉換。  
  
##  <a name="detachfromcontroller"></a>  CAnimationBaseObject::DetachFromController  
 卸離的動畫物件，從父動畫控制器。  
  
```  
void DetachFromController();
```  
  
### <a name="remarks"></a>備註  
 這個方法是在內部使用。  
  
##  <a name="enableintegervaluechangedevent"></a>  CAnimationBaseObject::EnableIntegerValueChangedEvent  
 設定整數值已變更的事件處理常式。  
  
```  
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 `pController`  
 父控制器指標。  
  
 `bEnable`  
 指定是否要啟用或停用整數值已變更事件。  
  
### <a name="remarks"></a>備註  
 如果已啟用的整數值已變更的事件處理常式，您可以處理這個 CAnimationController::OnAnimationIntegerValueChanged 方法，應該 CAnimationController 衍生類別中覆寫中的事件。 每次的動畫的整數值已變更，會呼叫這個方法。  
  
##  <a name="enablevaluechangedevent"></a>  CAnimationBaseObject::EnableValueChangedEvent  
 設定值變更的事件處理常式。  
  
```  
virtual void EnableValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 `pController`  
 父控制器指標。  
  
 `bEnable`  
 指定是否要啟用或停用變更值的事件。  
  
### <a name="remarks"></a>備註  
 如果已啟用的值變更的事件處理常式，您可以處理這個 CAnimationController::OnAnimationValueChanged 方法，應該 CAnimationController 衍生類別中覆寫中的事件。 每次的動畫值已變更，會呼叫這個方法。  
  
##  <a name="getanimationvariablelist"></a>  CAnimationBaseObject::GetAnimationVariableList  
 會收集包含的動畫變數的指標。  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `lst`  
 必須填入動畫物件中包含的動畫變數的清單。  
  
### <a name="remarks"></a>備註  
 這是必須在衍生類別中覆寫的純虛擬方法。 動畫物件，根據其類型，包含一或多個動畫變數。 例如，CAnimationPoint 包含兩個變數，X 和 Y 座標分別。 CAnimationBaseObject 的基底類別實作某些泛型的方法，處理動畫變數的清單： ApplyTransitions、 ClearTransitions、 EnableValueChangedEvent、 EnableIntegerValueChangedEvent。 這些方法會呼叫 GetAnimationVariableList，其中會填入衍生類別中包含特定的動畫物件中的實際動畫變數，則迴圈清單並執行必要的動作。 如果您建立自訂動畫物件時，您必須加入 lst 該物件中包含的所有動畫變數。  
  
##  <a name="getautodestroytransitions"></a>  CAnimationBaseObject::GetAutodestroyTransitions  
 會告知相關的轉換是否自動終結。  
  
```  
BOOL GetAutodestroyTransitions() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為 TRUE，自動; 終結相關的轉換如果為 FALSE，藉由呼叫應用程式應該會重新配置 transition 物件。  
  
### <a name="remarks"></a>備註  
 依預設這個旗標為 TRUE。 只有當您配置在堆疊上的轉換和/或轉換應該被呼叫的應用程式解除配置，請設定此旗標。  
  
##  <a name="getgroupid"></a>  CAnimationBaseObject::GetGroupID  
 傳回目前的群組識別碼。  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的群組識別碼。  
  
### <a name="remarks"></a>備註  
 使用這個方法來擷取群組的識別碼。 如果群組識別碼尚未設定明確建構函式中或與 SetID，的 0。  
  
##  <a name="getobjectid"></a>  CAnimationBaseObject::GetObjectID  
 傳回目前的物件識別碼。  
  
```  
UINT32 GetObjectID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的物件識別碼。  
  
### <a name="remarks"></a>備註  
 使用此方法來擷取物件識別碼。 如果物件識別碼尚未設定明確建構函式中或與 SetID，的 0。  
  
##  <a name="getuserdata"></a>  CAnimationBaseObject::GetUserData  
 傳回使用者定義資料。  
  
```  
DWORD GetUserData() const;  
```  
  
### <a name="return-value"></a>傳回值  
 自訂資料的值。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取在執行階段的自訂資料。 如果它未明確初始化 SetUserData 或建構函式中傳回的值將會是 0。  
  
##  <a name="m_bautodestroytransitions"></a>  CAnimationBaseObject::m_bAutodestroyTransitions  
 指定是否應該自動終結相關的轉換。  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
##  <a name="m_dwuserdata"></a>  CAnimationBaseObject::m_dwUserData  
 儲存使用者定義的資料。  
  
```  
DWORD m_dwUserData;  
```  
  
##  <a name="m_ngroupid"></a>  CAnimationBaseObject::m_nGroupID  
 指定的動畫物件的群組識別碼。  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_nobjectid"></a>  CAnimationBaseObject::m_nObjectID  
 指定的動畫物件的物件識別碼。  
  
```  
UINT32 m_nObjectID;  
```  
  
##  <a name="m_pparentcontroller"></a>  CAnimationBaseObject::m_pParentController  
 父動畫控制器指標。  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="setautodestroytransitions"></a>  CAnimationBaseObject::SetAutodestroyTransitions  
 設定旗標，會自動終結轉換的訂單。  
  
```  
void SetAutodestroyTransitions(BOOL bValue);
```  
  
### <a name="parameters"></a>參數  
 `bValue`  
 指定自動終結旗標。  
  
### <a name="remarks"></a>備註  
 只有當您配置的轉換物件使用新的運算子，請設定此旗標。 如果基於某些原因 transition 物件會在堆疊配置，自動終結旗標應為 FALSE。 依預設這個旗標為 TRUE。  
  
##  <a name="setid"></a>  CAnimationBaseObject::SetID  
 設定新的識別碼。  
  
```  
void SetID(
    UINT32 nObjectID,  
    UINT32 nGroupID = 0);
```  
  
### <a name="parameters"></a>參數  
 `nObjectID`  
 指定新的物件識別碼。  
  
 `nGroupID`  
 指定新的群組識別碼。  
  
### <a name="remarks"></a>備註  
 讓使用者能夠變更物件識別碼與群組識別碼。 如果新的群組識別碼不同於目前的識別碼，動畫物件移到另一個群組 （新的群組將會建立，如有必要）。  
  
##  <a name="setparentanimationobjects"></a>  CAnimationBaseObject::SetParentAnimationObjects  
 建立動畫物件和其容器中所包含的動畫變數之間的關聯性。  
  
```  
virtual void SetParentAnimationObjects();
```  
  
### <a name="remarks"></a>備註  
 這是可以用來建立動畫物件和其容器中所包含的動畫變數之間的關聯性的 helper。 它透過動畫變數執行迴圈，並設定父動畫物件，以每個動畫變數的返回指標。 在目前的實作中 CAnimationBaseObject::ApplyTransitions 建立實際的關聯性，因此回復指標未設定直到您呼叫 CAnimationGroup::Animate。 了解關聯性時可能會很有幫助您處理事件，且需要取得父動畫物件從 CAnimationVariable （使用 CAnimationVariable::GetParentAnimationObject）。  
  
##  <a name="setuserdata"></a>  CAnimationBaseObject::SetUserData  
 設定使用者定義的資料。  
  
```  
void SetUserData (DWORD dwUserData);
```  
  
### <a name="parameters"></a>參數  
 `dwUserData`  
 指定自訂的資料。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法將自訂資料與動畫物件產生關聯。 這項資料可能會稍後在執行階段由擷取 GetUserData。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
