---
title: "CBaseTransition 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
dev_langs:
- C++
helpviewer_keywords:
- CBaseTransition class
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
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
ms.openlocfilehash: b979d03587ada42486d0462733dfe6fd22f9f7cc
ms.lasthandoff: 02/24/2017

---
# <a name="cbasetransition-class"></a>CBaseTransition 類別
表示基本轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CBaseTransition : public CObject;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-enumerations"></a>公用列舉類型  
  
|名稱|說明|  
|----------|-----------------|  
|[CBaseTransition::TRANSITION_TYPE 列舉型別](#transition_type_enumeration)|定義目前的視窗動畫 API MFC 實作所支援的轉換類型。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CBaseTransition::CBaseTransition](#cbasetransition)|建構的基底轉換物件。|  
|[CBaseTransition:: ~ CBaseTransition](#cbasetransition__~cbasetransition)|解構函式。 轉換物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|將轉換加入至分鏡腳本。|  
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|將轉換加入至分鏡腳本。|  
|[CBaseTransition::Clear](#clear)|發行封裝 IUIAnimationTransition COM 物件。|  
|[CBaseTransition::Create](#create)|建立 COM 轉換。|  
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|傳回開始主要畫面格。|  
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|傳回相關變數的指標。|  
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|傳回開始主要畫面格。|  
|[CBaseTransition::GetTransition](#gettransition)|多載。 傳回基礎 COM 轉換物件的指標。|  
|[CBaseTransition::GetType](#gettype)|傳回轉換型別。|  
|[CBaseTransition::IsAdded](#isadded)|會指示轉換是否已經新增至腳本。|  
|[CBaseTransition::SetKeyframes](#setkeyframes)|設定主要畫面格的轉換。|  
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|建立轉換動畫變數之間關聯性。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CBaseTransition::m_bAdded](#m_badded)|指定轉換是否已經新增至腳本。|  
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|儲存指定轉換結束的主要畫面格的指標。|  
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|動畫變數動畫與轉換儲存在 m_transition 指標。|  
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|儲存指定轉換的開頭的主要畫面格的指標。|  
|[CBaseTransition::m_transition](#m_transition)|儲存 IUIAnimationTransition 的指標。 如果尚未建立 COM 物件轉換為 NULL。|  
|[CBaseTransition::m_type](#m_type)|儲存轉換類型。|  
  
## <a name="remarks"></a>備註  
 這個類別會封裝 IUIAnimationTransition 介面，並做為基底類別之所有轉換。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseTransition`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="_dtorcbasetransition"></a>CBaseTransition:: ~ CBaseTransition  
 解構函式。 轉換物件終結時呼叫。  
  
```  
virtual ~CBaseTransition();
```  
  
##  <a name="addtostoryboard"></a>CBaseTransition::AddToStoryboard  
 將轉換加入至分鏡腳本。  
  
```  
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 指標分鏡腳本，這會以動畫顯示相關的變數。  
  
### <a name="return-value"></a>傳回值  
 如果為 TRUE，轉換已成功新增至腳本。  
  
### <a name="remarks"></a>備註  
 套用轉換至腳本中相關的變數。 如果這是套用至這個腳本中的這個變數的第一個轉換，轉換就會開始腳本的開始。 否則，轉換會附加至最近新增至變數的轉換。  
  
##  <a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes  
 將轉換加入至分鏡腳本。  
  
```  
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 指標分鏡腳本，這會以動畫顯示相關的變數。  
  
### <a name="return-value"></a>傳回值  
 如果為 TRUE，轉換已成功新增至腳本。  
  
### <a name="remarks"></a>備註  
 套用轉換至腳本中相關的變數。 如果指定的開始主要畫面格，轉換會開始在該主要畫面格。 如果指定的結束主要畫面格，轉換就會開始在開始主要畫面格，並停止在結束主要畫面格。 如果指定的持續時間參數建立轉換，這段時間會覆寫的持續時間的開始和結束的主要畫面格之間的時間。 如果沒有主要畫面格已指定，轉換會附加至最近新增至變數的轉換。  
  
##  <a name="cbasetransition"></a>CBaseTransition::CBaseTransition  
 建構的基底轉換物件。  
  
```  
CBaseTransition();
```  
  
##  <a name="clear"></a>CBaseTransition::Clear  
 發行封裝 IUIAnimationTransition COM 物件。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 若要防止 IUITransition 介面流失，應該從衍生的類別的建立方法呼叫這個方法。  
  
##  <a name="create"></a>CBaseTransition::Create  
 建立 COM 轉換。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pLibrary`  
 這會建立標準轉換轉換程式庫指標。 自訂轉換，它可以是 NULL。  
  
 `pFactory`  
 轉換處理站，其會建立自訂轉換指標。 標準轉換，它可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 建立轉換 COM 物件，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這是純虛擬函式必須在衍生類別中被覆寫。 它會呼叫基礎 COM 轉換物件具現化架構。  
  
##  <a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe  
 傳回開始主要畫面格。  
  
```  
CBaseKeyFrame* GetEndKeyframe();
```  
  
### <a name="return-value"></a>傳回值  
 主要畫面格或 NULL，如果轉換不應該插入主要畫面格之間的有效指標。  
  
### <a name="remarks"></a>備註  
 這個方法可以用來存取 SetKeyframes 先前所設定的主要畫面格物件。 當轉換正在新增至腳本，則是由上層程式碼進行呼叫。  
  
##  <a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable  
 傳回相關變數的指標。  
  
```  
CAnimationVariable* GetRelatedVariable();
```  
  
### <a name="return-value"></a>傳回值  
 有效的動畫變數，或如果不設定 SetRelatedVariable 動畫變數為 NULL 指標。  
  
### <a name="remarks"></a>備註  
 這是相關的動畫變數的存取子。  
  
##  <a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe  
 傳回開始主要畫面格。  
  
```  
CBaseKeyFrame* GetStartKeyframe();
```  
  
### <a name="return-value"></a>傳回值  
 主要畫面格或如果主要畫面格之後，請勿開始轉換為 NULL 的有效指標。  
  
### <a name="remarks"></a>備註  
 這個方法可以用來存取 SetKeyframes 先前所設定的主要畫面格物件。 當轉換正在新增至腳本，則是由上層程式碼進行呼叫。  
  
##  <a name="gettransition"></a>CBaseTransition::GetTransition  
 傳回基礎 COM 轉換物件的指標。  
  
```  
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory);  
  
IUIAnimationTransition* GetTransition();
```  
  
### <a name="parameters"></a>參數  
 `pLibrary`  
 這會建立標準轉換轉換程式庫指標。 自訂轉換，它可以是 NULL。  
  
 `pFactory`  
 轉換處理站，其會建立自訂轉換指標。 標準轉換，它可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 無法建立有效的指標 IUIAnimationTransition 或如果基礎轉換為 NULL。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回基礎 COM 轉換物件的指標，並在必要時建立它。  
  
##  <a name="gettype"></a>CBaseTransition::GetType  
 傳回轉換型別。  
  
```  
TRANSITION_TYPE GetType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 TRANSITION_TYPE 的其中一個列舉值。  
  
### <a name="remarks"></a>備註  
 這個方法可以用來識別轉換物件，其型別。 類型 設定在衍生類別中的建構函式。  
  
##  <a name="isadded"></a>CBaseTransition::IsAdded  
 會指示轉換是否已經新增至腳本。  
  
```  
BOOL IsAdded();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 TRUE 轉換是否已新增至腳本，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 最上層程式碼會加入至分鏡腳本的轉換時，會在內部設定這個旗標。  
  
##  <a name="m_badded"></a>CBaseTransition::m_bAdded  
 指定轉換是否已經新增至腳本。  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe  
 儲存指定轉換結束的主要畫面格的指標。  
  
```  
CBaseKeyFrame* m_pEndKeyframe;  
```  
  
##  <a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable  
 動畫變數動畫與轉換儲存在 m_transition 指標。  
  
```  
CAnimationVariable* m_pRelatedVariable;  
```  
  
##  <a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe  
 儲存指定轉換的開頭的主要畫面格的指標。  
  
```  
CBaseKeyFrame* m_pStartKeyframe;  
```  
  
##  <a name="m_transition"></a>CBaseTransition::m_transition  
 儲存 IUIAnimationTransition 的指標。 如果尚未建立 COM 物件轉換為 NULL。  
  
```  
ATL::CComPtr<IUIAnimationTransition> m_transition;  
```  
  
##  <a name="m_type"></a>CBaseTransition::m_type  
 儲存轉換類型。  
  
```  
TRANSITION_TYPE m_type;  
```  
  
##  <a name="setkeyframes"></a>CBaseTransition::SetKeyframes  
 設定主要畫面格的轉換。  
  
```  
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,  
    CBaseKeyFrame* pEnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pStart`  
 主要畫面格，指定轉換的開頭。  
  
 `pEnd`  
 主要畫面格，指定轉換的結尾。  
  
### <a name="remarks"></a>備註  
 這個方法會告訴轉換到指定主要畫面格之後啟動，並選擇性地，如果不是 NULL，暫止結束之前指定的主要畫面格。 如果指定的持續時間參數建立轉換，這段時間會覆寫的持續時間的開始和結束的主要畫面格之間的時間。  
  
##  <a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable  
 建立轉換動畫變數之間關聯性。  
  
```  
void SetRelatedVariable(CAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>參數  
 `pVariable`  
 相關的動畫變數的指標。  
  
### <a name="remarks"></a>備註  
 建立轉換動畫變數之間關聯性。 轉換只能用於一個變數。  
  
##  <a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE 列舉型別  
 定義目前的視窗動畫 API MFC 實作所支援的轉換類型。  
  
```  
enum TRANSITION_TYPE;  
```  
  
### <a name="remarks"></a>備註  
 轉換類型會設定特定轉換的建構函式。 例如，CSinusoidalTransitionFromRange 會將其類型設定為 SINUSOIDAL_FROM_RANGE。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

