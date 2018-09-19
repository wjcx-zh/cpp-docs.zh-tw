---
title: 選項，ATL Active Server Page 元件精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fda466ad45b5b91f02920d68eef8eab071010830
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020130"
---
# <a name="options-atl-active-server-page-component-wizard"></a>選項, ATL Active Server Page 元件精靈

使用 ATL Active Server Page 元件精靈的這個頁面來設計以提升的效率及物件的錯誤支援。

如需有關 ATL 專案和 ATL COM 類別的詳細資訊，請參閱[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)。

- **執行緒模型**

   表示用於管理執行緒的方法。 根據預設，專案會使用**Apartment**執行緒。

   請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)如需詳細資訊。

   |選項|描述|
   |------------|-----------------|
   |**Single**|指定的物件會使用單一執行緒模型。 在單一執行緒模型中，一律在主要 COM 執行緒執行 物件。 請參閱[單一執行緒 Apartment](/windows/desktop/com/single-threaded-apartments)並[InprocServer32](/windows/desktop/com/inprocserver32)如需詳細資訊。|
   |**Apartment**|指定物件使用 apartment 執行緒。 相當於單一執行緒 apartment。 Apartment 執行緒的元件的每個物件會指派其物件的存留期間的執行緒 apartment不過，多個執行緒可以用於多個物件。 每個 apartment 會繫結至特定的執行緒，並有 Windows 訊息幫浦 （預設值）。<br /><br /> 請參閱[單一執行緒 Apartment](/windows/desktop/com/single-threaded-apartments)如需詳細資訊。|
   |**兩者**|指定的物件可以使用 apartment 或無限制執行緒，從建立的執行緒種類而定。|
   |**免費**|指定的物件，使用無限制執行緒。 無限制執行緒相當於多執行緒 apartment 模型。 請參閱[多執行緒的 Apartment](/windows/desktop/com/multithreaded-apartments)如需詳細資訊。|
   |**Neutral**|指定物件採用多執行緒的 apartment 的方針，但它可以在任何種類的執行緒上執行。|

- **彙總**

   指出物件是否使用[彙總](/windows/desktop/com/aggregation)。 彙總的物件可讓您選擇的介面來公開 （expose） 給用戶端，並如同彙總的物件實作它們所公開的介面。 彙總物件的用戶端通訊只能搭配彙總的物件。

   |選項|描述|
   |------------|-----------------|
   |**是**|指定可以彙總物件。 預設值。|
   |**No**|指定的物件不會彙總。|
   |**只有**|指定必須彙總物件。|

- **支援**

   其他支援選項：

   |選項|描述|
   |------------|-----------------|
   |**ISupportErrorInfo**|建立支援[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)介面讓物件可以將錯誤資訊傳回給用戶端。|
   |**連接點**|藉由衍生自物件的類別讓您為物件的連接點[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。|
   |**無限制執行緒封送處理器**|建立無限制執行緒封送處理器物件，以有效率地在相同的程序中執行緒之間的封送處理介面指標。 指定的物件可供**兩者**或**免費**為執行緒模型。|

## <a name="see-also"></a>另請參閱

[ATL Active Server Page 元件精靈](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[ATL Active Server Page 元件](../../atl/reference/adding-an-atl-active-server-page-component.md)

