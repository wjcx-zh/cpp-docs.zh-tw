---
title: "CBaseTransition 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a925de05d301d213d67bb699af47d0453478ffc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cbasetransition-class"></a>CBaseTransition 類別
表示基本轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CBaseTransition : public CObject;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-enumerations"></a>公用列舉類型  
  
|名稱|描述|  
|----------|-----------------|  
|[CBaseTransition::TRANSITION_TYPE 列舉](#transition_type_enumeration)|定義目前 Windows 動畫 API 的 MFC 實作所支援的轉換類型。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CBaseTransition::CBaseTransition](#cbasetransition)|建構的基底轉換物件。|  
|[CBaseTransition:: ~ CBaseTransition](#cbasetransition__~cbasetransition)|解構函式。 轉換物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|將轉換加入至分鏡腳本。|  
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|將轉換加入至分鏡腳本。|  
|[CBaseTransition::Clear](#clear)|發行封裝 IUIAnimationTransition COM 物件。|  
|[CBaseTransition::Create](#create)|建立 COM 轉換。|  
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|傳回開始主要畫面格。|  
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|傳回相關變數的指標。|  
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|傳回開始主要畫面格。|  
|[CBaseTransition::GetTransition](#gettransition)|多載。 傳回基礎 COM 轉換物件的指標。|  
|[CBaseTransition::GetType](#gettype)|傳回轉換類型。|  
|[CBaseTransition::IsAdded](#isadded)|指示轉換是否已加入至分鏡腳本。|  
|[Cbasetransition::](#setkeyframes)|設定主要畫面格進行轉換。|  
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|建立動畫變數，並轉換之間的關聯性。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CBaseTransition::m_bAdded](#m_badded)|指定轉換是否已加入至分鏡腳本。|  
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|儲存指定在轉換結束的主要畫面格指標。|  
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|動畫變數，會與儲存在 m_transition 轉換動畫指標。|  
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|儲存的主要畫面格，指定轉換的開頭的指標。|  
|[CBaseTransition::m_transition](#m_transition)|儲存 IUIAnimationTransition 的指標。 如果尚未建立 COM 物件轉換為 NULL。|  
|[CBaseTransition::m_type](#m_type)|儲存的轉換類型。|  
  
## <a name="remarks"></a>備註  
 這個類別會封裝 IUIAnimationTransition 介面，並做為所有轉換的基底類別。  
  
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
 指標分鏡腳本，其中會以動畫顯示相關的變數。  
  
### <a name="return-value"></a>傳回值  
 為 TRUE，如果轉換已成功加入至分鏡腳本。  
  
### <a name="remarks"></a>備註  
 適用於轉換中的分鏡腳本的相關變數。 如果這是套用至這個分鏡腳本中的這個變數的第一個轉換，轉換會分鏡腳本的開頭開始。 否則，轉換會附加至最近新增到變數的轉換。  
  
##  <a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes  
 將轉換加入至分鏡腳本。  
  
```  
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>參數  
 `pStoryboard`  
 指標分鏡腳本，其中會以動畫顯示相關的變數。  
  
### <a name="return-value"></a>傳回值  
 為 TRUE，如果轉換已成功加入至分鏡腳本。  
  
### <a name="remarks"></a>備註  
 適用於轉換中的分鏡腳本的相關變數。 如果指定的開始主要畫面格，轉換就會開始該主要畫面格。 轉換指定的結束主要畫面格，如果開始主要畫面格時間點開始和停止在結束主要畫面格。 如果轉換已建立指定的持續時間參數，該持續時間會覆寫的開始和結束的主要畫面格之間的時間。 如果已指定沒有主要畫面格，轉換會附加至最近新增到變數的轉換。  
  
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
 應該從衍生的類別的 Create 方法呼叫這個方法，以避免 IUITransition 介面流失。  
  
##  <a name="create"></a>CBaseTransition::Create  
 建立 COM 轉換。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pLibrary`  
 會建立標準轉換轉換程式庫指標。 自訂的轉換，它可以是 NULL。  
  
 `pFactory`  
 轉換處理站，會建立自訂的轉換指標。 標準轉換，它可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 建立轉換 COM 物件，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這是純虛擬函式，必須在衍生類別中覆寫。 它是由基礎 COM 轉換物件具現化架構呼叫。  
  
##  <a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe  
 傳回開始主要畫面格。  
  
```  
CBaseKeyFrame* GetEndKeyframe();
```  
  
### <a name="return-value"></a>傳回值  
 主要畫面格或 NULL，如果轉換不應該插入主要畫面格之間的有效指標。  
  
### <a name="remarks"></a>備註  
 這個方法可以用來存取 SetKeyframes 先前所設定的主要畫面格物件。 轉換加入至分鏡腳本時，它是由上層程式碼進行呼叫。  
  
##  <a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable  
 傳回相關變數的指標。  
  
```  
CAnimationVariable* GetRelatedVariable();
```  
  
### <a name="return-value"></a>傳回值  
 動畫變數或如果尚未設定動畫變數的 SetRelatedVariable 為 NULL 的有效指標。  
  
### <a name="remarks"></a>備註  
 這是相關的動畫變數的存取子。  
  
##  <a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe  
 傳回開始主要畫面格。  
  
```  
CBaseKeyFrame* GetStartKeyframe();
```  
  
### <a name="return-value"></a>傳回值  
 主要畫面格或 NULL，如果轉換不應在主要畫面格之後啟動的有效指標。  
  
### <a name="remarks"></a>備註  
 這個方法可以用來存取 SetKeyframes 先前所設定的主要畫面格物件。 轉換加入至分鏡腳本時，它是由上層程式碼進行呼叫。  
  
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
 會建立標準轉換轉換程式庫指標。 自訂的轉換，它可以是 NULL。  
  
 `pFactory`  
 轉換處理站，會建立自訂的轉換指標。 標準轉換，它可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 無法建立有效指向 IUIAnimationTransition 或如果基礎轉換為 NULL。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回基礎 COM 轉換物件的指標，並在必要時建立它。  
  
##  <a name="gettype"></a>CBaseTransition::GetType  
 傳回轉換類型。  
  
```  
TRANSITION_TYPE GetType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 TRANSITION_TYPE 的其中一個列舉值。  
  
### <a name="remarks"></a>備註  
 這個方法可以用來識別轉換物件，其型別。 類型是設定在衍生類別中的建構函式。  
  
##  <a name="isadded"></a>CBaseTransition::IsAdded  
 指示轉換是否已加入至分鏡腳本。  
  
```  
BOOL IsAdded();
```  
  
### <a name="return-value"></a>傳回值  
 為 true，則會傳回轉換是否已新增到分鏡腳本，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 最上層的程式碼會加入到分鏡腳本轉換時，會在內部設定此旗標。  
  
##  <a name="m_badded"></a>CBaseTransition::m_bAdded  
 指定轉換是否已加入至分鏡腳本。  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe  
 儲存指定在轉換結束的主要畫面格指標。  
  
```  
CBaseKeyFrame* m_pEndKeyframe;  
```  
  
##  <a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable  
 動畫變數，會與儲存在 m_transition 轉換動畫指標。  
  
```  
CAnimationVariable* m_pRelatedVariable;  
```  
  
##  <a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe  
 儲存的主要畫面格，指定轉換的開頭的指標。  
  
```  
CBaseKeyFrame* m_pStartKeyframe;  
```  
  
##  <a name="m_transition"></a>CBaseTransition::m_transition  
 儲存 IUIAnimationTransition 的指標。 如果尚未建立 COM 物件轉換為 NULL。  
  
```  
ATL::CComPtr<IUIAnimationTransition> m_transition;  
```  
  
##  <a name="m_type"></a>CBaseTransition::m_type  
 儲存的轉換類型。  
  
```  
TRANSITION_TYPE m_type;  
```  
  
##  <a name="setkeyframes"></a>Cbasetransition::  
 設定主要畫面格進行轉換。  
  
```  
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,  
    CBaseKeyFrame* pEnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pStart`  
 主要畫面格，指定轉換的開頭。  
  
 `pEnd`  
 指定在轉換結束一個主要畫面格。  
  
### <a name="remarks"></a>備註  
 這個方法會告訴轉換至啟動指定的主要畫面格之後，以及 （選擇性） 如果不是 NULL，暫止結束之前指定的主要畫面格。 如果轉換已建立指定的持續時間參數，該持續時間會覆寫的開始和結束的主要畫面格之間的時間。  
  
##  <a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable  
 建立動畫變數，並轉換之間的關聯性。  
  
```  
void SetRelatedVariable(CAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>參數  
 `pVariable`  
 相關的動畫變數的指標。  
  
### <a name="remarks"></a>備註  
 建立動畫變數，並轉換之間的關聯性。 轉換僅用於一個變數。  
  
##  <a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE 列舉  
 定義目前 Windows 動畫 API 的 MFC 實作所支援的轉換類型。  
  
```  
enum TRANSITION_TYPE;  
```  
  
### <a name="remarks"></a>備註  
 轉換類型會設定特定轉換的建構函式。 例如，CSinusoidalTransitionFromRange 其類型設定為 SINUSOIDAL_FROM_RANGE。  
  
## <a name="see-also"></a>請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
