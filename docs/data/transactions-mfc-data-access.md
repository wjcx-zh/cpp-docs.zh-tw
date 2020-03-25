---
title: 交易 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
ms.openlocfilehash: 742e95d896d107fb89b3d65f0eeb6d418f1b2057
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209062"
---
# <a name="transactions--mfc-data-access"></a>交易 (MFC 資料存取)

交易的概念是特別開發來處理一些情況，其中資料庫的結果狀態取決於一系列的作業是否全部成功。 之所以如此，是因為後續的作業可能會修改之前作業的結果。 在這種情況下，如果任何一個作業失敗，產生的狀態可能會不確定。

若要解決這個問題，異動會將一系列的作業組成群組，以確保最後結果的完整性。 除非所有作業成功且受到認可 (寫入至資料庫)，否則整個異動會失敗。 取消交易就稱之為復原。 復原可以回復所做的變更，並會讓資料庫回到交易前的狀態。

例如，在自動化銀行異動中，如果您從帳戶 A 傳輸金錢到 B 帳戶，從 A 提款以及存錢至 B 必須同時成功，才能正確處理款項，否則整筆異動就算失敗。

異動必須有 ACID 屬性，其代表以下：

- **Atomicity**不可部分完成交易是不可部分完成的工作單位，而且只執行一次;所有工作都已完成，或都不是。

- **一致性**交易會保留資料的一致性，將資料的一個一致狀態轉換成另一個一致的資料狀態。 由異動繫結程序的資料必會保留語意。

- **隔離**交易是一種隔離單位，而且每個都是分開且獨立于並行交易。 異動絕不應該看見其他異動的中繼階段。

- **持久性**交易是一種復原單位。 如果交易成功，即使系統當機或被關閉，其更新都會被保存。 如果異動失敗，系統會停留在認可此異動之前的狀態。

您可以在 OLE DB 中支援交易（請參閱[支援 OLE DB 中的交易](../data/oledb/supporting-transactions-in-ole-db.md)）或 ODBC （請參閱[交易（ODBC）](../data/odbc/transaction-odbc.md)）。

分散式的交易是更新分散式資料的交易，也就是一個以上的網路電腦系統上的資料。 如果您想要透過分散式系統支援交易，您應該使用 ADO.NET，而不是 OLE DB 的交易支援。

## <a name="see-also"></a>另請參閱

[資料存取程式設計 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)
