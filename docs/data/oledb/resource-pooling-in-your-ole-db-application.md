---
title: OLE DB 應用程式的資源集中化
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 2dc5fbe760b2e62eec8b974bb496e52d1de25f50
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "51264954"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>OLE DB 應用程式的資源集中化

若要充分利用在您的應用程式集區，您必須確定 OLE DB 服務由通過您的資料來源叫用`IDataInitialize`或`IDBPromptInitialize`。 如果您直接使用`CoCreateInstance`要叫用提供者的 CLSID 為基礎的提供者，會叫用任何 OLE DB 服務。

OLE DB 服務維護連接的資料來源，只要參考的集區`IDataInitialize`或`IDBPromptInitialize`保留或只要是使用中的連線。 集區也會在 COM + 1.0 服務或 Internet Information Services (IIS) 的環境中自動維護。 如果您的應用程式會利用共用外部 COM + 1.0 服務或 IIS 環境，您應該保留的參考`IDataInitialize`或`IDBPromptInitialize`或保留至少一個連線。 若要確保集區不會終結，最後一次連接發行應用程式時，保留參考，或保存您的應用程式的存留期的連接。

OLE DB 服務中識別集區連線繪製時的起點，`Initialize`呼叫。 連接取自集區之後，它不能移至不同的集區中。 因此，請避免在您的應用程式中變更初始化資訊，例如呼叫的事`UnInitialize`或呼叫`QueryInterface`提供者特定介面，然後再呼叫`Initialize`。 此外，不被共用與 DBPROMPT_NOPROMPT 以外的提示值建立的連線。 不過，從透過提示所建立的連接擷取的初始化字串可用來建立其他共用相同的資料來源的連接。

某些提供者必須建立個別的連線，每個工作階段。 這些額外的連線都必須個別登錄在分散式交易中，如果有的話。 OLE DB 服務的快取和重複使用單一的工作階段，每個資料來源，但如果應用程式會要求一次的多個工作階段，從單一資料來源，最後的提供者可能會建立其他連接，以及進行其他的交易登記，不共用。 它會更有效率的方式建立的集區的環境，而不是從單一資料來源建立多個工作階段中的每個工作階段的不同資料來源。

最後，因為 ADO 會自動將使用的 OLE DB 服務，您可以使用 ADO 來建立連接，以及共用和登記會自動發生。

## <a name="see-also"></a>另請參閱

[OLE DB 資源共用和服務](../../data/oledb/ole-db-resource-pooling-and-services.md)