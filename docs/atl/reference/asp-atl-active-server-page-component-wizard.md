---
title: ASP, ATL Active Server Page 元件精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.asp
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
ms.openlocfilehash: b88dffe2874d29918315af65c6ea093c24695f97
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503403"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, ATL Active Server Page 元件精靈

使用 ATL Active Server Page 元件精靈的這個頁面可指定選擇性設定處理資訊和與您的 ASP 元件的狀態。

- **選擇性方法**

   新增選擇性的 ASP 方法中， **OnStartPage**並**OnEndPage**，您的物件。 若要設定任何 Active Server Pages 的內建物件，就必須選取此選項。 根據預設，會選取它。

- **OnStartPage/OnEndPage**

   [OnStartPage](/previous-versions//ms691624\(v=vs.85\))稱為第一次指令碼會嘗試存取的物件。 **OnEndPage**物件完成時，會呼叫處理指令碼。

- **內建物件**

   您必須選取**OnStartPage/OnEndPage**選項可用來設定任何 ASP 內建物件。

|選項|描述|
|------------|-----------------|
|**要求**|可讓您存取內建的 Active Server Pages**要求**物件。 Request 物件用來將 HTTP 要求。|
|**回應**|可讓您存取內建的 Active Server Pages**回應**物件。 要求的回應，回應物件會將資訊傳送到瀏覽器顯示給使用者。|
|**工作階段**|可讓您存取內建的 Active Server Pages**工作階段**物件。 **工作階段**物件會維護目前的使用者工作階段，包括儲存和擷取狀態資訊的相關資訊。|
|**應用程式**|可讓您存取內建的 Active Server Pages**應用程式**物件。 **應用程式**物件會管理跨多個 ASP 物件共用的狀態。|
|**伺服器**|可讓您存取內建的 Active Server Pages **Server**物件。 **Server**物件可讓您建立 ASP 的其他物件。|

## <a name="see-also"></a>另請參閱

[ATL Active Server Page 元件精靈](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[ATL Active Server Page 元件](../../atl/reference/adding-an-atl-active-server-page-component.md)
