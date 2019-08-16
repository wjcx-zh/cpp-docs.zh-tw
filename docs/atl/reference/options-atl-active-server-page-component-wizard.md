---
title: 選項, ATL Active Server Page 元件精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.options
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
ms.openlocfilehash: c76ab7730256b007b66d54ca6753409926f7ae89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495306"
---
# <a name="options-atl-active-server-page-component-wizard"></a>選項, ATL Active Server Page 元件精靈

使用 [ATL Active Server Page Component Wizard] 的這個頁面來設計, 以提高物件的效率和錯誤支援。

如需有關 ATL 專案和 ATL COM 類別的詳細資訊，請參閱 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)。

- **執行緒模型**

   表示用於管理執行緒的方法。 根據預設, 專案會使用「**單元**執行緒」。

   如需詳細資訊，請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。

   |選項|描述|
   |------------|-----------------|
   |**Single**|指定物件使用單一線程模型。 在單一線程模型中, 物件一律會在主要 COM 執行緒中執行。 如需詳細資訊, 請參閱[單一執行緒的單元](/windows/win32/com/single-threaded-apartments)和[InprocServer32](/windows/win32/com/inprocserver32) 。|
   |**Apartment**|指定物件使用單元執行緒。 相當於單一線程單元。 在物件的生命週期內, 每個單元執行緒元件的每個物件都會被指派其執行緒的一個單元。不過, 多個執行緒可以用於多個物件。 每個公寓都會系結至特定的執行緒, 並具有 Windows 訊息提取 (預設值)。<br /><br /> 如需詳細資訊, 請參閱[單一執行緒單元](/windows/win32/com/single-threaded-apartments)。|
   |**既**|指定物件可以使用「單元」或「自由」執行緒, 視它所建立的執行緒類型而定。|
   |**受**|指定物件使用無限制執行緒。 自由執行緒相當於多執行緒單元模型。 如需詳細資訊, 請參閱[多執行緒單元](/windows/win32/com/multithreaded-apartments)。|
   |**Neutral**|指定物件遵循多執行緒單元的指導方針, 但可以在任何類型的執行緒上執行。|

- **彙總**

   指出物件是否使用[匯總](/windows/win32/com/aggregation)。 匯總物件會選擇要公開給用戶端的介面, 而介面的公開方式就如同匯總物件所實。 匯總物件的用戶端只會與 aggregate 物件通訊。

   |選項|描述|
   |------------|-----------------|
   |**是**|指定可以匯總物件。 預設值。|
   |**No**|指定不匯總物件。|
   |**Only**|指定必須匯總物件。|

- **支援**

   其他支援選項:

   |選項|說明|
   |------------|-----------------|
   |**ISupportErrorInfo**|建立適用於 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 介面的支援，以便讓物件將錯誤資訊傳回給用戶端。|
   |**連接點**|藉由讓物件的類別衍生自[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md), 為您的物件啟用連接點。|
   |**無限制執行緒封送處理器**|建立無限制執行緒封送處理器物件, 以便在相同進程中的執行緒之間有效率地封送處理介面指標。 可供物件**同時**指定或**Free**為執行緒模型。|

## <a name="see-also"></a>另請參閱

[ATL Active Server Page 元件精靈](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[ATL Active Server Page 元件](../../atl/reference/adding-an-atl-active-server-page-component.md)
