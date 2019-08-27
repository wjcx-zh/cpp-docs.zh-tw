---
title: 選項, ATL 簡單物件精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.options
helpviewer_keywords:
- ATL Simple Object Wizard, options
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
ms.openlocfilehash: e92f4909907645fc317590fbcc3601887346c642
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495163"
---
# <a name="options-atl-simple-object-wizard"></a>選項, ATL 簡單物件精靈

使用 [ATL 簡單物件 Wizard] 的這個頁面來設計, 以提高物件的效率和錯誤支援。

如需有關 ATL 專案和 ATL COM 類別的詳細資訊，請參閱 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)。

- **執行緒模型**

   表示用於管理執行緒的方法。 根據預設, 專案會使用「**單元**執行緒」。

   如需詳細資訊，請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。

   |選項|描述|
   |------------|-----------------|
   |**Single**|指定物件一律在主要 COM 執行緒中執行。 如需詳細資訊, 請參閱[單一執行緒的單元](/windows/win32/com/single-threaded-apartments)和[InprocServer32](/windows/win32/com/inprocserver32) 。|
   |**Apartment**|指定物件使用單元執行緒。 相當於單一線程單元。 在物件的生命週期內, 每個單元執行緒元件的每個物件都會被指派其執行緒的一個單元。不過, 多個執行緒可以用於多個物件。 每個公寓都會系結至特定的執行緒, 並具有 Windows 訊息提取 (預設值)。<br /><br /> 如需詳細資訊, 請參閱[單一執行緒單元](/windows/win32/com/single-threaded-apartments)。|
   |**既**|指定物件可以使用「單元」或「自由」執行緒, 視它所建立的執行緒類型而定。|
   |**受**|指定物件使用無限制執行緒。 自由執行緒相當於多執行緒單元模型。 如需詳細資訊, 請參閱[多執行緒單元](/windows/win32/com/multithreaded-apartments)。|
   |**Neutral**|指定物件遵循多執行緒單元的指導方針, 但可以在任何類型的執行緒上執行。|

- **彙總**

   指出物件是否使用[匯總](/windows/win32/com/aggregation)。 匯總物件會選擇要公開給用戶端的介面, 而介面的公開方式就如同匯總物件所實。 匯總物件的用戶端只會與 aggregate 物件通訊。

   |選項|說明|
   |------------|-----------------|
   |**是**|指定可以匯總物件。 預設值。|
   |**No**|指定不匯總物件。|
   |**Only**|指定必須匯總物件。|

- **Interface**

   指出物件所支援的介面類型。 物件預設會支援雙重介面。

   |選項|說明|
   |------------|-----------------|
   |**雙重**|指定物件支援雙重介面 (其 vtable 具有自訂介面函數加上晚期繫結`IDispatch`方法)。 可讓 COM 用戶端和[自動化控制器](../../mfc/automation-clients.md)存取物件。 預設值。|
   |**自訂**|指定物件支援自訂介面 (其 vtable 具有自訂介面函式)。 自訂介面執行速度比雙重介面快，特別是跨處理序界限時。<br /><br /> - **自動化相容**允許 Automation 控制器存取具有自訂介面支援的物件。|

- **支援**

   指出物件的其他支援。

   |選項|說明|
   |------------|-----------------|
   |**ISupportErrorInfo**|建立適用於 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 介面的支援，以便讓物件將錯誤資訊傳回給用戶端。|
   |**連接點**|藉由讓物件的類別衍生自[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md), 為您的物件啟用連接點。|
   |**無限制執行緒封送處理器**|建立無限制執行緒封送處理器物件, 以便在相同進程中的執行緒之間有效率地封送處理介面指標。 可用於**同時**指定為執行緒模型的物件。|
   |**IObjectWithSite**(IE 物件支援)|會執行[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md), 以提供簡單的方式來支持對象及其在容器中的網站之間的通訊。|

## <a name="see-also"></a>另請參閱

[ATL 簡單物件精靈](../../atl/reference/atl-simple-object-wizard.md)<br/>
[ATL 簡單物件](../../atl/reference/adding-an-atl-simple-object.md)<br/>
[同進程伺服器執行緒問題](/windows/win32/com/in-process-server-threading-issues)
