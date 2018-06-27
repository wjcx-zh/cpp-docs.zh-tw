---
title: CAnimationPoint 類別 |Microsoft 文件
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
ms.openlocfilehash: 58c8c9aaaf212e98fdeff1e639bb09423304e643
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957399"
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
|[CAnimationPoint::AddTransition](#addtransition)|新增轉換 X 和 Y 座標。|  
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|傳回預設值為 X 和 Y 座標。|  
|[CAnimationPoint::GetValue](#getvalue)|傳回目前的值。|  
|[CAnimationPoint::GetX](#getx)|提供存取 CAnimationVariable 的 X 座標。|  
|[CAnimationPoint::GetY](#gety)|CAnimationVariable 可存取的 Y 座標。|  
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|設定預設值。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|將封裝的動畫變數放入清單。 (覆寫[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationPoint::operator CPoint](#operator_cpoint)|將 CPoint CAnimationPoint。|  
|[CAnimationPoint::operator =](#operator_eq)|將 ptSrc 指派給 CAnimationPoint。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationPoint::m_xValue](#m_xvalue)|表示 X 之封裝的動畫變數的動畫點座標。|  
|[CAnimationPoint::m_yValue](#m_yvalue)|封裝的動畫變數，表示動畫點的 Y 座標。|  
  
## <a name="remarks"></a>備註  
 CAnimationPoint 類別會封裝兩個 CAnimationVariable 物件，並可以代表應用程式中的點。 例如，您可以使用這個類別，以動畫方式顯示 （例如文字字串、 圓形、 點等），螢幕上的任何物件的位置。 若要在應用程式中使用這個類別，只要具現化這個類別的物件、 將它加入至使用 CAnimationController::AddAnimationObject 動畫控制器，並呼叫還得針對每個轉換套用至 X 和 （或） Y 座標。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationPoint`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>  CAnimationPoint::AddTransition  
 新增轉換 X 和 Y 座標。  
  
```  
void AddTransition(
    CBaseTransition* pXTransition,  
    CBaseTransition* pYTransition);
```  
  
### <a name="parameters"></a>參數  
 *pXTransition*  
 指標轉換的 X 座標。  
  
 *pYTransition*  
 指標轉換的 Y 座標。  
  
### <a name="remarks"></a>備註  
 呼叫此函式，指定的轉換加入內部清單的轉換套用至動畫變數的 X 和 Y 座標。 當您新增轉換時，它們不會立即套用，而儲存在內部清單。 轉換會套用 （加入至特定的值分鏡腳本） 當您呼叫 CAnimationController::AnimateGroup。 如果您不需要將轉換套用到其中一個座標，您可以傳遞 NULL。  
  
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
 *ptDefault*  
 指定預設點座標。  
  
 *nGroupID*  
 指定的群組識別碼。  
  
 *nObjectID*  
 指定物件識別碼。  
  
 *dwUserData*  
 指定使用者定義的資料。  
  
### <a name="remarks"></a>備註  
 建構具有預設屬性 CAnimationPoint 物件： 預設終點座標，群組識別碼和物件識別碼設定為 0。  
  
##  <a name="getanimationvariablelist"></a>  CAnimationPoint::GetAnimationVariableList  
 將封裝的動畫變數放入清單。  
  
```  
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>參數  
 *lst*  
 函式傳回時，它會包含代表 X 和 Y 座標的兩個 CAnimationVariable 物件的指標。  
  
##  <a name="getdefaultvalue"></a>  CAnimationPoint::GetDefaultValue  
 傳回預設值為 X 和 Y 座標。  
  
```  
CPoint GetDefaultValue();
```  
  
### <a name="return-value"></a>傳回值  
 點包含預設值。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取先前已設定的建構函式或 SetDefaultValue 的預設值。  
  
##  <a name="getvalue"></a>  CAnimationPoint::GetValue  
 傳回目前的值。  
  
```  
BOOL GetValue(CPoint& ptValue);
```  
  
### <a name="parameters"></a>參數  
 *ptValue*  
 輸出。 此方法傳回時，包含目前的值。  
  
### <a name="return-value"></a>傳回值  
 已成功擷取目前的值; 如果為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取動畫的目前值。 如果此方法失敗或基礎 COM 物件 x 和 Y 座標尚未初始化，ptValue 包含建構函式中或 SetDefaultValue 先前設定的預設值。  
  
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
 封裝 CAnimationVariable 表示 Y 座標的參考。  
  
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
 此函式內部呼叫 GetValue。 如果 GetValue 因故失敗，傳回的點將會包含預設值 x 和 Y 座標。  
  
##  <a name="operator_eq"></a>  CAnimationPoint::operator =  
 將 ptSrc 指派給 CAnimationPoint。  
  
```  
void operator=(const CPoint& ptSrc);
```  
  
### <a name="parameters"></a>參數  
 *ptSrc*  
 是指 CPoint 或點。  
  
### <a name="remarks"></a>備註  
 將 ptSrc 指派給 CAnimationPoint。 建議您不要的動畫開始之前此運算子會呼叫 SetDefaultValue，因為這會重新建立的基礎 COM 物件的 X 和 Y 座標如果尚未建立。 如果您已訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。  
  
##  <a name="setdefaultvalue"></a>  CAnimationPoint::SetDefaultValue  
 設定預設值。  
  
```  
void SetDefaultValue(const POINT& ptDefault);
```  
  
### <a name="parameters"></a>參數  
 *ptDefault*  
 指定預設點值。  
  
### <a name="remarks"></a>備註  
 使用此函式設動畫物件的預設值。 這個方法會指派預設值的動畫點的 X 和 Y 座標。 如果尚未建立，它也會重建基礎 COM 物件。 如果您已訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
