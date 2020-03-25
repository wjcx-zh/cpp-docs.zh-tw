---
title: 覆寫提供者服務預設值
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 4cf3ad1064627f64315822a5045642aa50330d10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209791"
---
# <a name="overriding-provider-service-defaults"></a>覆寫提供者服務預設值

提供者的 OLEDB_SERVICES 的登錄值會當做資料來源物件上[DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85))初始化屬性的預設值傳回。

只要登錄專案存在，就會匯總提供者的物件。 使用者可以在初始化之前設定 DBPROP_INIT_OLEDBSERVICES 屬性，以覆寫已啟用服務之提供者的預設設定。 若要啟用或停用特定服務，使用者會取得 DBPROP_INIT_OLEDBSERVICES 屬性的目前值，設定或清除要啟用或停用之特定屬性的位，然後重設屬性。 DBPROP_INIT_OLEDBSERVICES 可以直接在 OLE DB 中，或在傳遞至 ADO 或 `IDataInitialize::GetDatasource`的連接字串中設定。 下表列出啟用/停用個別服務的對應值。

|預設服務已啟用|DBPROP_INIT_OLEDBSERVICES 屬性值|連接字串中的值|
|------------------------------|------------------------------------------------|--------------------------------|
|所有服務（預設值）|DBPROPVAL_OS_ENABLEALL|"OLE DB Services =-1;"|
|除了 Pooling 和 AutoEnlistment 以外的所有|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB Services =-4;"|
|除了用戶端資料指標以外的所有|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-5;"|
|除了 Pooling、AutoEnlistment 和用戶端資料指標以外的所有|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-7;"|
|沒有服務|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB Services = 0;"|

如果提供者的登錄專案不存在，則元件管理員不會收集提供者的物件。 即使使用者明確要求，也不會開啟任何服務。

## <a name="see-also"></a>另請參閱

[資源集區](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[取用者如何使用資源分享](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[提供者如何有效地與資源分享搭配運作](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[啟用和停用 OLE DB 服務](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>
