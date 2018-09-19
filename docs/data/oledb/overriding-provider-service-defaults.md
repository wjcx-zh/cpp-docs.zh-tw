---
title: 覆寫提供者服務預設值 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 561617628e79513434d498d4c5e5af8ff2c189be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104903"
---
# <a name="overriding-provider-service-defaults"></a>覆寫提供者服務預設值

OLEDB_SERVICES 的提供者的登錄值會傳回的預設值[DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898\(v=vs.85\))初始化資料來源物件的屬性。  
  
只要登錄項目存在，提供者的物件會彙總，而且使用者可以覆寫提供者的預設設定為已啟用的服務，藉由設定`DBPROP_INIT_OLEDBSERVICES`之前初始化的屬性。 若要啟用或停用特定的服務，使用者通常取得的目前值`DBPROP_INIT_OLEDBSERVICES`屬性，設定或清除的位元為特定的屬性來啟用或停用，以及重設屬性。 `DBPROP_INIT_OLEDBSERVICES` 可以直接在 OLE DB 或 ado 傳遞的連接字串中設定或`IDataInitialize::GetDatasource`。 啟用/停用個別的服務對應的值詳列於下表。  
  
|預設啟用的服務|DBPROP_INIT_OLEDBSERVICES 屬性值|連接字串中的值|  
|------------------------------|------------------------------------------------|--------------------------------|  
|所有服務 （預設值）|`DBPROPVAL_OS_ENABLEALL`|「 OLE DB 服務 =-1;"|  
|集區以外的所有與自動編列|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|「 OLE DB 服務 =-4; 」|  
|用戶端資料指標的全部項目|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|「 OLE DB 服務 =-5，"|  
|以外所有集區，自動編列和用戶端資料指標|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|「 OLE DB 服務 =-7;"|  
|沒有服務|`~DBPROPVAL_OS_ENABLEALL`|「 OLE DB 服務 = 0;"|  
  
如果提供者的登錄項目不存在，元件管理員將不會彙總提供者的物件，並沒有服務會叫用，即使使用者明確要求。  
  
## <a name="see-also"></a>另請參閱  

[資源集區](/previous-versions/windows/desktop/ms713655\(v=vs.85\))   
[如何取用者會使用資源集區](/previous-versions/windows/desktop/ms715907\(v=vs.85\))   
[提供者如何有效地使用資源集區](/previous-versions/windows/desktop/ms714906\(v=vs.85\))   
[啟用和停用 OLE DB 服務](../../data/oledb/enabling-and-disabling-ole-db-services.md)