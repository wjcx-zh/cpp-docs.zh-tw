---
title: CMFCStandardColorsPropertyPage 類別
ms.date: 11/04/2016
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
ms.openlocfilehash: c57715171816e83cd1e04872d88b452b51b39388
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843946"
---
# <a name="cmfcstandardcolorspropertypage-class"></a>CMFCStandardColorsPropertyPage 類別

表示使用者用來選取 [色彩] 對話方塊中之標準色彩的屬性頁。

## <a name="syntax"></a>語法

```
class CMFCStandardColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|-|-|
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|`CMFCStandardColorsPropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCStandardColorsPropertyPage::GetThisClass`|由架構用來取得與這個類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件的指標。|

### <a name="remarks"></a>備註

`CMFCColorDialog`類別會使用這個類別來顯示標準色彩屬性頁。 如需的詳細資訊 `CMFCColorDialog` ，請參閱 [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxstandardcolorspropertypage。h

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCCustomColorsPropertyPage 類別](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
