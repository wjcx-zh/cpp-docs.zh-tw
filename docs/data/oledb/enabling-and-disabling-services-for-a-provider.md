---
title: 啟用和停用提供者的服務 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a5db612c836e4b902e7cad83017661246f4b649e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079384"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>啟用和停用提供者的服務

個別的 OLE DB 服務可以啟用或停用存取單一提供者的所有應用程式的預設值。 這是藉由新增提供者的 CLSID 下 OLEDB_SERVICES 登錄項目與`DWORD`值，指定要啟用或停用的服務下, 表所示。  
  
|預設啟用的服務|關鍵字的值|  
|------------------------------|-------------------|  
|所有服務 （預設值）|0xffffffff|  
|集區以外的所有與自動編列|0xfffffffe|  
|用戶端資料指標的全部項目|0xfffffffb|  
|以外所有集區，自動編列和用戶端資料指標|0xfffffff0|  
|沒有服務|0x00000000|  
|沒有彙總，所有服務已停用|\<遺漏金鑰 >|  
  
## <a name="see-also"></a>另請參閱  

[啟用和停用 OLE DB 服務](../../data/oledb/enabling-and-disabling-ole-db-services.md)