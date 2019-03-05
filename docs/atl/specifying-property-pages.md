---
title: 指定屬性頁 (ATL)
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPages
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
ms.openlocfilehash: d738759dfba50f26b788ee1b0761baf8bc4b00ab
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287123"
---
# <a name="specifying-property-pages"></a>指定屬性頁

當您建立 ActiveX 控制項時，您通常要關聯可用來設定您的控制項屬性的屬性頁。 控制容器使用`ISpecifyPropertyPages`介面，以了解哪些屬性頁面可以用來設定您的控制項屬性。 您必須在您的控制項上實作這個介面。

若要實作`ISpecifyPropertyPages`使用 ATL，採取下列步驟：

1. 衍生您的類別，從[ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)。

1. 新增項目`ISpecifyPropertyPages`類別的 COM 對應。

1. 新增[PROP_PAGE](reference/property-map-macros.md#prop_page)每個頁面與您的控制項相關聯的屬性對應的項目。

> [!NOTE]
> 產生標準控制項使用時[ATL 控制項精靈](../atl/reference/atl-control-wizard.md)，您只需要將 PROP_PAGE 項目加入至屬性對應。 精靈會產生必要的程式碼，如需其他步驟。

正常運作的容器會顯示指定的屬性頁中 PROP_PAGE 中的項目屬性對應的順序相同。 一般而言，您應該放置標準屬性頁面項目之後的項目屬性對應，在自訂頁面，讓使用者看到專屬於您控制的頁面第一次。

## <a name="example"></a>範例

下列類別日曆控制項會使用`ISpecifyPropertyPages`介面，以判斷可以使用自訂日期頁面和 [內建的色彩] 頁面來設定其屬性的容器。

[!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]

## <a name="see-also"></a>另請參閱

[屬性頁](../atl/atl-com-property-pages.md)<br/>
[ATLPages 範例](../visual-cpp-samples.md)
