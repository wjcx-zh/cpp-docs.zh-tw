---
title: CMFCImagePaintArea 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 449d79119b15e814485f3b7e0c3eb7472d314d19
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852473"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea 類別
提供您用來修改影像編輯器 對話方塊中的映像的 圖片 區域。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCImagePaintArea : public CButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|建構 `CMFCImagePaintArea` 物件。|  
|`CMFCImagePaintArea::~CMFCImagePaintArea`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCImagePaintArea::GetMode](#getmode)|擷取目前的繪製模式。|  
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|設定 [圖片] 區域的點陣圖影像。|  
|[CMFCImagePaintArea::SetColor](#setcolor)|設定目前的繪圖色彩。|  
|[CMFCImagePaintArea::SetMode](#setmode)|設定目前的繪製模式。|  
  
### <a name="remarks"></a>備註  
 這個類別不是直接從您的程式碼使用。  
  
 架構會使用這個類別中的影像編輯器 對話方塊中顯示圖片區域。 如需映像的 [編輯器] 對話方塊的詳細資訊，請參閱[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCImagePaintArea`類別中，將目前的繪圖的色彩，請將目前的繪製模式中，設定和設定點陣圖影像的圖片區域。  
  
 [!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afximagepaintarea.h  
  
##  <a name="cmfcimagepaintarea"></a>  CMFCImagePaintArea::CMFCImagePaintArea  
 建構 `CMFCImagePaintArea` 物件。  
  
```  
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*pParentDlg*|指標的對話方塊中，「 影像編輯器的父系。|  
  
##  <a name="getmode"></a>  CMFCImagePaintArea::GetMode  
 擷取目前的繪製模式。  
  
```  
IMAGE_EDIT_MODE GetMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值，指定目前的繪製模式。  
  
##  <a name="setbitmap"></a>  CMFCImagePaintArea::SetBitmap  
 設定 [圖片] 區域的點陣圖影像。  
  
```  
void SetBitmap(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*pBitmap*|要顯示新的點陣圖影像。|  
  
### <a name="remarks"></a>備註  
 如果*pBitmap*是 NULL，這個方法會設定可修改 [小畫家] 區域的大小為零。 否則，它會提供的點陣圖影像的大小設定可修改 [小畫家] 區域的大小。  
  
##  <a name="setcolor"></a>  CMFCImagePaintArea::SetColor  
 設定目前的繪圖色彩。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*色彩*|新繪圖的色彩。|  
  
### <a name="remarks"></a>備註  
 當您從映像編輯器調色盤列中選取色彩或色彩選擇器，架構會呼叫此方法來更新目前的繪圖色彩。 初始繪圖的色彩為黑色 （COLORREF 值為 0）。  
  
 將繪圖的色彩會使用影像編輯器對話方塊 IMAGE_EDIT_MODE_COLOR 除外的所有繪圖模式。 如需有關繪圖模式的詳細資訊，請參閱[cmfcimagepaintarea:: Image_edit_mode 列舉](cmfcimagepaintarea-image-edit-mode-enumeration.md)。  
  
##  <a name="setmode"></a>  CMFCImagePaintArea::SetMode  
 設定目前的繪製模式。  
  
```  
void SetMode(IMAGE_EDIT_MODE mode);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*模式*|[IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值，指定目前的繪製模式。|  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)
