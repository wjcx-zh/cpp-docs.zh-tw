---
title: CMFCRibbonContextCaption 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetColor
- AFXRIBBONBAR/CMFCRibbonContextCaption::GetRightTabX
helpviewer_keywords:
- CMFCRibbonContextCaption [MFC], GetColor
- CMFCRibbonContextCaption [MFC], GetRightTabX
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
ms.openlocfilehash: 7aacbe23684914c91129d9962ae847d442cc411b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375211"
---
# <a name="cmfcribboncontextcaption-class"></a>CMFCRibbonContextCaption 類別

實作出現在功能區類別或內容類別頂端的彩色標題。

## <a name="syntax"></a>語法

```
class CMFCRibbonContextCaption : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCRibbonContextCaption::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCRibbonContextCaption::GetColor](#getcolor)|傳回標題的色彩。|
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||
|`CMFCRibbonContextCaption::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|

## <a name="remarks"></a>備註

此類別無法直接具現化。 [CMFCRibbonBar 類](../../mfc/reference/cmfcribbonbar-class.md)在內部使用此類向功能區類別添加顏色。

要設定功能區類別的顏色,請致電[CMFC 功能區類別::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)。 要設定內容內容的顏色,請致電[CMFC 功能區列::新增上下文類別](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)

## <a name="requirements"></a>需求

**標題:** afxRibbonBar.h

## <a name="cmfcribboncontextcaptiongetcolor"></a><a name="getcolor"></a>CMFC功能相關標題:取得顏色

返回標題的背景顏色。

```
AFX_RibbonCategoryColor GetColor() const;
```

### <a name="return-value"></a>傳回值

傳回的值可以是以下枚舉值之一:

- `AFX_CategoryColor_None`

- `AFX_CategoryColor_Red`

- `AFX_CategoryColor_Orange`

- `AFX_CategoryColor_Yellow`

- `AFX_CategoryColor_Green`

- `AFX_CategoryColor_Blue`

- `AFX_CategoryColor_Indigo`

- `AFX_CategoryColor_Violet`

### <a name="remarks"></a>備註

標題的顏色可以通過調用[CMFC 功能分類::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)或[CMFC 功能列::添加上下文類別](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)來設置。

## <a name="cmfcribboncontextcaptiongetrighttabx"></a><a name="getrighttabx"></a>CMFC功能相關標題:取得正確的TabX

檢索類別功能區選項卡右側邊緣的位置。

```
int GetRightTabX() const;
```

### <a name="return-value"></a>傳回值

傳`CMFCRibbonCategory`回 物件功能區選項卡的封閉矩形的右側 X 值,如果選項卡被截斷,則返回 -1 的值。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonCategory 類別](../../mfc/reference/cmfcribboncategory-class.md)<br/>
[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
