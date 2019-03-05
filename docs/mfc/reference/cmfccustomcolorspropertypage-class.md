---
title: CMFCCustomColorsPropertyPage 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: b28711991835dd14929e5387709046c3867c715e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299878"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage 類別

表示屬性頁，可以在 [色彩] 對話方塊中選取自訂色彩。

## <a name="syntax"></a>語法

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|`CMFCCustomColorsPropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCCustomColorsPropertyPage::Setup](#setup)|設定色彩元件的屬性頁。|

### <a name="remarks"></a>備註

`CMFCColorDialog`類別會使用這個類別來顯示 [自訂色彩] 屬性頁。 如需詳細資訊`CMFCColorDialog`，請參閱 < [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="example"></a>範例

下列範例示範如何建構`CMFCCustomColorsPropertyPage`物件，並設定 [屬性] 頁面的色彩元件。

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>需求

**標頭：** afxcustomcolorspropertypage.h

##  <a name="setup"></a>  CMFCCustomColorsPropertyPage::Setup

設定色彩元件的屬性頁。

```
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*R*|[in]紅色的 RGB 值的元件。|
|*G*|[in]綠色的 RGB 值的元件。|
|*B*|[in]RGB 值的藍色元件。|

### <a name="remarks"></a>備註

這個方法會更新目前的 RGB 和關聯的 HLS （色調、 亮度和飽和度） 色彩值的屬性頁。 [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo)架構初始化 [色彩] 對話方塊中，或使用者按下滑鼠左的按鈕時，方法會呼叫這個方法。 如需詳細資訊`CMFCColorDialog`，請參閱 < [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage 類別](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
