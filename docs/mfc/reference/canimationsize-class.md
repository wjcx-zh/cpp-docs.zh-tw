---
title: CAnimationSize 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
ms.openlocfilehash: 80a90dfa37bc1d2c3c84e6451ae23af7ded767c2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369708"
---
# <a name="canimationsize-class"></a>CAnimationSize 類別

實作可以動畫顯示其維度的大小物件功能。

## <a name="syntax"></a>語法

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[動畫大小:動畫大小](#canimationsize)|已多載。 構造動畫大小物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[動畫大小::新增轉換](#addtransition)|添加寬度和高度的過渡。|
|[動畫大小:取得CX](#getcx)|提供對表示寬度的「動畫變數」的訪問。|
|[動畫大小:取得](#getcy)|提供對表示高度的 CAnimation 變數的訪問。|
|[動畫大小:取得預設值](#getdefaultvalue)|返回"寬度"和"高度"的預設值。|
|[動畫大小:取得價值](#getvalue)|返回當前值。|
|[動畫大小:設定預設值](#setdefaultvalue)|設置預設值。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[動畫大小:抓取動畫變數清單](#getanimationvariablelist)|將封裝的動畫變數放入清單中。 ( 覆[寫動畫基礎物件:抓取動畫變數列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[動畫大小::運算子 CSize](#operator_csize)|將「動畫大小」轉換為「CSize」。|
|[動畫大小::操作員*](#operator_eq)|將 szSrc 分配給 CAnimation Size。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[動畫大小::m_cxValue](#m_cxvalue)|表示動畫大小寬度的封裝動畫變數。|
|[動畫大小::m_cyValue](#m_cyvalue)|表示動畫大小高度的封裝動畫變數。|

## <a name="remarks"></a>備註

CAnimationSize 類封裝了兩個 CAnimationvariable 物件,可以在應用程式中表示大小。 例如,可以使用此類為螢幕上任何二維物件的大小(如矩形、控制項等)設置動畫。 要在應用程式中使用此類,只需實例化此類的物件,請使用 CAnimationController::addAnimationObject 將其添加到動畫控制器,並調用要應用於寬度和/或高度的每個轉換的 AddTransition。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[動畫基礎物件](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="canimationsizeaddtransition"></a><a name="addtransition"></a>動畫大小::新增轉換

添加寬度和高度的過渡。

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>參數

*pCX 轉換*<br/>
指向寬度過渡的指標。

*pCY 轉換*<br/>
指向高度過渡的指標。

### <a name="remarks"></a>備註

呼叫此函數以將指定的過渡添加到要應用於"寬度"和"高"的動畫變數的內部過渡清單中。 添加轉換時,不會立即應用這些轉換並存儲在內部清單中。 當您調用 CAnimationController::AnimateGroup 時,將應用轉換(添加到特定值的情節提要中)。 如果不需要將轉換應用於其中一個維度,則可以傳遞 NULL。

## <a name="canimationsizecanimationsize"></a><a name="canimationsize"></a>動畫大小:動畫大小

構造動畫大小物件。

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>參數

*szDefault*<br/>
指定預設大小。

*n集團ID*<br/>
指定組識別碼。

*nObjectID*<br/>
指定物件識別碼。

*dwUserData*<br/>
指定使用者定義的數據。

### <a name="remarks"></a>備註

對象建構的預設值為寬度、高度、物件ID和組ID,該值將設置為0。 可以使用 SetDefaultValue 和 SetID 在運行時稍後更改它們。

## <a name="canimationsizegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>動畫大小:抓取動畫變數清單

將封裝的動畫變數放入清單中。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>參數

*Lst*<br/>
當函數返回時,它包含指向表示寬度和高度的兩個 CAnimation 變數物件的指標。

## <a name="canimationsizegetcx"></a><a name="getcx"></a>動畫大小:取得CX

提供對表示寬度的「動畫變數」的訪問。

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>傳回值

對表示寬度的封裝的 C動畫變數的引用。

### <a name="remarks"></a>備註

可以調用此方法來直接訪問表示寬度的基礎 C動畫變數。

## <a name="canimationsizegetcy"></a><a name="getcy"></a>動畫大小:取得

提供對表示高度的 CAnimation 變數的訪問。

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>傳回值

對表示高度的封裝的 C動畫變數的引用。

### <a name="remarks"></a>備註

可以調用此方法來直接訪問表示高度的基礎 C動畫變數。

## <a name="canimationsizegetdefaultvalue"></a><a name="getdefaultvalue"></a>動畫大小:取得預設值

返回"寬度"和"高度"的預設值。

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>傳回值

包含預設值的 CSize 物件。

### <a name="remarks"></a>備註

調用此函數以檢索以前由建構函數或 SetDefaultValue 設置的預設值。

## <a name="canimationsizegetvalue"></a><a name="getvalue"></a>動畫大小:取得價值

返回當前值。

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>參數

*szValue*<br/>
輸出。 當此方法返回時,包含當前值。

### <a name="return-value"></a>傳回值

TRUE,如果成功檢索當前值;如果成功檢索當前值,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

呼叫此函數以檢索動畫大小的當前值。 如果此方法失敗或「寬度和大小」的基礎 COM 物件尚未初始化,szValue 包含預設值,該預設值以前在建構函數或 SetDefaultValue 中設置。

## <a name="canimationsizem_cxvalue"></a><a name="m_cxvalue"></a>動畫大小::m_cxValue

表示動畫大小寬度的封裝動畫變數。

```
CAnimationVariable m_cxValue;
```

## <a name="canimationsizem_cyvalue"></a><a name="m_cyvalue"></a>動畫大小::m_cyValue

表示動畫大小高度的封裝動畫變數。

```
CAnimationVariable m_cyValue;
```

## <a name="canimationsizeoperator-csize"></a><a name="operator_csize"></a>動畫大小::運算子 CSize

將「動畫大小」轉換為「CSize」。

```
operator CSize();
```

### <a name="return-value"></a>傳回值

動畫大小的當前值為"大小"。

### <a name="remarks"></a>備註

此功能在內部調用 GetValue。 如果由於某種原因 GetValue 失敗,則返回的大小將包含"寬度"和"高度"的預設值。

## <a name="canimationsizeoperator"></a><a name="operator_eq"></a>動畫大小::操作員*

將 szSrc 分配給 CAnimation Size。

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>參數

*什施爾克*<br/>
指"大小"或"大小"。

### <a name="remarks"></a>備註

將 szSrc 分配給 CAnimation Size。 建議在動畫啟動之前執行此操作,因為此運算符稱為 SetDefaultValue,如果已創建"寬度"和"高度",則重新創建寬度和高度的基礎 COM 物件。 如果將此動畫物件訂閱到事件(Value已更改或整數值更改),則需要重新啟用這些事件。

## <a name="canimationsizesetdefaultvalue"></a><a name="setdefaultvalue"></a>動畫大小:設定預設值

設置預設值。

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>參數

*szDefault*<br/>
指定新的預設大小。

### <a name="remarks"></a>備註

使用此函數可為動畫物件設置預設值。 此方法將預設值分配給動畫大小的寬度和高度。 它還會重新創建基礎 COM 物件(如果已創建)。 如果將此動畫物件訂閱到事件(Value已更改或整數值更改),則需要重新啟用這些事件。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
