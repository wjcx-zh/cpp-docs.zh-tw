---
title: 啟用和停用提供者的服務
ms.date: 07/30/2019
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: a74f8a8b099a30cf25007547e8059c77728435f9
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "70311812"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>啟用和停用提供者的服務

所有存取單一提供者的應用程式，預設都可以啟用或停用個別 OLE DB 服務。 這是藉由在提供者的 CLSID 底下新增 OLEDB_SERVICES 登錄專案來完成，其中包含指定要啟用或停用服務的 DWORD 值，如下表所示。

|預設服務已啟用|DWORD 值|
|------------------------------|-------------------|
|除了用戶端資料指標和共用以外的所有服務|0xfffffffa|
|用戶端資料指標以外的所有服務|0xfffffffb|
|共用和自動登記以外的所有服務|0xfffffffc|
|共用以外的所有服務|0xfffffffe|
|所有服務（預設值）|0xffffffff|
|沒有服務|0x00000000|
|沒有匯總，已停用所有服務|沒有 OLEDB_Services 登錄專案|

## <a name="see-also"></a>另請參閱

[啟用和停用 OLE DB 服務](../../data/oledb/enabling-and-disabling-ole-db-services.md)
