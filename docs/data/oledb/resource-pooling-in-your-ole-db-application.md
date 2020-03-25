---
title: OLE DB 應用程式的資源集中化
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 3604f6eaaf0f34a0ff7e54826923c2aa92eef4a2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209757"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>OLE DB 應用程式的資源集中化

若要在您的應用程式中利用共用，您必須透過 `IDataInitialize` 或 `IDBPromptInitialize`取得您的資料來源，以確保叫用 OLE DB 的服務。 如果您直接使用 `CoCreateInstance` 根據提供者的 CLSID 叫用提供者，則不會叫用任何 OLE DB 的服務。

只要 `IDataInitialize` 或 `IDBPromptInitialize` 的參考，或只要有使用中的連接，OLE DB 服務就會維護已連線資料來源的集區。 集區也會自動在 COM + 1.0 服務或 Internet Information Services （IIS）環境中維護。 如果您的應用程式利用 COM + 1.0 服務或 IIS 環境的外部共用，您應該保留 `IDataInitialize` 或 `IDBPromptInitialize` 的參考，或保存至少一個連接。 為確保在應用程式發行最後一個連接時，不會終結集區，請在應用程式的存留期內保留參考或保存連接。

OLE DB 服務會識別在呼叫 `Initialize` 時，用來繪製連接的集區。 從集區中繪製連接之後，就無法將它移至不同的集區。 因此，請避免在您的應用程式中進行變更初始化資訊的作業，例如呼叫 `UnInitialize` 或呼叫提供者特定介面的 `QueryInterface`，再呼叫 `Initialize`。 此外，使用 DBPROMPT_NOPROMPT 以外的提示值所建立的連線不會共用。 不過，從透過提示所建立的連接中抓取的初始化字串，可以用來建立與相同資料來源的其他共用連接。

某些提供者必須為每個會話建立個別的連接。 這些額外的連接必須分別登錄在分散式交易中（如果有的話）。 OLE DB 服務會在每個資料來源中快取和重複使用單一會話，但如果應用程式一次要求一個以上的會話來自單一資料來源，則提供者可能會建立額外的連接，並執行其他的交易登記，不是集區。 針對集區環境中的每個會話建立不同的資料來源，會比從單一資料來源建立多個會話更有效率。

最後，因為 ADO 會自動使用 OLE DB 服務，所以您可以使用 ADO 來建立連接，而共用和登記會自動進行。

## <a name="see-also"></a>另請參閱

[OLE DB 資源共用和服務](../../data/oledb/ole-db-resource-pooling-and-services.md)
