---
title: 異動物件介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b8f03516aedcaf231f14943079eb9be40adf5be4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073119"
---
# <a name="transaction-object-interfaces"></a>異動物件介面

交易物件的資料來源上定義不可部分完成的工作單位，並判斷這些工作單位如何互相關聯性。 此物件不直接支援 OLE DB 提供者範本 （也就是您必須建立自己的物件）。

下表顯示由 OLE DB 定義的交易物件的必要和選用的介面。

|介面|是否為必要項？|實作 OLE DB 範本嗎？|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|強制|否|
|[ITransaction](/previous-versions/windows/desktop/ms723053)|強制|否|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|Optional|否|

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)