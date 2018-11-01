---
title: ODBC 類別和執行緒
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 1d470e79ba5a6a73a30743a21da0462a6b89e7da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608165"
---
# <a name="odbc-classes-and-threads"></a>ODBC 類別和執行緒

從 MFC 4.2 開始，沒有適用於 MFC ODBC 類別的多執行緒支援。 不過，要注意的是，MFC 不需 DAO 類別提供多執行緒的支援。

ODBC 類別的多執行緒支援有一些限制。 這些類別會包裝 ODBC API，因為它們僅限於建立所在的元件進行多執行緒處理的支援。 比方說，許多 ODBC 驅動程式不是安全執行緒，因此，MFC ODBC 類別不具備執行緒安全如果您使用其中一個這些驅動程式使用。 您應該確認您的特定驅動程式是否具備執行緒安全。

在建立多執行緒應用程式時，您應該非常小心使用多個執行緒操作相同的物件。 例如，使用相同`CRecordset`兩個執行緒中的物件可能會造成問題，擷取資料時，一個執行緒中的提取作業可能會覆寫在另一個執行緒中提取的資料。 MFC ODBC 類別，在個別執行緒中的較常見用法是共用開啟`CDatabase`多個使用相同的 ODBC 連接，使用不同的執行緒物件`CRecordset`中每個執行緒的物件。 請注意，您不應將傳遞未開啟`CDatabase`物件至`CRecordset`另一個執行緒的物件。

> [!NOTE]
>  如果您必須有多個執行緒操作相同的物件，您應該實作適當的同步處理機制，例如關鍵區段。 請注意，某些作業，例如`Open`，未受保護。 您應該確定，這些作業將不會呼叫同時從不同的執行緒。

如需建立多執行緒應用程式的詳細資訊，請參閱 <<c0> [ 多執行緒主題](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[資料存取程式設計 (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)