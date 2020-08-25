---
title: CMFCImagePaintArea 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
ms.openlocfilehash: ee960b27651489ac1c196789d41a6c5ee396b260
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831147"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea 類別

提供您在 [影像編輯器] 對話方塊中用來修改影像的圖片區域。

## <a name="syntax"></a>語法

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|-|-|
|[CMFCImagePaintArea：： CMFCImagePaintArea](#cmfcimagepaintarea)|建構 `CMFCImagePaintArea` 物件。|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[CMFCImagePaintArea：： GetMode](#getmode)|抓取目前的繪圖模式。|
|[CMFCImagePaintArea：： SetBitmap](#setbitmap)|設定圖片區域的點陣圖影像。|
|[CMFCImagePaintArea：： SetColor](#setcolor)|設定目前的繪圖色彩。|
|[CMFCImagePaintArea：： SetMode](#setmode)|設定目前的繪圖模式。|

### <a name="remarks"></a>備註

這個類別並不適合直接從您的程式碼使用。

架構會使用這個類別，在 [影像編輯器] 對話方塊中顯示圖片區域。 如需 [影像編輯器] 對話方塊的詳細資訊，請參閱 [CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)。

## <a name="example"></a>範例

下列範例示範如何建立類別的物件 `CMFCImagePaintArea` 、設定目前的繪圖色彩、設定目前的繪圖模式，以及設定圖片區域的點陣圖影像。

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afximagepaintarea。h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a> CMFCImagePaintArea：： CMFCImagePaintArea

建構 `CMFCImagePaintArea` 物件。

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>參數

*pParentDlg*\
在對話方塊的指標，該對話方塊為影像編輯器的父系。

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a> CMFCImagePaintArea：： GetMode

抓取目前的繪圖模式。

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>傳回值

[IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值，這個值會指定目前的繪圖模式。

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a> CMFCImagePaintArea：： SetBitmap

設定圖片區域的點陣圖影像。

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>參數

*pBitmap*\
在要顯示的新點陣圖影像。

### <a name="remarks"></a>備註

如果 *pBitmap* 是 Null，這個方法會將可修改的繪製區域大小設定為零。 否則，它會將可修改的繪製區域大小設定為所提供點陣圖影像的大小。

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a> CMFCImagePaintArea：： SetColor

設定目前的繪圖色彩。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*\
在新的繪圖色彩。

### <a name="remarks"></a>備註

當您從影像編輯器選擇區列或色彩選擇器選取色彩時，架構會呼叫這個方法來更新目前的繪圖色彩。 初始繪圖色彩為黑色 (COLORRE光圈值為 0) 。

[影像編輯器] 對話方塊會針對所有繪圖模式使用繪圖色彩，但 IMAGE_EDIT_MODE_COLOR 除外。 如需繪製模式的詳細資訊，請參閱 [CMFCImagePaintArea：： IMAGE_EDIT_MODE 列舉](cmfcimagepaintarea-image-edit-mode-enumeration.md)。

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a> CMFCImagePaintArea：： SetMode

設定目前的繪圖模式。

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>參數

*模式*\
在 [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) 值，這個值會指定目前的繪圖模式。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)
