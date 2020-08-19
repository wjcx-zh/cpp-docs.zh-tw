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
ms.openlocfilehash: d4bdd1524f71bfba33e9090058fce26763a862bf
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561124"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage 類別

表示可以在 [色彩] 對話方塊中選取自訂色彩的屬性頁。

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
|`CMFCCustomColorsPropertyPage::GetThisClass`|由架構用來取得與這個類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件的指標。|
|[CMFCCustomColorsPropertyPage：： Setup](#setup)|設定屬性頁的色彩元件。|

### <a name="remarks"></a>備註

`CMFCColorDialog`類別會使用這個類別來顯示 [自訂色彩] 屬性頁。 如需的詳細資訊 `CMFCColorDialog` ，請參閱 [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="example"></a>範例

下列範例示範如何建立 `CMFCCustomColorsPropertyPage` 物件，並設定屬性頁的色彩元件。

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxcustomcolorspropertypage。h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a> CMFCCustomColorsPropertyPage：： Setup

設定屬性頁的色彩元件。

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>參數

*R*\
在RGB 值的紅色元件。

*G*\
在RGB 值的綠色元件。

*B*\
在RGB 值的藍色元件。

### <a name="remarks"></a>備註

這個方法會將目前的 RGB 和相關聯的 HLS (色調、亮度和飽和度) 屬性頁的色彩值。 當架構初始化 [色彩] 對話方塊或使用者按下滑鼠左鍵時， [CMFCColorDialog：： SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) 方法會呼叫這個方法。 如需的詳細資訊 `CMFCColorDialog` ，請參閱 [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage 類別](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
