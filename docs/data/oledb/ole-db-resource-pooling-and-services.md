---
title: OLE DB 資源集中化和服務
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: f46c6f493ae41570c75c384fcc836707faeab99f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023746"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB 資源集中化和服務

若要搭配 OLE DB 共用，或任何 OLE DB 服務，您的提供者必須支援所有物件的彙的總。 這是任何 OLE DB 1.5 或更新版本的提供者的需求。 最重要的是利用服務。 不支援彙總的提供者無法共用，並且會提供任何其他服務。

若要共用，提供者必須支援無限制執行緒模型。 資源集區會決定根據 DBPROP_THREADMODEL 屬性的提供者的執行緒模型。

如果提供者具有全域連線狀態，可能會變更資料來源初始化的狀態時，它應該支援新的 DBPROP_RESETDATASOURCE 屬性。 此屬性稱為之前連線重複使用，並讓提供者有機會先清除其下一步 使用之前的狀態。 如果提供者無法清除某些與連接相關聯的狀態，它會傳回 DBPROPSTATUS_NOTSETTABLE 的屬性，並不會重複使用的連接。

連接到遠端資料庫，以及可以偵測到該連線是否可能遺失的提供者應該支援 DBPROP_CONNECTIONSTATUS 屬性。 這個屬性會讓 OLE DB 服務能夠偵測無作用的連線，並確定它們未返回集區。

最後，自動異動登記通常無法運作除非它實作共用，就會發生相同層級。 支援自動交易登記的提供者應該支援停用這個登記公開 DBPROP_INIT_OLEDBSERVICES 屬性，而如果 DBPROPVAL_OS_TXNENLISTMENT 取消選取此選項，請停用登錄。

## <a name="see-also"></a>另請參閱

[進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)