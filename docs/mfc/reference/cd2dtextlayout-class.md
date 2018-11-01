---
title: CD2DTextLayout 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
ms.openlocfilehash: 378c96622144a4acac27785cef844f0c1d21b98b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630941"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout 類別

IDWriteTextLayout 包裝函式。

## <a name="syntax"></a>語法

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|建構 CD2DTextLayout 物件。|
|[CD2DTextLayout:: ~ CD2DTextLayout](#cd2dtextlayout__~cd2dtextlayout)|解構函式。 D2D 文字版面配置物件正在被終結時呼叫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DTextLayout::Create](#create)|建立 CD2DTextLayout。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|
|[CD2DTextLayout::Destroy](#destroy)|終結 CD2DTextLayout 物件。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|
|[CD2DTextLayout::Get](#get)|傳回 IDWriteTextLayout 介面|
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|複製指定位置處之文字的字型家族名稱。|
|[CD2DTextLayout::GetLocaleName](#getlocalename)|取得位於指定位置的地區設定名稱的文字。|
|[CD2DTextLayout::IsValid](#isvalid)|檢查資源的有效性 (會覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2DTextLayout::ReCreate](#recreate)|CD2DTextLayout 會重新建立。 (覆寫[CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate)。)|
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|設定 null 終止的字型家族名稱中指定的文字範圍的文字|
|[CD2DTextLayout::SetLocaleName](#setlocalename)|設定指定的文字範圍內文字的地區設定名稱|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DTextLayout::operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|傳回 IDWriteTextLayout 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|IDWriteTextLayout 指標。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="_dtorcd2dtextlayout"></a>  CD2DTextLayout:: ~ CD2DTextLayout

解構函式。 D2D 文字版面配置物件正在被終結時呼叫。

```
virtual ~CD2DTextLayout();
```

##  <a name="cd2dtextlayout"></a>  CD2DTextLayout::CD2DTextLayout

建構 CD2DTextLayout 物件。

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*pParentTarget*<br/>
到轉譯目標的指標。

*先把 strText*<br/>
CString 物件，其中包含要建立的新 CD2DTextLayout 物件的字串。

*TextFormat*<br/>
CString 物件，其中包含要套用至字串的格式。

*sizeMax*<br/>
[配置] 方塊的大小。

*bAutoDestroy*<br/>
表示擁有者 (pParentTarget) 將會終結物件。

##  <a name="create"></a>  CD2DTextLayout::Create

建立 CD2DTextLayout。

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="destroy"></a>  CD2DTextLayout::Destroy

終結 CD2DTextLayout 物件。

```
virtual void Destroy();
```

##  <a name="get"></a>  CD2DTextLayout::Get

傳回 IDWriteTextLayout 介面

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 IDWriteTextLayout 介面的指標。

##  <a name="getfontfamilyname"></a>  CD2DTextLayout::GetFontFamilyName

複製指定位置處之文字的字型家族名稱。

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>參數

*currentPosition*<br/>
若要檢查文字的位置。

*TextRange*<br/>
具有相同的文字範圍格式化為文字在 currentPosition 所指定的位置。 這表示執行結果為確切的格式為指定的位置，包括但不是限於字型家族名稱。

### <a name="return-value"></a>傳回值

CString 物件，包含目前的字型家族名稱。

##  <a name="getlocalename"></a>  CD2DTextLayout::GetLocaleName

取得位於指定位置的地區設定名稱的文字。

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>參數

*currentPosition*<br/>
要檢查的文字位置。

*TextRange*<br/>
具有相同的文字範圍格式化為文字在 currentPosition 所指定的位置。 這表示執行結果為確切的格式為指定的位置，包括但不是限於的地區設定名稱。

### <a name="return-value"></a>傳回值

CString 物件，包含目前的地區設定名稱。

##  <a name="isvalid"></a>  CD2DTextLayout::IsValid

檢查資源的有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源無效，則為 TRUE否則為 FALSE。

##  <a name="m_ptextlayout"></a>  CD2DTextLayout::m_pTextLayout

IDWriteTextLayout 指標。

```
IDWriteTextLayout* m_pTextLayout;
```

##  <a name="operator_idwritetextlayout_star"></a>  CD2DTextLayout::operator IDWriteTextLayout *

傳回 IDWriteTextLayout 介面

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 IDWriteTextLayout 介面的指標。

##  <a name="recreate"></a>  CD2DTextLayout::ReCreate

CD2DTextLayout 會重新建立。

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。

##  <a name="setfontfamilyname"></a>  CD2DTextLayout::SetFontFamilyName

設定 null 終止的字型家族名稱中指定的文字範圍的文字

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>參數

*pwzFontFamilyName*<br/>
適用於整個文字字串出現在 textRange 所指定之範圍的字型系列名稱

*TextRange*<br/>
要套用這項變更的文字範圍

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE

##  <a name="setlocalename"></a>  CD2DTextLayout::SetLocaleName

設定指定的文字範圍內文字的地區設定名稱

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>參數

*pwzLocaleName*<br/>
以 null 結尾的地區設定名稱字串

*TextRange*<br/>
要套用這項變更的文字範圍

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
