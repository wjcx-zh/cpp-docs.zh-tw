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
ms.openlocfilehash: 67eeffff2bf165a5ccbdbaa546ad5b9ca9a57914
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210024"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB 資源集中化和服務

您的提供者必須支援所有物件的匯總，才能與 OLE DB 共用或任何 OLE DB 服務搭配運作。 這是任何 OLE DB 1.5 或更新版本提供者的需求。 這對於利用服務非常重要。 不支援匯總的提供者無法集區，也不會提供其他服務。

若要進行集區，提供者必須支援免費的執行緒模型。 資源集區會根據 DBPROP_THREADMODEL 屬性來決定提供者的執行緒模型。

如果提供者的全域連接狀態在資料來源處於初始化狀態時可能會變更，則它應該支援新的 DBPROP_RESETDATASOURCE 屬性。 在重複使用連接之前，會呼叫這個屬性，讓提供者有機會在下一次使用之前清除狀態。 如果提供者無法清除與連接相關聯的某些狀態，它可以傳回屬性的 DBPROPSTATUS_NOTSETTABLE，而且不會重複使用連接。

連接到遠端資料庫並可偵測該連接是否可能遺失的提供者，應該支援 DBPROP_CONNECTIONSTATUS 屬性。 此屬性可讓 OLE DB 服務偵測出不正確連線，並確保它們不會傳回到集區。

最後，自動交易登記通常不會運作，除非它是在共用發生的相同層級上執行。 支援自動交易登錄的提供者應該支援藉由公開 DBPROP_INIT_OLEDBSERVICES 屬性來停用此登記，如果取消選取 DBPROPVAL_OS_TXNENLISTMENT 則停用登記。

## <a name="see-also"></a>另請參閱

[進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)
