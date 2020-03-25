---
title: ODBC 類別和執行緒
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 8cb5df605bef31e177e976798f975bb4ca14ced7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213155"
---
# <a name="odbc-classes-and-threads"></a>ODBC 類別和執行緒

從 MFC 4.2 開始，MFC ODBC 類別有多執行緒支援。 不過要注意的是，MFC 並不提供 DAO 類別的多執行緒支援。

ODBC 類別的多執行緒支援有一些限制。 因為這些類別會包裝 ODBC API，所以僅限於建立它們之元件的多執行緒支援。 例如，許多 ODBC 驅動程式都不是安全線程;因此，如果您搭配使用這些驅動程式的其中一個，則 MFC ODBC 類別不是安全線程。 您應該確認特定的驅動程式是否為安全線程。

建立多執行緒應用程式時，您應該非常小心地使用多個執行緒來操作相同的物件。 例如，在兩個執行緒中使用相同的 `CRecordset` 物件，可能會在抓取資料時造成問題;一個執行緒中的提取作業可能會覆寫在另一個執行緒中提取的資料。 在不同的執行緒中，MFC ODBC 類別的較常見用法是跨執行緒共用開啟的 `CDatabase` 物件，以使用相同的 ODBC 連接，並在每個執行緒中使用個別的 `CRecordset` 物件。 請注意，您不應該將未打開的 `CDatabase` 物件傳遞至另一個執行緒中的 `CRecordset` 物件。

> [!NOTE]
>  如果您必須有多個執行緒操作相同的物件，您應該執行適當的同步處理機制，例如重要區段。 請注意，某些作業（例如 `Open`）並未受到保護。 您應該確定不會從個別的執行緒同時呼叫這些作業。

如需有關建立多執行緒應用程式的詳細資訊，請參閱[多執行緒主題](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[資料存取程式設計 (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
