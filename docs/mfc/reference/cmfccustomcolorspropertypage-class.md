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
ms.openlocfilehash: 468d947947fc89f9ebc832cda722d854bb8b4be2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752471"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage 類別

表示可在顏色對話框中選擇自定義顏色的屬性頁。

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
|`CMFCCustomColorsPropertyPage::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFC自訂顏色屬性頁::設定](#setup)|設定屬性頁的顏色元件。|

### <a name="remarks"></a>備註

類`CMFCColorDialog`使用此類來顯示自定義顏色屬性頁。 有關 的詳細`CMFCColorDialog`資訊 ,請參閱[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCCustomColorsPropertyPage`物件並設置屬性頁的顏色元件。

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFC自訂顏色屬性頁](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>需求

**標題:** afx自訂顏色屬性頁.h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a>CMFC自訂顏色屬性頁::設定

設定屬性頁的顏色元件。

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*R*|[在]RGB 值的紅色元件。|
|*G*|[在]RGB 值的綠色元件。|
|*B*|[在]RGB 值的藍色元件。|

### <a name="remarks"></a>備註

此方法更新屬性頁的當前 RGB 和關聯的 HLS(色調、光度和飽和度)顏色值。 當框架初始化顏色對話方塊或使用者按下滑鼠左鍵時[,CMFCColorDialog:setPageTWO](../../mfc/reference/cmfccolordialog-class.md#setpagetwo)方法調用此方法。 有關 的詳細`CMFCColorDialog`資訊 ,請參閱[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage 類別](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
