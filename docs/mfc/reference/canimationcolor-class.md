---
title: CAnimationColor 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: ee6003a22db78c2a510579c3d717fec887f8a6ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151171"
---
# <a name="canimationcolor-class"></a>CAnimationColor 類別

實作紅色、綠色和藍色元件可以動畫顯示的色彩功能。

## <a name="syntax"></a>語法

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAnimationColor::CAnimationColor](#canimationcolor)|多載。 建構的動畫色彩物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|將轉換為紅色、 綠色和藍色元件。|
|[CAnimationColor::GetB](#getb)|提供存取權 CAnimationVariable 代表藍色元件。|
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|傳回色彩元件的預設值。|
|[CAnimationColor::GetG](#getg)|提供存取權 CAnimationVariable 代表綠色元件。|
|[CAnimationColor::GetR](#getr)|提供存取權 CAnimationVariable 代表紅色元件。|
|[CAnimationColor::GetValue](#getvalue)|傳回目前的值。|
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|設定預設值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|將封裝的動畫變數放入清單中。 (覆寫[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAnimationColor::operator COLORREF](#operator_colorref)||
|[CAnimationColor::operator=](#operator_eq)|將色彩指派給 CAnimationColor 中。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CAnimationColor::m_bValue](#m_bvalue)|表示動畫色彩中的藍色元件之封裝的動畫變數。|
|[CAnimationColor::m_gValue](#m_gvalue)|表示動畫色彩中的綠色元件之封裝的動畫變數。|
|[CAnimationColor::m_rValue](#m_rvalue)|表示動畫色彩中的紅色元件之封裝的動畫變數。|

## <a name="remarks"></a>備註

CAnimationColor 類別包含三個 CAnimationVariable 物件和色彩在應用程式可以代表。 比方說，您可以使用這個類別以動畫顯示在螢幕上的任何物件的色彩 （例如文字色彩、 背景色彩等等）。 若要在應用程式中使用這個類別，只要具現化這個類別的物件、 將它新增至使用 CAnimationController::AddAnimationObject 的動畫控制器，並呼叫 AddTransition 針對每個轉換套用至紅色、 綠色和藍色元件。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationColor::AddTransition

將轉換為紅色、 綠色和藍色元件。

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>參數

*pRTransition*<br/>
紅色元件的轉換。

*pGTransition*<br/>
綠色元件的轉換。

*pBTransition*<br/>
藍色元件的轉換。

### <a name="remarks"></a>備註

呼叫此函式可將轉換套用至動畫變數表示色彩元件內部清單中指定的轉換。 當您新增轉換時，它們就會不立即套用，並儲存在內部清單。 轉換會套用 （加入至特定值如分鏡腳本） 當您呼叫 CAnimationController::AnimateGroup。 如果您不需要將轉換套用到其中一個色彩元件，您可以傳遞 NULL。

##  <a name="canimationcolor"></a>  CAnimationColor::CAnimationColor

建構 CAnimationColor 物件。

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*color*<br/>
指定預設色彩。

*nGroupID*<br/>
指定群組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
指定使用者定義的資料。

### <a name="remarks"></a>備註

在物件建構具有預設值為紅色、 綠色、 藍色，物件識別碼和群組識別碼，將會設定為 0。 它們都可以在執行階段使用 SetDefaultValue 和 SetID 稍後變更。

##  <a name="getanimationvariablelist"></a>  CAnimationColor::GetAnimationVariableList

將封裝的動畫變數放入清單中。

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>參數

*lst*<br/>
當函式傳回時，它會包含代表紅色、 綠色和藍色元件的三個 CAnimationVariable 物件的指標。

##  <a name="getb"></a>  CAnimationColor::GetB

提供存取權 CAnimationVariable 代表藍色元件。

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>傳回值

代表藍色元件的封裝 CAnimationVariable 參考。

### <a name="remarks"></a>備註

您可以呼叫此方法以直接存取基礎 CAnimationVariable 代表藍色元件。

##  <a name="getdefaultvalue"></a>  CAnimationColor::GetDefaultValue

傳回色彩元件的預設值。

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>傳回值

COLORREF 值，包含 RGB 元件的預設值。

### <a name="remarks"></a>備註

呼叫此函式可擷取預設值，也就先前設定的建構函式或 SetDefaultValue。

##  <a name="getg"></a>  CAnimationColor::GetG

提供存取權 CAnimationVariable 代表綠色元件。

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>傳回值

封裝 CAnimationVariable 代表綠色元件的參考。

### <a name="remarks"></a>備註

您可以呼叫此方法以直接存取基礎 CAnimationVariable 代表綠色元件。

##  <a name="getr"></a>  CAnimationColor::GetR

提供存取權 CAnimationVariable 代表紅色元件。

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>傳回值

代表紅色元件的封裝 CAnimationVariable 參考。

### <a name="remarks"></a>備註

您可以呼叫此方法以直接存取基礎 CAnimationVariable 代表紅色元件。

##  <a name="getvalue"></a>  CAnimationColor::GetValue

傳回目前的值。

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>參數

*color*<br/>
輸出。 這個方法傳回時，包含目前的值。

### <a name="return-value"></a>傳回值

為 TRUE，如果已成功擷取目前的值;否則為 FALSE。

### <a name="remarks"></a>備註

呼叫此函式可擷取目前的動畫色彩值。 如果此方法失敗或尚未初始化色彩元件的基礎 COM 物件，色彩就會包含在建構函式或 SetDefaultValue 先前設定的預設值。

##  <a name="m_bvalue"></a>  CAnimationColor::m_bValue

表示動畫色彩中的藍色元件之封裝的動畫變數。

```
CAnimationVariable m_bValue;
```

##  <a name="m_gvalue"></a>  CAnimationColor::m_gValue

表示動畫色彩中的綠色元件之封裝的動畫變數。

```
CAnimationVariable m_gValue;
```

##  <a name="m_rvalue"></a>  CAnimationColor::m_rValue

表示動畫色彩中的紅色元件之封裝的動畫變數。

```
CAnimationVariable m_rValue;
```

##  <a name="operator_colorref"></a>  CAnimationColor::operator COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>傳回值

##  <a name="operator_eq"></a>  CAnimationColor::operator=

將色彩指派給 CAnimationColor 中。

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
指定新值動畫的色彩。

### <a name="remarks"></a>備註

建議您在動畫開始之前這樣做，因為此運算子會呼叫 SetDefaultValue，重新建立色彩元件的基礎 COM 物件，如果尚未建立。 如果您訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。

##  <a name="setdefaultvalue"></a>  CAnimationColor::SetDefaultValue

設定預設值。

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
指定新的預設值為紅色、 綠色和藍色元件。

### <a name="remarks"></a>備註

此函式可用於設定動畫物件的預設值。 這個方法會將預設值指派給動畫色彩的色彩元件。 如果尚未建立，它也會重建基礎 COM 物件。 如果您訂閱事件 （ValueChanged 或 IntegerValueChanged） 這個動畫物件時，您需要重新啟用這些事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
