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
ms.openlocfilehash: 0debd40825990b647cd5b1df9a144e3abd450de3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361612"
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
|[CMFC功能化應用按鈕::CMFC功能化應用按鈕](#cmfcribbonapplicationbutton)|建構並初始化 `CMFCRibbonApplicationButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonApplicationButton::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFC功能化應用按鈕::設定影像](#setimage)|將圖像分配給功能區應用程式按鈕。|

## <a name="example"></a>範例

下例示範如何在 `CMFCRibbonApplicationButton` 類別中使用各種方法。 該示例演示如何將圖像分配給應用程式按鈕,以及如何設置其工具提示。 這段程式碼片段是 [Draw 用戶端範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxRibbonBar.h

## <a name="cmfcribbonapplicationbuttoncmfcribbonapplicationbutton"></a><a name="cmfcribbonapplicationbutton"></a>CMFC功能化應用按鈕::CMFC功能化應用按鈕

建構並初始化[CMFC 功能應用程式按鈕](../../mfc/reference/cmfcribbonapplicationbutton-class.md)物件。

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>參數

*烏布佈雷斯ID*<br/>
要在應用程式按鈕上顯示的圖像的資源 ID。

*hBmp*<br/>
要顯示在應用程式按鈕上的點陣圖的句柄。

### <a name="remarks"></a>備註

功能區應用程式按鈕是位於應用程式視窗左上角的特殊按鈕。 當使用者按下此按鈕時,應用程式將開啟一個選單,該選單通常包含常見的**檔案**命令,如**開啟**、**儲存**與**離開**。

## <a name="cmfcribbonapplicationbuttonsetimage"></a><a name="setimage"></a>CMFC功能化應用按鈕::設定影像

將圖像分配給應用程式按鈕。

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>參數

*烏布佈雷斯ID*<br/>
[在]要在應用程式按鈕上顯示的圖像的資源 ID。

*hBmp*<br/>
[在]要顯示在應用程式按鈕上的點陣圖的句柄。

### <a name="remarks"></a>備註

使用此方法在創建按鈕后將新映射分配給功能區應用程式按鈕。 應用程式按鈕位於應用程式視窗的左上角。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)
