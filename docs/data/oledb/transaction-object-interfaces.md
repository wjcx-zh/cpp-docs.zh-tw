---
title: 異動物件介面
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
ms.openlocfilehash: b86064c162dcacfbbc5877614c63d92d0f2bd347
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311669"
---
# <a name="transaction-object-interfaces"></a>異動物件介面

交易對象定義資料來源的不可部分完成單位，並決定這些工作單位之間的關聯性。 OLE DB 提供者範本不直接支援這個物件（也就是您必須建立自己的物件）。

下表顯示由 OLE DB 針對交易對象所定義的必要和選擇性介面。

|介面|必要項？|由 OLE DB 範本來執行？|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|強制|否|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|強制|否|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|選擇性|否|

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
