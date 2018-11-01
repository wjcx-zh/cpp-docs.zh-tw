---
title: 選項, ATL 屬性頁精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: e891bd9e37bbf2fbedcdd71649305cdc366065fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642002"
---
# <a name="options-atl-property-page-wizard"></a>選項, ATL 屬性頁精靈

您可以使用精靈的這個頁面來定義您所建立的屬性頁的執行緒模型和彙總層級。

- **執行緒模型**

   指定的屬性頁所使用的執行緒模型。

   請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)如需詳細資訊。

   |選項|描述|
   |------------|-----------------|
   |**Single**|[屬性] 頁面只會在執行主要 COM 執行緒。|
   |**Apartment**|[屬性] 頁面可由任何單一執行緒 apartment 中。 預設值。|

- **彙總**

   新增您要建立的 [屬性] 頁面的彙總支援。 請參閱[彙總](../../atl/aggregation.md)如需詳細資訊。

   |選項|描述|
   |------------|-----------------|
   |**是**|建立可彙總的屬性頁。|
   |**No**|建立無法彙總的屬性頁。|
   |**只有**|建立只具現化彙總的屬性頁。|

## <a name="see-also"></a>另請參閱

[ATL 屬性頁精靈](../../atl/reference/atl-property-page-wizard.md)<br/>
[字串，ATL 屬性頁精靈](../../atl/reference/strings-atl-property-page-wizard.md)

