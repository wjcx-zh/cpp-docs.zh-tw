---
title: CMFC 影像繪製區域類別
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
ms.openlocfilehash: cd74d2418bb874553fbbafa637f527a7b84b73bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754275"
---
# <a name="cmfcimagepaintarea-class"></a>CMFC 影像繪製區域類別

提供用於修改圖像編輯器對話框中圖像的圖片區域。

## <a name="syntax"></a>語法

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFC 影像繪製區域:CMFC 影像繪製區域](#cmfcimagepaintarea)|建構 `CMFCImagePaintArea` 物件。|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFC 影像繪製區域:取得模式](#getmode)|檢索當前繪圖模式。|
|[CMFC 影像繪製區域::設定點陣圖](#setbitmap)|設置圖片區域的點陣圖圖像。|
|[CMFC 影像繪製區域:設定顏色](#setcolor)|設置當前繪圖顏色。|
|[CMFC 影像繪製區域:設定模式](#setmode)|設置當前繪圖模式。|

### <a name="remarks"></a>備註

這個類別並不適合直接從您的程式碼使用。

框架使用此類在圖像編輯器對話框中顯示圖片區域。 有關影像編輯器對話框的詳細資訊,請參閱[CMFCImage 編輯器對話類](../../mfc/reference/cmfcimageeditordialog-class.md)。

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCImagePaintArea`類的物件、設置當前繪圖顏色、設置當前繪圖模式以及設置圖片區域的點陣圖影像。

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFC 影像繪製區域](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>需求

**標題:** afximagepaint 區域.h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a>CMFC 影像繪製區域:CMFC 影像繪製區域

建構 `CMFCImagePaintArea` 物件。

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*p 家長Dlg*|[在]指向作為圖像編輯器父級的對話框的指標。|

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a>CMFC 影像繪製區域:取得模式

檢索當前繪圖模式。

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>傳回值

指定目前繪圖模式[的IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值。

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a>CMFC 影像繪製區域::設定點陣圖

設置圖片區域的點陣圖圖像。

```cpp
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pBitmap*|[在]要顯示的新點陣圖圖像。|

### <a name="remarks"></a>備註

如果*pBitmap*為 NULL,則此方法將可修改的繪製區域的大小設置為零。 否則,它將可修改的繪製區域的大小設置為提供的位圖圖像的大小。

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a>CMFC 影像繪製區域:設定顏色

設置當前繪圖顏色。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*顏色*|[在]新的繪圖顏色。|

### <a name="remarks"></a>備註

當您從影像編輯器調色板列或顏色選取器中選擇顏色時,框架將調用此方法以更新當前繪圖顏色。 初始繪圖顏色為黑色(COLORREF 值為 0)。

除IMAGE_EDIT_MODE_COLOR外,圖像編輯器對話框對所有繪圖模式都使用繪圖顏色。 有關繪圖模式的詳細資訊,請參閱[CMFCImagePaint 區域::IMAGE_EDIT_MODE枚舉](cmfcimagepaintarea-image-edit-mode-enumeration.md)。

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a>CMFC 影像繪製區域:設定模式

設置當前繪圖模式。

```cpp
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*模式*|[在]指定目前繪圖模式[的IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值。|

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)
