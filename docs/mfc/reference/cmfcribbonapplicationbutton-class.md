---
title: CMFCRibbonApplicationButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
ms.openlocfilehash: d1dc8ef6e801623aa96cb4b47936413cd17f24f0
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821249"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton 類別

實作位於應用程式視窗左上角的特殊按鈕。 按一下按鈕時，按鈕會開啟通常包含一般 [ **檔案** ] 命令 (例如 [ **開啟**]、[ **儲存**] 和 [ **結束**]) 的功能表。

## <a name="syntax"></a>語法

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|建構並初始化 `CMFCRibbonApplicationButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonApplicationButton::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCRibbonApplicationButton::SetImage](#setimage)|將影像指派給 [功能區應用程式] 按鈕。|

## <a name="example"></a>範例

下例示範如何在 `CMFCRibbonApplicationButton` 類別中使用各種方法。 此範例示範如何將影像指派給應用程式按鈕, 以及如何設定其工具提示。 這段程式碼片段是 [Draw 用戶端範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>需求

**標頭:** afxribbonbar.h。h

##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

建立[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)物件的結構並加以初始化。

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>參數

*uiBmpResID*<br/>
要在應用程式按鈕上顯示之影像的資源識別碼。

*hBmp*<br/>
要在應用程式按鈕上顯示之點陣圖的控制碼。

### <a name="remarks"></a>備註

[功能區應用程式] 按鈕是位於應用程式視窗左上角的特殊按鈕。 當使用者按一下此按鈕時, 應用程式會開啟一個功能表, 其中通常包含一般檔案命令, 例如**開啟**、**儲存**和結束。

##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage

將影像指派給應用程式按鈕。

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>參數

*uiBmpResID*<br/>
在要在應用程式按鈕上顯示之影像的資源識別碼。

*hBmp*<br/>
在要在應用程式按鈕上顯示之點陣圖的控制碼。

### <a name="remarks"></a>備註

您可以使用這個方法, 在建立按鈕之後, 將新的影像指派給 [功能區應用程式] 按鈕。 [應用程式] 按鈕位於應用程式視窗的左上角。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)
