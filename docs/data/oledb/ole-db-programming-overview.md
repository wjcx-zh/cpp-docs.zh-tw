---
title: OLE DB 程式設計概觀
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 2b855e0917ba9cdbdaa38a92473d7bddb4279101
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210064"
---
# <a name="ole-db-programming-overview"></a>OLE DB 程式設計概觀

OLE DB 是高效能、以 COM 為基礎的資料庫技術。 它提供了一種常見的方式來存取資料，而不受其儲存所在的表單影響。 在一般的商務情況下，大量的資訊並不會儲存在公司資料庫中。 這項資訊可在檔案系統（例如 FAT 或 NTFS）、索引順序檔案、個人資料庫（例如 Access）、試算表（例如 Excel）、專案規劃應用程式（例如專案）和電子郵件（例如 Outlook）中找到。 OLE DB 可讓您以相同的方式存取任何類型的資料存放區，只要資料存放區具有 OLE DB 提供者即可。

OLE DB 可讓您開發存取不同資料來源的應用程式，不論它們是否為 DBMS。 OLE DB 使用支援給定資料來源之適當 DBMS 功能的 COM 介面，讓您能夠進行通用存取。 COM 可減少不必要的服務重複，而且不只是在資料來源，也能達到最大的互通性。

## <a name="benefits-of-com"></a>COM 的優點

這就是 COM 的來源。 OLE DB 是一組 COM 介面。 藉由一組統一的介面來存取資料，您可以將資料庫組織成一個合作元件的矩陣。

根據 COM 規格，OLE DB 會定義可延伸和可維護的介面集合，以構成並封裝一致、可重複使用的 DBMS 功能部分。 這些介面會定義 DBMS 元件的界限，例如資料列容器、查詢處理器和交易協調員，這可讓您對各種資訊來源進行統一的交易式存取。

## <a name="see-also"></a>另請參閱

[OLE DB 程式設計](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 範本](../../data/oledb/ole-db-templates.md)
