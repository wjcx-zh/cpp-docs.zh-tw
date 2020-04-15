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
ms.openlocfilehash: 5940cce6d55b95d8e1bac103cacc0bc828c213de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371111"
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
|[動畫顏色::動畫顏色](#canimationcolor)|已多載。 構造動畫顏色物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫顏色::新增轉換](#addtransition)|添加紅色、綠色和藍色元件的過渡。|
|[動畫顏色:取得B](#getb)|提供對表示藍色元件的 CAnimation 變數的訪問。|
|[動畫顏色:取得預設值](#getdefaultvalue)|傳回顏色元件的預設值。|
|[動畫顏色:取得G](#getg)|提供對表示綠色元件的 CAnimation 變數的訪問。|
|[動畫顏色:GetR](#getr)|提供對表示紅色元件的 CAnimation 變數的訪問。|
|[動畫顏色:取得價值](#getvalue)|返回當前值。|
|[動畫顏色::設定預設值](#setdefaultvalue)|設置預設值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[動畫顏色::抓取動畫變數清單](#getanimationvariablelist)|將封裝的動畫變數放入清單中。 ( 覆[寫動畫基礎物件:抓取動畫變數列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[動畫顏色::運算子 COLORREF](#operator_colorref)||
|[動畫顏色::運算符*](#operator_eq)|將顏色分配給 CAnimationColor。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[動畫顏色::m_bValue](#m_bvalue)|表示動畫顏色的藍色分量的封裝動畫變數。|
|[動畫顏色:m_gValue](#m_gvalue)|表示動畫顏色的綠色分量的封裝動畫變數。|
|[動畫顏色::m_rValue](#m_rvalue)|表示動畫顏色的紅色分量的封裝動畫變數。|

## <a name="remarks"></a>備註

CAnimationColor 類封裝了三個 CAnimationVariable 物件,可以在應用程式中表示顏色。 例如,可以使用此類對螢幕上任何對象的顏色(如文字顏色、背景顏色等)進行動畫處理。 要在應用程式中使用此類,只需實例化此類的物件,請使用 CAnimationController::addAnimationObject 將其添加到動畫控制器,並調用 AddTransition,以便應用於紅色、綠色和藍色元件的每個轉換。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[動畫基礎物件](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationcoloraddtransition"></a><a name="addtransition"></a>動畫顏色::新增轉換

添加紅色、綠色和藍色元件的過渡。

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>參數

*pR 轉換*<br/>
紅色元件的轉換。

*pG 轉換*<br/>
綠色元件的轉換。

*pB 轉換*<br/>
藍色元件的轉換。

### <a name="remarks"></a>備註

呼叫此函數以將指定的過渡添加到要應用於表示顏色分量的動畫變數的內部過渡清單中。 添加轉換時,不會立即應用這些轉換並存儲在內部清單中。 當您調用 CAnimationController::AnimateGroup 時,將應用轉換(添加到特定值的情節提要中)。 如果不需要對其中一個顏色分量應用過渡,則可以傳遞 NULL。

## <a name="canimationcolorcanimationcolor"></a><a name="canimationcolor"></a>動畫顏色::動畫顏色

構造 C動畫顏色物件。

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*顏色*<br/>
指定預設顏色。

*n集團ID*<br/>
指定組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
指定使用者定義的數據。

### <a name="remarks"></a>備註

對象建構的預設值為紅色、綠色、藍色、對象ID和組ID,該值將設置為0。 可以使用 SetDefaultValue 和 SetID 在運行時稍後更改它們。

## <a name="canimationcolorgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>動畫顏色::抓取動畫變數清單

將封裝的動畫變數放入清單中。

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>參數

*Lst*<br/>
當函數返回時,它包含指向表示紅色、綠色和藍色元件的三個 CAnimation 變數物件的指標。

## <a name="canimationcolorgetb"></a><a name="getb"></a>動畫顏色:取得B

提供對表示藍色元件的 CAnimation 變數的訪問。

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>傳回值

表示藍色元件的封裝 CAnimation 變數的引用。

### <a name="remarks"></a>備註

您可以調用此方法來直接訪問表示 Blue 元件的基礎 C動畫變數。

## <a name="canimationcolorgetdefaultvalue"></a><a name="getdefaultvalue"></a>動畫顏色:取得預設值

傳回顏色元件的預設值。

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>傳回值

包含 RGB 元件預設值的 COLORREF 值。

### <a name="remarks"></a>備註

調用此函數以檢索以前由建構函數或 SetDefaultValue 設置的預設值。

## <a name="canimationcolorgetg"></a><a name="getg"></a>動畫顏色:取得G

提供對表示綠色元件的 CAnimation 變數的訪問。

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>傳回值

表示綠色元件的封裝 CAnimation 變數的引用。

### <a name="remarks"></a>備註

您可以調用此方法來直接訪問表示綠色元件的基礎 C動畫變數。

## <a name="canimationcolorgetr"></a><a name="getr"></a>動畫顏色:GetR

提供對表示紅色元件的 CAnimation 變數的訪問。

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>傳回值

表示紅色分量的封裝 CAnimation 的引用。

### <a name="remarks"></a>備註

您可以調用此方法來直接訪問表示紅色元件的基礎 C動畫變數。

## <a name="canimationcolorgetvalue"></a><a name="getvalue"></a>動畫顏色:取得價值

返回當前值。

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
輸出。 當此方法返回時,包含當前值。

### <a name="return-value"></a>傳回值

TRUE,如果成功檢索當前值;如果成功檢索當前值,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

呼叫此函數以檢索動畫顏色的當前值。 如果此方法失敗或顏色元件的基礎 COM 物件尚未初始化,則顏色包含預設值,該值以前在建構函數或 SetDefaultValue 中設置。

## <a name="canimationcolorm_bvalue"></a><a name="m_bvalue"></a>動畫顏色::m_bValue

表示動畫顏色的藍色分量的封裝動畫變數。

```
CAnimationVariable m_bValue;
```

## <a name="canimationcolorm_gvalue"></a><a name="m_gvalue"></a>動畫顏色:m_gValue

表示動畫顏色的綠色分量的封裝動畫變數。

```
CAnimationVariable m_gValue;
```

## <a name="canimationcolorm_rvalue"></a><a name="m_rvalue"></a>動畫顏色::m_rValue

表示動畫顏色的紅色分量的封裝動畫變數。

```
CAnimationVariable m_rValue;
```

## <a name="canimationcoloroperator-colorref"></a><a name="operator_colorref"></a>動畫顏色::運算子 COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>傳回值

## <a name="canimationcoloroperator"></a><a name="operator_eq"></a>動畫顏色::運算符*

將顏色分配給 CAnimationColor。

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
指定新值動畫顏色。

### <a name="remarks"></a>備註

建議在動畫啟動之前執行此操作,因為此運算符稱為 SetDefaultValue,如果已創建顏色元件,則重新創建顏色元件的基礎 COM 物件。 如果將此動畫物件訂閱到事件(Value已更改或整數值更改),則需要重新啟用這些事件。

## <a name="canimationcolorsetdefaultvalue"></a><a name="setdefaultvalue"></a>動畫顏色::設定預設值

設置預設值。

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
為紅色、綠色和藍色元件指定新的預設值。

### <a name="remarks"></a>備註

使用此函數可為動畫物件設置預設值。 此方法將預設值分配給動畫顏色的顏色元件。 它還會重新創建基礎 COM 物件(如果已創建)。 如果將此動畫物件訂閱到事件(Value已更改或整數值更改),則需要重新啟用這些事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
