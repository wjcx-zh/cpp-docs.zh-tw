---
title: CD2DTextFormat 類別
ms.date: 03/27/2019
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
ms.openlocfilehash: f7310fd3ca2ac34df7cc1a99cd5527ea8ba709c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369039"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat 類別

IDWriteText格式的包裝。

## <a name="syntax"></a>語法

```
class CD2DTextFormat : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D 文字格式:CD2D文字格式](#cd2dtextformat)|建構 CD2DText 格式物件。|
|[CD2D 文字格式:*CD2D文字格式](#_dtorcd2dtextformat)|解構函式。 銷毀 D2D 文字格式物件時呼叫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2D 文字格式:建立](#create)|建立 CD2D 文字格式。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2D 文字格式::D](#destroy)|銷毀 CD2DText 格式物件。 (覆蓋[CD2D 資源::D)](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2D 文字格式:取得](#get)|傳回 IDWriteText 格式介面|
|[CD2D 文字格式::取得方特家庭名稱](#getfontfamilyname)|獲取字體姓氏的副本。|
|[CD2D 文字格式:抓取本地化名稱](#getlocalename)|獲取區域設置名稱的副本。|
|[CD2D 文字格式::有效](#isvalid)|檢查資源有效性(覆寫[CD2D 資源::有效](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2D 文字格式:重新建立](#recreate)|重新建立 CD2D 文字格式。 (覆寫[CD2D 資源:重新建立](../../mfc/reference/cd2dresource-class.md#recreate).)|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2D 文字格式::操作員 IDWriteText 格式*](#operator_idwritetextformat_star)|傳回 IDWriteText 格式介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2D文字格式::m_pTextFormat](#m_ptextformat)|指向 IDWriteText 格式的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

[CD2D 文字格式](../../mfc/reference/cd2dtextformat-class.md)

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a>CD2D 文字格式:*CD2D文字格式

解構函式。 銷毀 D2D 文字格式物件時呼叫。

```
virtual ~CD2DTextFormat();
```

## <a name="cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a>CD2D 文字格式:CD2D文字格式

建構 CD2DText 格式物件。

```
CD2DTextFormat(
    CRenderTarget* pParentTarget,
    const CString& strFontFamilyName,
    FLOAT fontSize,
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,
    const CString& strFontLocale = _T(""),
    IDWriteFontCollection* pFontCollection = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*斯特方特家族名稱*<br/>
包含字體系列名稱的 CString 物件。

*字型大小*<br/>
以 DIP("與設備無關的圖元")為單位的字體的邏輯大小。 DIP 等於1/96英寸。

*字體重量*<br/>
指示文本物件的字體粗細的值。

*字型樣式*<br/>
指示文本物件的字體樣式的值。

*字型拉伸*<br/>
指示文本物件的字體拉伸的值。

*斯特方特拉茲*<br/>
包含區域設置名稱的 CString 物件。

*pFontCollection*<br/>
指向字體集合物件的指標。 當為 NULL 時,指示系統字體收集。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dtextformatcreate"></a><a name="create"></a>CD2D 文字格式:建立

建立 CD2D 文字格式。

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dtextformatdestroy"></a><a name="destroy"></a>CD2D 文字格式::D

銷毀 CD2DText 格式物件。

```
virtual void Destroy();
```

## <a name="cd2dtextformatget"></a><a name="get"></a>CD2D 文字格式:取得

傳回 IDWriteText 格式介面

```
IDWriteTextFormat* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 IDWriteTextFormat 介面或 NULL 的指標。

## <a name="cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2D 文字格式::取得方特家庭名稱

獲取字體姓氏的副本。

```
CString GetFontFamilyName() const;
```

### <a name="return-value"></a>傳回值

包含當前字體族名的 CString 物件。

## <a name="cd2dtextformatgetlocalename"></a><a name="getlocalename"></a>CD2D 文字格式:抓取本地化名稱

獲取區域設置名稱的副本。

```
CString GetLocaleName() const;
```

### <a name="return-value"></a>傳回值

包含當前區域設置名稱的 CString 物件。

## <a name="cd2dtextformatisvalid"></a><a name="isvalid"></a>CD2D 文字格式::有效

檢查資源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源有效,則為 TRUE;否則 FALSE。

## <a name="cd2dtextformatm_ptextformat"></a><a name="m_ptextformat"></a>CD2D文字格式::m_pTextFormat

指向 IDWriteText 格式的指標。

```
IDWriteTextFormat* m_pTextFormat;
```

## <a name="cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a>CD2D 文字格式::操作員 IDWriteText 格式*

傳回 IDWriteText 格式介面

```
operator IDWriteTextFormat*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 IDWriteTextFormat 介面或 NULL 的指標。

## <a name="cd2dtextformatrecreate"></a><a name="recreate"></a>CD2D 文字格式:重新建立

重新建立 CD2D 文字格式。

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
