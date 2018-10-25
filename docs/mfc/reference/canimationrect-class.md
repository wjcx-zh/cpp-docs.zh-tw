---
title: CAnimationRect 類別 |Microsoft Docs
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
ms.openlocfilehash: ec22bfd2805f4af432821c4aaeb350a2cf635cfa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083421"
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
|[CAnimationRect::CAnimationRect](#canimationrect)|多載。 建構動畫矩形物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|將左側、 頂端、 右側和底部座標的轉換。|
|[CAnimationRect::GetBottom](#getbottom)|提供存取權 CAnimationVariable 代表底端座標。|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|傳回矩形的界限的預設值。|
|[CAnimationRect::GetLeft](#getleft)|提供存取權 CAnimationVariable 表示左的座標。|
|[CAnimationRect::GetRight](#getright)|提供存取權 CAnimationVariable 表示右的座標。|
|[CAnimationRect::GetTop](#gettop)|提供存取權 CAnimationVariable 代表上方座標。|
|[CAnimationRect::GetValue](#getvalue)|傳回目前的值。|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|設定預設值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|將封裝的動畫變數放入清單中。 (覆寫[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAnimationRect::operator RECT](#operator_rect)|CAnimationRect 將就是 RECT。|
|[CAnimationRect::operator =](#operator_eq)|給 CAnimationRect rect。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|指定的矩形是否具有固定大小。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|表示下之封裝的動畫變數繫結的動畫矩形。|
|[CAnimationRect::m_leftValue](#m_leftvalue)|表示左之封裝的動畫變數繫結的動畫矩形。|
|[CAnimationRect::m_rightValue](#m_rightvalue)|表示權限之封裝的動畫變數繫結的動畫矩形。|
|[CAnimationRect::m_szInitial](#m_szinitial)|指定初始大小的動畫矩形。|
|[CAnimationRect::m_topValue](#m_topvalue)|表示最上方之封裝的動畫變數繫結的動畫矩形。|

## <a name="remarks"></a>備註

CAnimationRect 類別包含四個 CAnimationVariable 物件和矩形中的應用程式可以代表。 若要在應用程式中使用這個類別，只要具現化這個類別的物件、 將它新增至使用 CAnimationController::AddAnimationObject 的動畫控制器，並呼叫 AddTransition 針對每個轉換套用至左、 右的頂端和底端座標。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationRect::AddTransition

將左側、 頂端、 右側和底部座標的轉換。

```
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>參數

*pLeftTransition*<br/>
指定左邊算起的轉換。

*pTopTransition*<br/>
指定轉換的上方。

*pRightTransition*<br/>
指定之右端的轉換。

*pBottomTransition*<br/>
指定下方的轉換。

### <a name="remarks"></a>備註

呼叫此函式可將轉換套用至動畫變數的每個矩形邊內部清單中指定的轉換。 當您新增轉換時，它們就會不立即套用，並儲存在內部清單。 轉換會套用 （加入至特定值如分鏡腳本） 當您呼叫 CAnimationController::AnimateGroup。 如果您不需要將轉換套用到其中一個矩形邊，您可以傳遞 NULL。

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

*rect*<br/>
指定預設的矩形。

*nGroupID*<br/>
指定群組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
指定使用者定義的資料。

*太平洋時間*<br/>
左上角座標。

*sz*<br/>
矩形的大小。

*nLeft*<br/>
指定左界限的座標。

*nTop*<br/>
指定繫結的頂端座標。

*nRight*<br/>
指定右界限的座標。

*nBottom*<br/>
指定繫結的底端座標。

### <a name="remarks"></a>備註

在物件建構具有預設值為左框線、 頂端、 右側和底部，物件識別碼和群組識別碼，將會設定為 0。 它們都可以在執行階段使用 SetDefaultValue 和 SetID 稍後變更。

##  <a name="getanimationvariablelist"></a>  CAnimationRect::GetAnimationVariableList

將封裝的動畫變數放入清單中。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>參數

*lst*<br/>
當函式傳回時，它會包含代表矩形的座標的四個 CAnimationVariable 物件的指標。

##  <a name="getbottom"></a>  CAnimationRect::GetBottom

提供存取權 CAnimationVariable 代表底端座標。

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>傳回值

封裝 CAnimationVariable 表示下方座標的參考。

### <a name="remarks"></a>備註

您可以呼叫此方法以直接存取基礎 CAnimationVariable 代表的底端座標。

##  <a name="getdefaultvalue"></a>  CAnimationRect::GetDefaultValue

傳回矩形的界限的預設值。

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>傳回值

CRect 值，包含左框線、 右邊、 上方和下方的預設值。

### <a name="remarks"></a>備註

呼叫此函式可擷取預設值，也就先前設定的建構函式或 SetDefaultValue。

##  <a name="getleft"></a>  CAnimationRect::GetLeft

提供存取權 CAnimationVariable 表示左的座標。

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>傳回值

封裝 CAnimationVariable 表示左的座標的參考。

### <a name="remarks"></a>備註

您可以呼叫此方法以直接存取基礎 CAnimationVariable 表示左的座標。

##  <a name="getright"></a>  CAnimationRect::GetRight

提供存取權 CAnimationVariable 表示右的座標。

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>傳回值

封裝 CAnimationVariable 表示右的座標參考。

### <a name="remarks"></a>備註

您可以呼叫此方法以直接存取基礎 CAnimationVariable 代表的右邊座標。

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

*rect*<br/>
輸出。 這個方法傳回時，包含目前的值。

### <a name="return-value"></a>傳回值

為 TRUE，如果已成功擷取目前的值;否則為 FALSE。

### <a name="remarks"></a>備註

呼叫此函式以擷取動畫矩形的目前值。 如果此方法失敗或基礎 COM 物件的左邊，頂端、 右側和底部中尚未初始化，矩形會包含在建構函式或 SetDefaultValue 先前設定的預設值。

##  <a name="m_bfixedsize"></a>  CAnimationRect::m_bFixedSize

指定的矩形是否具有固定大小。

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>備註

如果這個成員為 true，然後矩形的大小是固定和右和下值每的次重新計算移左上角依固定的大小。 您可以將此值設為 TRUE，輕鬆地移動螢幕周圍的矩形。 在此情況下，系統會忽略轉換套用至右側和底端座標。 當您建構物件和/或呼叫 SetDefaultValue 時，會在內部儲存大小。 依預設這個成員設定為 FALSE。

##  <a name="m_bottomvalue"></a>  CAnimationRect::m_bottomValue

表示下之封裝的動畫變數繫結的動畫矩形。

```
CAnimationVariable m_bottomValue;
```

##  <a name="m_leftvalue"></a>  CAnimationRect::m_leftValue

表示左之封裝的動畫變數繫結的動畫矩形。

```
CAnimationVariable m_leftValue;
```

##  <a name="m_rightvalue"></a>  CAnimationRect::m_rightValue

表示權限之封裝的動畫變數繫結的動畫矩形。

```
CAnimationVariable m_rightValue;
```

##  <a name="m_szinitial"></a>  CAnimationRect::m_szInitial

指定初始大小的動畫矩形。

```
CSize m_szInitial;
```

##  <a name="m_topvalue"></a>  CAnimationRect::m_topValue

表示最上方之封裝的動畫變數繫結的動畫矩形。

```
CAnimationVariable m_topValue;
```

##  <a name="operator_rect"></a>  CAnimationRect::operator RECT

CAnimationRect 將就是 RECT。

```
operator RECT();
```

### <a name="return-value"></a>傳回值

目前的值的動畫矩形為就是 RECT。

### <a name="remarks"></a>備註

此函式會在內部呼叫 GetValue。 如果基於某些原因的 GetValue 失敗，傳回的矩形會包含所有的矩形座標的預設值。

##  <a name="operator_eq"></a>  CAnimationRect::operator =

給 CAnimationRect rect。

```
void operator=(const RECT& rect);
```

### <a name="parameters"></a>參數

*rect*<br/>
動畫矩形的新值。

### <a name="remarks"></a>備註

建議您在動畫開始之前這樣做，因為此運算子會呼叫 SetDefaultValue，重新建立色彩元件的基礎 COM 物件，如果尚未建立。 如果您訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。

##  <a name="setdefaultvalue"></a>  CAnimationRect::SetDefaultValue

設定預設值。

```
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>參數

*rect*<br/>
指定左框線、 頂端、 右側和底部的新預設值。

### <a name="remarks"></a>備註

此函式可用於設定動畫物件的預設值。 這個方法會將預設值指派至矩形的界限。 如果尚未建立，它也會重建基礎 COM 物件。 如果您訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
