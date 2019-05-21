---
title: 選項, ATL 屬性頁精靈
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: c883b3e79bd857bb457da0a1bd540a08ddddf017
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524547"
---
# <a name="options-atl-property-page-wizard"></a>選項, ATL 屬性頁精靈


::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL 屬性頁精靈。

::: moniker-end

::: moniker range="vs-2017"

使用精靈的這個頁面來定義您所建立之屬性頁的執行緒模型和彙總層級。

- **執行緒模型**

   指定屬性頁所使用的執行緒模型。

   如需詳細資訊，請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。

   |選項|說明|
   |------------|-----------------|
   |**Single**|屬性頁只會在主要 COM 執行緒中執行。|
   |**Apartment**|屬性頁可以在任何單一 Apartment 執行緒中建立。 預設值。|

- **彙總**

   增加對您要建立之屬性頁的彙總支援。 如需詳細資訊，請參閱 [Aggregation](../../atl/aggregation.md)。

   |選項|說明|
   |------------|-----------------|
   |**是**|建立可以彙總的屬性頁。|
   |**No**|建立無法彙總的屬性頁。|
   |**Only**|建立僅能透過彙總具現化的屬性頁。|

::: moniker-end

## <a name="see-also"></a>另請參閱

[ATL 屬性頁精靈](../../atl/reference/atl-property-page-wizard.md)<br/>
[字串, ATL 屬性頁精靈](../../atl/reference/strings-atl-property-page-wizard.md)
