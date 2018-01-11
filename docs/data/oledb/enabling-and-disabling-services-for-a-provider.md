---
title: "啟用和停用提供者的服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dc6b3d7cc8e80eaa24c2e2dd9b4e23e79dfb09f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>啟用和停用提供者的服務
個別的 OLE DB 服務可以啟用或停用存取單一提供者的所有應用程式的預設值。 這是藉由新增**OLEDB_SERVICES**提供者下的登錄項目具有的 CLSID，`DWORD`值，指定要啟用或停用的服務下, 表所示。  
  
|預設的服務啟用|關鍵字的值|  
|------------------------------|-------------------|  
|所有服務 （預設值）|0xffffffff|  
|除了共用及自動編列|0xfffffffe|  
|除了用戶端資料指標|0xfffffffb|  
|以外所有共用、 自動編列和用戶端資料指標|0xfffffff0|  
|沒有任何服務|0x00000000|  
|任何彙總，所有不服務已停用|\<遺漏金鑰 >|  
  
## <a name="see-also"></a>請參閱  
 [啟用和停用 OLE DB 服務](../../data/oledb/enabling-and-disabling-ole-db-services.md)