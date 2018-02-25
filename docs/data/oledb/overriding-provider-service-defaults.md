---
title: "覆寫提供者服務預設 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8788de8ad28dc3c746155f59dee3ba5bb763bcaa
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="overriding-provider-service-defaults"></a>覆寫提供者服務預設值
提供者的登錄值**OLEDB_SERVICES**傳回的預設值為[DBPROP_INIT_OLEDBSERVICES](https://msdn.microsoft.com/en-us/library/ms716898.aspx)資料來源物件上的初始化屬性。  
  
 只要存在的登錄項目，提供者的物件彙總資料，而且使用者可以覆寫提供者的預設設定已啟用的服務設定**DBPROP_INIT_OLEDBSERVICES**之前初始化的屬性。 若要啟用或停用特定的服務，使用者通常取得的目前值**DBPROP_INIT_OLEDBSERVICES**屬性，設定或清除要啟用或停用的特定屬性的位元和重設屬性。 **DBPROP_INIT_OLEDBSERVICES**可以直接在 OLE DB 或 ADO 傳入的連接字串中設定或**idatainitialize:: Getdatasource**。 下表會列出啟用/停用個別的服務對應的值。  
  
|預設的服務啟用|DBPROP_INIT_OLEDBSERVICES 屬性值|連接字串中的值|  
|------------------------------|------------------------------------------------|--------------------------------|  
|所有服務 （預設值）|**DBPROPVAL_OS_ENABLEALL**|"OLE DB Services = -1;"|  
|除了共用及自動編列|**DBPROPVAL_OS_ENABLEALL （& S)**<br /><br /> **~DBPROPVAL_OS_RESOURCEPOOLING &**<br /><br /> **~DBPROPVAL_OS_TXNENLISTMENT**|"OLE DB Services = -4;"|  
|除了用戶端資料指標|**DBPROPVAL_OS_ENABLEALL** &<br /><br /> ~**DBPROPVAL_OS_CLIENTCURSOR**|"OLE DB Services = -5;"|  
|以外所有共用、 自動編列和用戶端資料指標|**DBPROPVAL_OS_ENABLEALL （& S)**<br /><br /> **~DBPROPVAL_OS_TXNENLISTMENT &**<br /><br /> **~DBPROPVAL_OS_CLIENTCURSOR**|"OLE DB Services = -7;"|  
|沒有任何服務|~**DBPROPVAL_OS_ENABLEALL**|"OLE DB Services = 0;"|  
  
 如果提供者的登錄項目不存在，元件管理員將不會彙總提供者的物件，並沒有任何服務將會叫用，即使明確要求的使用者。  
  
## <a name="see-also"></a>請參閱  
 [資源集區](https://msdn.microsoft.com/en-us/library/ms713655.aspx)   
 [消費者如何使用資源集區](https://msdn.microsoft.com/en-us/library/ms715907.aspx)   
 [提供者如何有效地使用資源集區](https://msdn.microsoft.com/en-us/library/ms714906.aspx)   
 [啟用和停用 OLE DB 服務](../../data/oledb/enabling-and-disabling-ole-db-services.md)