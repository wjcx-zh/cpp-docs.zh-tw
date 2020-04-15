---
title: CBaseTransition 類別
ms.date: 03/27/2019
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
ms.openlocfilehash: 8339785fd10fa3dcef1c0fb573310762dc2d2405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352838"
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
|[CBase 轉換::TRANSITION_TYPE枚舉](#transition_type_enumeration)|定義 Windows 動畫 API MFC 實現目前支援的過渡類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CBase 轉換:CBase 轉換](#cbasetransition)|構造基本過渡物件。|
|[CBase 轉換:*CBase 轉換](#_dtorcbasetransition)|解構函式。 在銷毀過渡物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBase 轉換::新增到故事板](#addtostoryboard)|向情節提要添加過渡。|
|[CBase 轉換::添加到故事板的幀](#addtostoryboardatkeyframes)|向情節提要添加過渡。|
|[CBase 轉換:清除](#clear)|釋放封裝的 IUI 動畫轉換 COM 物件。|
|[CBase 轉換:建立](#create)|創建 COM 轉換。|
|[CBase 轉換:取得結束關鍵幀](#getendkeyframe)|返回啟動關鍵幀。|
|[CBase 轉換:取得相關變數](#getrelatedvariable)|返回指向相關變數的指標。|
|[CBase 轉換:取得啟動關鍵畫面](#getstartkeyframe)|返回啟動關鍵幀。|
|[CBase 轉換:取得過渡](#gettransition)|已多載。 返回指向基礎 COM 過渡物件的指標。|
|[CBase 轉換:抓取類型](#gettype)|返回轉換類型。|
|[CBase 轉換:已新增](#isadded)|告訴是否已將過渡添加到情節提要中。|
|[CBase 轉換::設定關鍵幀](#setkeyframes)|為過渡設置關鍵幀。|
|[CBase 轉換::設定相關變數](#setrelatedvariable)|在動畫變數和轉換之間建立關係。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CBase 轉換:m_bAdded](#m_badded)|指定過渡是否已添加到情節提要。|
|[CBase 轉換:m_pEndKeyframe](#m_pendkeyframe)|存儲指向指定過渡結束的關鍵幀的指標。|
|[CBase 轉換:m_pRelatedVariable](#m_prelatedvariable)|指向動畫變數的指標,該變數使用存儲在m_transition中的過渡進行動畫處理。|
|[CBase 轉換:m_pStartKeyframe](#m_pstartkeyframe)|存儲指向指定轉換開始的關鍵幀的指標。|
|[CBase 轉換:m_transition](#m_transition)|存儲指向 IUI 動畫轉換的指標。 如果未建立 COM 過渡物件,則為 NULL。|
|[CBase 轉換:m_type](#m_type)|存儲過渡類型。|

## <a name="remarks"></a>備註

此類封裝 IUIAnimation 轉換介面,並用作所有轉換的基類。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>需求

**標頭：** afxanimationcontroller.h

## <a name="cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a>CBase 轉換:*CBase 轉換

解構函式。 在銷毀過渡物件時調用。

```
virtual ~CBaseTransition();
```

## <a name="cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a>CBase 轉換::新增到故事板

向情節提要添加過渡。

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>參數

*板*<br/>
指向情節提要的指標,它將為相關變數設置動畫。

### <a name="return-value"></a>傳回值

如果過渡已成功添加到情節提要,則為 TRUE。

### <a name="remarks"></a>備註

將轉換應用於情節提要中的相關變數。 如果這是在此情節提要中應用於此變數的第一個過渡,則過渡從情節提要的開頭開始。 否則,過渡將追加到最近添加到變數的過渡。

## <a name="cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a>CBase 轉換::添加到故事板的幀

向情節提要添加過渡。

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>參數

*板*<br/>
指向情節提要的指標,它將為相關變數設置動畫。

### <a name="return-value"></a>傳回值

如果過渡已成功添加到情節提要,則為 TRUE。

### <a name="remarks"></a>備註

將轉換應用於情節提要中的相關變數。 如果指定了啟動關鍵幀,則轉換從該關鍵幀開始。 如果指定了端鍵幀,則過渡從啟動關鍵幀開始,並在端鍵幀停止。 如果轉換是在指定持續時間參數下創建的,則該持續時間將覆蓋在開始和結束關鍵幀之間的持續時間。 如果未指定關鍵幀,則過渡將追加到最近添加到變數的過渡中。

## <a name="cbasetransitioncbasetransition"></a><a name="cbasetransition"></a>CBase 轉換:CBase 轉換

構造基本過渡物件。

```
CBaseTransition();
```

## <a name="cbasetransitionclear"></a><a name="clear"></a>CBase 轉換:清除

釋放封裝的 IUI 動畫轉換 COM 物件。

```
void Clear();
```

### <a name="remarks"></a>備註

應從派生類的 Create 方法調用此方法,以防止 IUI 轉換介面洩漏。

## <a name="cbasetransitioncreate"></a><a name="create"></a>CBase 轉換:建立

創建 COM 轉換。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>參數

*p庫*<br/>
指向過渡庫的指標,該指標創建標準轉換。 對於自訂轉換,它可以為 NULL。

*pFactory*<br/>
指向轉換工廠的指標,該指標創建自定義轉換。 對於標準轉換,它可以為 NULL。

### <a name="return-value"></a>傳回值

如果成功建立了轉換 COM 物件,則為 TRUE;如果成功創建了轉換 COM 物件,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

這是一個純虛擬函數,必須在派生類中重寫。 框架呼叫它來實例化基礎 COM 轉換物件。

## <a name="cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a>CBase 轉換:取得結束關鍵幀

返回啟動關鍵幀。

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>傳回值

如果不應在關鍵幀之間插入過渡,則指向關鍵幀的有效指標或NULL。

### <a name="remarks"></a>備註

此方法可用於訪問以前由 SetKeyframe 設置的關鍵幀物件。 在將轉換添加到情節提要時,由頂級代碼調用它。

## <a name="cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a>CBase 轉換:取得相關變數

返回指向相關變數的指標。

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>傳回值

動畫變數尚未由 Set關聯變數設置動畫變數,則指向動畫變數的有效指標,或 NULL。

### <a name="remarks"></a>備註

這是相關動畫變數的訪問器。

## <a name="cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a>CBase 轉換:取得啟動關鍵畫面

返回啟動關鍵幀。

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>傳回值

如果過渡不應在關鍵幀之後啟動,則指向關鍵幀的有效指標或 NULL。

### <a name="remarks"></a>備註

此方法可用於訪問以前由 SetKeyframe 設置的關鍵幀物件。 在將轉換添加到情節提要時,由頂級代碼調用它。

## <a name="cbasetransitiongettransition"></a><a name="gettransition"></a>CBase 轉換:取得過渡

返回指向基礎 COM 過渡物件的指標。

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>參數

*p庫*<br/>
指向過渡庫的指標,該指標創建標準轉換。 對於自訂轉換,它可以為 NULL。

*pFactory*<br/>
指向轉換工廠的指標,該指標創建自定義轉換。 對於標準轉換,它可以為 NULL。

### <a name="return-value"></a>傳回值

如果無法建立基礎轉換,則指向 IUIAnimation 轉換或 NULL 的有效指標。

### <a name="remarks"></a>備註

此方法返回指向基礎 COM 過渡物件的指標,並在必要時創建它。

## <a name="cbasetransitiongettype"></a><a name="gettype"></a>CBase 轉換:抓取類型

返回轉換類型。

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>傳回值

TRANSITION_TYPE枚舉值之一。

### <a name="remarks"></a>備註

此方法可用於按其類型標識過渡物件。 類型在派生類中的構造函數中設置。

## <a name="cbasetransitionisadded"></a><a name="isadded"></a>CBase 轉換:已新增

告訴是否已將過渡添加到情節提要中。

```
BOOL IsAdded();
```

### <a name="return-value"></a>傳回值

如果過渡已添加到情節提要,則返回 TRUE,否則為 FALSE。

### <a name="remarks"></a>備註

當頂級代碼向情節提要添加轉換時,將在內部設置此標誌。

## <a name="cbasetransitionm_badded"></a><a name="m_badded"></a>CBase 轉換:m_bAdded

指定過渡是否已添加到情節提要。

```
BOOL m_bAdded;
```

## <a name="cbasetransitionm_pendkeyframe"></a><a name="m_pendkeyframe"></a>CBase 轉換:m_pEndKeyframe

存儲指向指定過渡結束的關鍵幀的指標。

```
CBaseKeyFrame* m_pEndKeyframe;
```

## <a name="cbasetransitionm_prelatedvariable"></a><a name="m_prelatedvariable"></a>CBase 轉換:m_pRelatedVariable

指向動畫變數的指標,該變數使用存儲在m_transition中的過渡進行動畫處理。

```
CAnimationVariable* m_pRelatedVariable;
```

## <a name="cbasetransitionm_pstartkeyframe"></a><a name="m_pstartkeyframe"></a>CBase 轉換:m_pStartKeyframe

存儲指向指定轉換開始的關鍵幀的指標。

```
CBaseKeyFrame* m_pStartKeyframe;
```

## <a name="cbasetransitionm_transition"></a><a name="m_transition"></a>CBase 轉換:m_transition

存儲指向 IUI 動畫轉換的指標。 如果未建立 COM 過渡物件,則為 NULL。

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

## <a name="cbasetransitionm_type"></a><a name="m_type"></a>CBase 轉換:m_type

存儲過渡類型。

```
TRANSITION_TYPE m_type;
```

## <a name="cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a>CBase 轉換::設定關鍵幀

為過渡設置關鍵幀。

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>參數

*p 開始*<br/>
指定轉換開頭的關鍵幀。

*pEnd*<br/>
指定過渡結束的關鍵幀。

### <a name="remarks"></a>備註

此方法告訴轉換在指定的關鍵幀之後開始,並且(可選地,如果 pEnd 不是 NULL)在指定的關鍵幀之前結束。 如果轉換是在指定持續時間參數下創建的,則該持續時間將覆蓋在開始和結束關鍵幀之間的持續時間。

## <a name="cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a>CBase 轉換::設定相關變數

在動畫變數和轉換之間建立關係。

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>參數

*pvariable*<br/>
指向相關動畫變數的指標。

### <a name="remarks"></a>備註

在動畫變數和轉換之間建立關係。 轉換只能應用於一個變數。

## <a name="cbasetransitiontransition_type-enumeration"></a><a name="transition_type_enumeration"></a>CBase 轉換::TRANSITION_TYPE枚舉

定義 Windows 動畫 API MFC 實現目前支援的過渡類型。

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>備註

在特定過渡的構造函數中設置過渡類型。 例如,CSinusoid轉換FromRange將其類型設置為SINUSOIDAL_FROM_RANGE。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
