---
title: CD2DTextLayout 類別
ms.date: 03/27/2019
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
ms.openlocfilehash: 9be4c1134e2f82ceb3af31cbeb1a7d55f4071777
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369031"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout 類別

IDWriteTextLayout 的包裝器。

## <a name="syntax"></a>語法

```
class CD2DTextLayout : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D 文字佈局::CD2D文字佈局](#cd2dtextlayout)|構造 CD2DTextLayout 物件。|
|[CD2D 文字佈局::~CD2D文字佈局](#_dtorcd2dtextlayout)|解構函式。 銷毀 D2D 文字佈局物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2D 文字佈局::建立](#create)|建立 CD2D 文字佈局。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2D文字佈局::D](#destroy)|銷毀 CD2DTextLayout 物件。 (覆蓋[CD2D 資源::D)](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2D 文字佈局::取得](#get)|傳回 IDWrite 文字佈局介面|
|[CD2D 文字佈局::取得方特家族名稱](#getfontfamilyname)|在指定位置複製文本的字型族名稱。|
|[CD2D 文字佈局::取得本地化名稱](#getlocalename)|在指定位置取得文本的區域設定名稱。|
|[CD2D 文字佈局::有效](#isvalid)|檢查資源有效性(覆寫[CD2D 資源::有效](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2D 文字佈局::重新建立](#recreate)|重新建立 CD2D 文字佈局。 (覆寫[CD2D 資源:重新建立](../../mfc/reference/cd2dresource-class.md#recreate).)|
|[CD2D 文字佈局::設定字型家庭名稱](#setfontfamilyname)|指定文字範圍內的文字設定 null 連接字型家族名稱|
|[CD2D 文字佈局::設定本地化名稱](#setlocalename)|設定指定文字範圍內文字的區域設定名稱|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2D文字佈局::操作員 IDWriteTextLayout*](#operator_idwritetextlayout_star)|傳回 IDWrite 文字佈局介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2D文字佈局::m_pTextLayout](#m_ptextlayout)|指向 IDWriteTextLayout 的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

[CD2D 文字佈局](../../mfc/reference/cd2dtextlayout-class.md)

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="_dtorcd2dtextlayout"></a>CD2D 文字佈局::~CD2D文字佈局

解構函式。 銷毀 D2D 文字佈局物件時調用。

```
virtual ~CD2DTextLayout();
```

## <a name="cd2dtextlayoutcd2dtextlayout"></a><a name="cd2dtextlayout"></a>CD2D 文字佈局::CD2D文字佈局

構造 CD2DTextLayout 物件。

```
CD2DTextLayout(
    CRenderTarget* pParentTarget,
    const CString& strText,
    CD2DTextFormat& textFormat,
    const CD2DSizeF& sizeMax,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*斯特文字*<br/>
包含要從中創建新 CD2DTextLayout 物件的 CString 物件。

*textFormat*<br/>
包含要應用於字串的格式的 CString 物件。

*大小最大*<br/>
佈局框的大小。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dtextlayoutcreate"></a><a name="create"></a>CD2D 文字佈局::建立

建立 CD2D 文字佈局。

```
virtual HRESULT Create(CRenderTarget* */);
```

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dtextlayoutdestroy"></a><a name="destroy"></a>CD2D文字佈局::D

銷毀 CD2DTextLayout 物件。

```
virtual void Destroy();
```

## <a name="cd2dtextlayoutget"></a><a name="get"></a>CD2D 文字佈局::取得

傳回 IDWrite 文字佈局介面

```
IDWriteTextLayout* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 IDWriteTextLayout 介面或 NULL 的指標。

## <a name="cd2dtextlayoutgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2D 文字佈局::取得方特家族名稱

在指定位置複製文本的字型族名稱。

```
CString GetFontFamilyName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>參數

*電流位置*<br/>
要檢查的文本的位置。

*文字範圍*<br/>
與目前位置指定位置的文本具有相同格式的文本範圍。 這意味著運行具有指定位置的精確格式,包括但不限於字體族名。

### <a name="return-value"></a>傳回值

包含當前字體族名的 CString 物件。

## <a name="cd2dtextlayoutgetlocalename"></a><a name="getlocalename"></a>CD2D 文字佈局::取得本地化名稱

在指定位置取得文本的區域設定名稱。

```
CString GetLocaleName(
    UINT32 currentPosition,
    DWRITE_TEXT_RANGE* textRange = NULL) const;
```

### <a name="parameters"></a>參數

*電流位置*<br/>
要檢查的文本的位置。

*文字範圍*<br/>
與目前位置指定位置的文本具有相同格式的文本範圍。 這意味著運行具有指定位置的精確格式,包括但不限於區域設置名稱。

### <a name="return-value"></a>傳回值

包含當前區域設置名稱的 CString 物件。

## <a name="cd2dtextlayoutisvalid"></a><a name="isvalid"></a>CD2D 文字佈局::有效

檢查資源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源有效,則為 TRUE;否則 FALSE。

## <a name="cd2dtextlayoutm_ptextlayout"></a><a name="m_ptextlayout"></a>CD2D文字佈局::m_pTextLayout

指向 IDWriteTextLayout 的指標。

```
IDWriteTextLayout* m_pTextLayout;
```

## <a name="cd2dtextlayoutoperator-idwritetextlayout"></a><a name="operator_idwritetextlayout_star"></a>CD2D文字佈局::操作員 IDWriteTextLayout*

傳回 IDWrite 文字佈局介面

```
operator IDWriteTextLayout*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 IDWriteTextLayout 介面或 NULL 的指標。

## <a name="cd2dtextlayoutrecreate"></a><a name="recreate"></a>CD2D 文字佈局::重新建立

重新建立 CD2D 文字佈局。

```
virtual HRESULT ReCreate(CRenderTarget* */);
```

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dtextlayoutsetfontfamilyname"></a><a name="setfontfamilyname"></a>CD2D 文字佈局::設定字型家庭名稱

指定文字範圍內的文字設定 null 連接字型家族名稱

```
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>參數

*pwzFont 家族名稱*<br/>
套用文字Range 指定範圍內的整個文字字串的字型族名稱

*文字範圍*<br/>
此變更套用的文字範圍

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE

## <a name="cd2dtextlayoutsetlocalename"></a><a name="setlocalename"></a>CD2D 文字佈局::設定本地化名稱

設定指定文字範圍內文字的區域設定名稱

```
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,
    DWRITE_TEXT_RANGE textRange);
```

### <a name="parameters"></a>參數

*pwzLocale名稱*<br/>
空終止區域設定名稱字串

*文字範圍*<br/>
此變更套用的文字範圍

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
