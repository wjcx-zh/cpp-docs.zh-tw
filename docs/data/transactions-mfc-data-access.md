---
title: 交易 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
ms.openlocfilehash: e3dc5b9319a8745ddb446ae7dbe895bfcd446c37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152653"
---
# <a name="transactions--mfc-data-access"></a>交易 (MFC 資料存取)

交易的概念是特別開發來處理一些情況，其中資料庫的結果狀態取決於一系列的作業是否全部成功。 之所以如此，是因為後續的作業可能會修改之前作業的結果。 在這種情況下，如果任何一個作業失敗，產生的狀態可能會不確定。

若要解決這個問題，異動會將一系列的作業組成群組，以確保最後結果的完整性。 除非所有作業成功且受到認可 (寫入至資料庫)，否則整個異動會失敗。 取消交易就稱之為復原。 復原可以回復所做的變更，並會讓資料庫回到交易前的狀態。

例如，在自動化銀行異動中，如果您從帳戶 A 傳輸金錢到 B 帳戶，從 A 提款以及存錢至 B 必須同時成功，才能正確處理款項，否則整筆異動就算失敗。

異動必須有 ACID 屬性，其代表以下：

- **不可部分完成性**交易是不可部分完成的工作單位，並只能執行一次，所有工作完成或全都都是。

- **一致性**： 異動會保留資料，將資料的一個一致的狀態轉換成另一個一致的狀態資料的一致性。 由異動繫結程序的資料必會保留語意。

- **隔離**異動是隔離的單位和個別且獨立的並行交易，每個發生。 異動絕不應該看見其他異動的中繼階段。

- **持久性**交易已復原的單位。 如果交易成功，即使系統當機或被關閉，其更新都會被保存。 如果異動失敗，系統會停留在認可此異動之前的狀態。

您可以支援 OLE DB 中的交易 (請參閱[支援 OLE DB 中的交易](../data/oledb/supporting-transactions-in-ole-db.md)) 或 ODBC (請參閱[異動 (ODBC)](../data/odbc/transaction-odbc.md))。

分散式的交易是更新分散式資料的交易，也就是一個以上的網路電腦系統上的資料。 如果您想要透過分散式系統支援交易，您應該使用 ADO.NET，而不是 OLE DB 異動支援。

## <a name="see-also"></a>另請參閱

[資料存取程式設計 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)