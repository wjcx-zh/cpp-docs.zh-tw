---
title: 覆寫提供者服務預設值
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 08011f65ca220885e124e5ad6072244e4ad6e80d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282945"
---
# <a name="overriding-provider-service-defaults"></a>覆寫提供者服務預設值

OLEDB_SERVICES 的提供者的登錄值會傳回的預設值[DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85))初始化資料來源物件的屬性。

只要存在的登錄項目，會彙總提供者的物件。 使用者可以覆寫提供者的預設設定初始化之前 DBPROP_INIT_OLEDBSERVICES 屬性值已啟用的服務。 若要啟用或停用特定的服務，使用者會取得 DBPROP_INIT_OLEDBSERVICES 屬性的目前值、 設定或清除的位元為特定的屬性來啟用或停用，以及重設屬性。 直接在 OLE DB 或 ado 傳遞的連接字串中，就可以設定 DBPROP_INIT_OLEDBSERVICES 或`IDataInitialize::GetDatasource`。 啟用/停用個別的服務對應的值詳列於下表。

|預設啟用的服務|DBPROP_INIT_OLEDBSERVICES 屬性值|連接字串中的值|
|------------------------------|------------------------------------------------|--------------------------------|
|所有服務 （預設值）|DBPROPVAL_OS_ENABLEALL|"OLE DB Services = -1;"|
|集區以外的所有與自動編列|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|「 OLE DB 服務 =-4; 」|
|用戶端資料指標的全部項目|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services = -5;"|
|以外所有集區，自動編列和用戶端資料指標|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|「 OLE DB 服務 =-7;"|
|沒有服務|`~DBPROPVAL_OS_ENABLEALL`|「 OLE DB 服務 = 0;"|

如果登錄項目不存在提供者，元件管理員不會收集提供者的物件。 任何服務將會不開啟，即使使用者明確要求。

## <a name="see-also"></a>另請參閱

[資源集區](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[如何取用者會使用資源集區](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[提供者如何有效地使用資源集區](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[啟用和停用 OLE DB 服務](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>