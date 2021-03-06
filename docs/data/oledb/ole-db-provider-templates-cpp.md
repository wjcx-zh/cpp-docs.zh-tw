---
title: OLE DB 提供者樣板 (C++)
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
ms.openlocfilehash: 793aa08630ec92f99c33c2a4f3688e78630a6c58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361252"
---
# <a name="ole-db-provider-templates-c"></a>OLE DB 提供者樣板 (C++)

OLE DB 是 Microsoft 通用資料存取策略中很重要的一部分。 OLE DB 設計允許從任何資料來源的高效能的資料存取。 可透過 OLE DB 不論它是否來自資料庫檢視任何表格式資料。 彈性可讓您極大的電源。

中所述[OLE DB 消費者和提供者](../../data/oledb/ole-db-consumers-and-providers.md)，OLE DB 使用取用者和提供者的概念。 取用者針對提出要求的資料;提供者會傳回給取用者以表格式格式的資料。 程式設計的觀點而言，這個模型的最重要的用意是提供者必須實作可讓取用者的任何呼叫。

## <a name="what-is-a-provider"></a>什麼是提供者？

OLE DB 提供者是一份服務取用者物件的介面呼叫的 COM 物件，從持久的來源 （稱為資料存放區） 的表格式格式的資料傳輸給取用者。

提供者可以是簡單或很複雜。 提供者可以藉由實作多個介面支援的最少的功能或成熟的生產品質提供者。 提供者可以傳回資料表，允許用戶端決定該資料表的格式和執行對該資料的作業。

每個提供者會實作一組標準的 COM 物件來處理來自用戶端的要求，也就是說，任何 OLE DB 標準取用者可以存取資料，請在任何提供者，不論語言為何 (例如C++和基本)。

每個 COM 物件都包含數個介面，其中有些是必要，而其中有些是選擇性。 藉由實作必要的介面，提供者可確保任何用戶端應該能夠使用的功能 （稱為合規性） 的最低層級。 提供者可實作選擇性的介面，以提供額外的功能。 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)這些介面的詳細資料。 用戶端應該一律呼叫`QueryInterface`來判斷提供者是否支援指定的介面。

## <a name="ole-db-specification-level-support"></a>OLE DB 規格的層級支援

OLE DB 提供者範本支援 OLE DB 2.7 版規格。 您可以使用 OLE DB 提供者範本，來實作層級 0 相容的提供者。 `Provider`範例中，例如，使用範本來實作執行 DOS DIR 命令來查詢檔案系統的 non-MS-DOS 命令伺服器。 `Provider`範例會傳回目錄資訊中的資料列集，這是傳回表格式資料的標準 OLE DB 機制。

最簡單的 OLE DB 範本所支援的提供者類型是唯讀的提供者，使用任何命令。 也支援使用命令的提供者，因為書籤和讀取/寫入功能。 您可以撰寫其他程式碼來實作讀取/寫入提供者。 最新版本，不支援動態資料列集和交易，但如果您要新增它們。

## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>您需要時建立的 OLE DB 提供者？

您永遠不需要建立自己的提供者;Microsoft 提供數個預先封裝的標準提供者，在**資料連結屬性**視覺效果中的對話方塊中C++。 若要建立的 OLE DB 提供者的主要原因是運用通用資料存取策略。 這麼做的優點，包括：

- 透過任何語言存取資料，例如C++、 Basic 和 Visual Basic Scripting Edition。 它可讓您組織中不同程式設計人員可以存取相同的資料相同的方式，不論使用哪種語言。

- 開啟您的資料，例如 SQL Server、 Excel 及存取其他資料來源。 這可以是很有用，如果您想要在不同的格式之間的資料傳輸。

- 參與 （異質性） 的跨資料來源的作業。 這可以是資料倉儲的有效方式。 藉由使用 OLE DB 提供者，您可以將資料保存原生格式，並仍能夠存取在簡單的作業。

- 其他功能加入您的資料，例如查詢處理。

- 增加存取資料，藉由控制它的操作方式的效能。

- 增加強固性。 如果您有專屬的資料格式，只有一位程式設計人員存取，您就有風險。 使用 OLE DB 提供者，可以開啟該專屬格式，您所有的程式設計人員。

## <a name="read-only-and-updatable-providers"></a>唯讀和可更新的提供者

提供者在複雜度和功能差異極大。 您最好將分類為唯讀狀態提供者和可更新的提供者的提供者：

- 視覺化C++6.0 支援只有唯讀提供者。 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)討論如何建立唯讀的提供者。
- 視覺化C++支援可更新的提供者，可以更新它 （寫入） 資料存放區。 可更新的提供者的相關資訊，請參閱[建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md); [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)範例是可更新的提供者。

如需詳細資訊，請參閱:

- [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)

- [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)

- [OLE DB 程式設計](../../data/oledb/ole-db-programming.md)

## <a name="see-also"></a>另請參閱

[資料存取](../data-access-in-cpp.md)<br/>
[OLE DB SDK 文件](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[OLE DB 設計人員參考](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)<br/>
