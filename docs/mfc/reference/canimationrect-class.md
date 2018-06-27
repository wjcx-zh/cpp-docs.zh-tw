---
title: CAnimationRect 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3959ae03d40bac93ca6453c254e894b8782f5333
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957194"
---
# <a name="canimationrect-class"></a>CAnimationRect 類別
實作可以動畫顯示其邊緣的矩形功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CAnimationRect : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationRect::CAnimationRect](#canimationrect)|多載。 會建構一個動畫 rect 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationRect::AddTransition](#addtransition)|將加入左框線、 頂端、 右側和底部座標的轉換。|  
|[CAnimationRect::GetBottom](#getbottom)|提供存取權 CAnimationVariable 表示下方座標。|  
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|傳回矩形界限的預設值。|  
|[CAnimationRect::GetLeft](#getleft)|提供存取權 CAnimationVariable 表示左方的座標。|  
|[CAnimationRect::GetRight](#getright)|提供存取權 CAnimationVariable 代表右方座標。|  
|[CAnimationRect::GetTop](#gettop)|提供存取權 CAnimationVariable 代表上方座標。|  
|[CAnimationRect::GetValue](#getvalue)|傳回目前的值。|  
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|設定預設值。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|將封裝的動畫變數放入清單。 (覆寫[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationRect::operator RECT](#operator_rect)|CAnimationRect 將 RECT|  
|[CAnimationRect::operator =](#operator_eq)|將矩形指派給 CAnimationRect。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|指定矩形是否具有固定大小。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|表示下之封裝的動畫變數繫結的動畫矩形。|  
|[CAnimationRect::m_leftValue](#m_leftvalue)|表示左邊之封裝的動畫變數繫結的動畫矩形。|  
|[CAnimationRect::m_rightValue](#m_rightvalue)|代表權限的封裝的動畫變數繫結的動畫矩形。|  
|[CAnimationRect::m_szInitial](#m_szinitial)|指定動畫矩形的初始大小。|  
|[CAnimationRect::m_topValue](#m_topvalue)|表示上方之封裝的動畫變數繫結的動畫矩形。|  
  
## <a name="remarks"></a>備註  
 CAnimationRect 類別四個 CAnimationVariable 物件封裝起來，矩形中的應用程式來表示。 若要在應用程式中使用這個類別，只要具現化這個類別的物件、 將它加入至使用 CAnimationController::AddAnimationObject 動畫控制器，並呼叫還得針對每個轉換套用至左、 右的上方和下方座標。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationRect`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>  CAnimationRect::AddTransition  
 將加入左框線、 頂端、 右側和底部座標的轉換。  
  
```  
void AddTransition(
    CBaseTransition* pLeftTransition,  
    CBaseTransition* pTopTransition,  
    CBaseTransition* pRightTransition,  
    CBaseTransition* pBottomTransition);
```  
  
### <a name="parameters"></a>參數  
 *pLeftTransition*  
 指定的左半部的轉換。  
  
 *pTopTransition*  
 指定轉換的頂端。  
  
 *pRightTransition*  
 指定右端的轉換。  
  
 *pBottomTransition*  
 指定轉換的底部。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可將指定的轉換加入至要套用至動畫變數的每個矩形的邊轉換內部清單。 當您新增轉換時，它們不會立即套用，而儲存在內部清單。 轉換會套用 （加入至特定的值分鏡腳本） 當您呼叫 CAnimationController::AnimateGroup。 如果您不需要將轉換套用到其中一個矩形側邊，您可以傳遞 NULL。  
  
##  <a name="canimationrect"></a>  CAnimationRect::CAnimationRect  
 建構 CAnimationRect 物件。  
  
```  
CAnimationRect();

 
CAnimationRect(
    const CRect& rect,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);

 
CAnimationRect(
    const CPoint& pt,  
    const CSize& sz,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);

 
CAnimationRect(
    int nLeft,  
    int nTop,  
    int nRight,  
    int nBottom,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>參數  
 *rect*  
 指定預設的矩形。  
  
 *nGroupID*  
 指定的群組識別碼。  
  
 *nObjectID*  
 指定物件識別碼。  
  
 *dwUserData*  
 指定使用者定義的資料。  
  
 *pt*  
 左上角座標。  
  
 *sz*  
 矩形的大小。  
  
 *nLeft*  
 指定左界限的座標。  
  
 *nTop*  
 指定繫結的上方座標。  
  
 *nRight*  
 指定右界限的座標。  
  
 *nBottom*  
 指定繫結的下方座標。  
  
### <a name="remarks"></a>備註  
 預設值為左框線、 頂端、 右側和底部，物件識別碼和群組識別碼，將設定為 0，建構物件。 它們都可以在執行階段使用 SetDefaultValue 和 SetID 稍後變更。  
  
##  <a name="getanimationvariablelist"></a>  CAnimationRect::GetAnimationVariableList  
 將封裝的動畫變數放入清單。  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>參數  
 *lst*  
 函式傳回時，它會包含代表矩形的座標的四個 CAnimationVariable 物件的指標。  
  
##  <a name="getbottom"></a>  CAnimationRect::GetBottom  
 提供存取權 CAnimationVariable 表示下方座標。  
  
```  
CAnimationVariable& GetBottom();
```  
  
### <a name="return-value"></a>傳回值  
 封裝 CAnimationVariable 表示下方座標的參考。  
  
### <a name="remarks"></a>備註  
 您可以呼叫此方法以直接存取基礎 CAnimationVariable 表示下方座標。  
  
##  <a name="getdefaultvalue"></a>  CAnimationRect::GetDefaultValue  
 傳回矩形界限的預設值。  
  
```  
CRect GetDefaultValue();
```  
  
### <a name="return-value"></a>傳回值  
 CRect 值，其中包含左邊、 右邊、 上方和下方的預設值。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取先前已設定的建構函式或 SetDefaultValue 的預設值。  
  
##  <a name="getleft"></a>  CAnimationRect::GetLeft  
 提供存取權 CAnimationVariable 表示左方的座標。  
  
```  
CAnimationVariable& GetLeft();
```  
  
### <a name="return-value"></a>傳回值  
 參考封裝 CAnimationVariable 表示左方的座標。  
  
### <a name="remarks"></a>備註  
 您可以呼叫此方法以直接存取基礎 CAnimationVariable 表示左方的座標。  
  
##  <a name="getright"></a>  CAnimationRect::GetRight  
 提供存取權 CAnimationVariable 代表右方座標。  
  
```  
CAnimationVariable& GetRight();
```  
  
### <a name="return-value"></a>傳回值  
 封裝代表右方座標的 CAnimationVariable 參考。  
  
### <a name="remarks"></a>備註  
 您可以呼叫此方法以直接存取基礎 CAnimationVariable 代表右方座標。  
  
##  <a name="gettop"></a>  CAnimationRect::GetTop  
 提供存取權 CAnimationVariable 代表上方座標。  
  
```  
CAnimationVariable& GetTop();
```  
  
### <a name="return-value"></a>傳回值  
 參考封裝 CAnimationVariable 代表上方座標。  
  
### <a name="remarks"></a>備註  
 您可以呼叫此方法以直接存取基礎 CAnimationVariable 代表的上方座標。  
  
##  <a name="getvalue"></a>  CAnimationRect::GetValue  
 傳回目前的值。  
  
```  
BOOL GetValue(CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 *rect*  
 輸出。 此方法傳回時，包含目前的值。  
  
### <a name="return-value"></a>傳回值  
 已成功擷取目前的值; 如果為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取動畫矩形的目前值。 如果此方法失敗或基礎 COM 物件的左邊，頂端、 右側和底部尚未初始化，因為 rect 含有建構函式中或 SetDefaultValue 先前設定的預設值。  
  
##  <a name="m_bfixedsize"></a>  CAnimationRect::m_bFixedSize  
 指定矩形是否具有固定大小。  
  
```  
BOOL m_bFixedSize;  
```  
  
### <a name="remarks"></a>備註  
 這個成員為 true，如果矩形的大小是固定和右然後界值會重新計算左上角固定的大小根據移動每一次。 設定此值為 TRUE，即可輕易地移動螢幕上的矩形。 在此情況下轉換套用至右側和底部的座標會被忽略。 當您建構物件及 （或） 呼叫 SetDefaultValue 大小是在內部儲存。 依預設這個成員是設定為 FALSE。  
  
##  <a name="m_bottomvalue"></a>  CAnimationRect::m_bottomValue  
 表示下之封裝的動畫變數繫結的動畫矩形。  
  
```  
CAnimationVariable m_bottomValue;  
```  
  
##  <a name="m_leftvalue"></a>  CAnimationRect::m_leftValue  
 表示左邊之封裝的動畫變數繫結的動畫矩形。  
  
```  
CAnimationVariable m_leftValue;  
```  
  
##  <a name="m_rightvalue"></a>  CAnimationRect::m_rightValue  
 代表權限的封裝的動畫變數繫結的動畫矩形。  
  
```  
CAnimationVariable m_rightValue;  
```  
  
##  <a name="m_szinitial"></a>  CAnimationRect::m_szInitial  
 指定動畫矩形的初始大小。  
  
```  
CSize m_szInitial;  
```  
  
##  <a name="m_topvalue"></a>  CAnimationRect::m_topValue  
 表示上方之封裝的動畫變數繫結的動畫矩形。  
  
```  
CAnimationVariable m_topValue;  
```  
  
##  <a name="operator_rect"></a>  CAnimationRect::operator RECT  
 CAnimationRect 將 RECT  
  
```  
operator RECT();
```   
  
### <a name="return-value"></a>傳回值  
 目前的值為 RECT 動畫矩形  
  
### <a name="remarks"></a>備註  
 此函式內部呼叫 GetValue。 如果基於某些原因 GetValue 失敗，傳回的矩形會包含所有的矩形座標的預設值。  
  
##  <a name="operator_eq"></a>  CAnimationRect::operator =  
 將矩形指派給 CAnimationRect。  
  
```  
void operator=(const RECT& rect);
```  
  
### <a name="parameters"></a>參數  
 *rect*  
 動畫矩形的新值。  
  
### <a name="remarks"></a>備註  
 建議您動畫開始之前這樣做，因為這個運算子會呼叫 SetDefaultValue，重新建立色彩元件的基礎 COM 物件，如果尚未建立。 如果您已訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。  
  
##  <a name="setdefaultvalue"></a>  CAnimationRect::SetDefaultValue  
 設定預設值。  
  
```  
void SetDefaultValue(const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 *rect*  
 指定左框線、 頂端、 右側和底部的新預設值。  
  
### <a name="remarks"></a>備註  
 使用此函式設動畫物件的預設值。 這個方法會將預設值指派給矩形的界限。 如果尚未建立，它也會重建基礎 COM 物件。 如果您已訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
