---
title: OLE DB 應用程式的資源集中化
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: c4e548d00f5772e41e0a725020cd2f279e3ab89b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479543"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>OLE DB 應用程式的資源集中化

若要充分利用在您的應用程式集區，您必須確定 OLE DB 服務會取得您的資料來源，透過叫用`IDataInitialize`或`IDBPromptInitialize`。 如果您直接使用`CoCreateInstance`要叫用提供者的 CLSID 為基礎的提供者，會叫用任何 OLE DB 服務。

OLE DB 服務維護連接的資料來源，只要參考的集區`IDataInitialize`或`IDBPromptInitialize`保留或只要是使用中的連線。 集區也會在 COM + 1.0 服務或 Internet Information Services (IIS) 的環境中自動維護。 如果您的應用程式會利用共用 COM + 1.0 服務或 IIS 環境之外，您應該保留的參考`IDataInitialize`或`IDBPromptInitialize`或保留至少一個連線。 若要確定，集區不會終結，最後一次連接發行應用程式時，保留參考，或保存您的應用程式的存留期的連接。

OLE DB 服務中識別集區連線繪製時的起點，`Initialize`呼叫。 連接取自集區之後，它不能移至不同的集區中。 因此，避免在您的應用程式中變更初始化資訊，例如呼叫的事`UnInitialize`或呼叫`QueryInterface`提供者特定介面，然後再呼叫`Initialize`。 此外，使用 DBPROMPT_NOPROMPT 以外的提示值建立的連接不共用。 不過，從透過提示所建立的連接擷取的初始化字串可用來建立其他共用相同的資料來源的連接。

某些提供者必須建立個別的連線，每個工作階段。 這些額外的連線都必須個別登錄在分散式交易中，如果有的話。 OLE DB 服務會快取並重複使用單一的工作階段，每個資料來源，但如果應用程式會要求一次的多個工作階段，從單一資料來源，最後的提供者可能會建立其他連接，以及進行的是其他交易登記不共用。 會在集區的環境，而不是從單一資料來源建立多個工作階段中建立每個工作階段的不同資料來源事實上會更有效率。

最後，因為 ADO 會自動將使用的 OLE DB 服務，您可以使用 ADO 來建立連接，以及共用和登記會自動發生。

## <a name="see-also"></a>另請參閱

[OLE DB 資源共用和服務](../../data/oledb/ole-db-resource-pooling-and-services.md)