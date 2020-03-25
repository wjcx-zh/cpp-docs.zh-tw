---
title: 支援 OLE DB 中的異動
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
ms.openlocfilehash: e7ec4f69b4bba497446c94afb94cb5a1d648f7c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209535"
---
# <a name="supporting-transactions-in-ole-db"></a>支援 OLE DB 中的異動

[交易](../../data/transactions-mfc-data-access.md)是對資料來源的一系列更新進行分組或批次的方式，如此一來，不論是成功並同時認可，或（如果有任何一個失敗），都不會認可任何專案，且會回復整個交易。 此程式可確保資料來源上的結果完整性。

OLE DB 支援具有下列三種方法的交易：

- [ITransactionLocal：： StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction：： Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction：： Abort](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>會話和交易的關聯性

單一資料來源物件可以建立一或多個會話物件，每個物件都可以在指定時間的交易範圍內或外。

當會話未輸入交易時，在該會話的資料存放區中完成的所有工作都會在每個方法呼叫上立即認可。 （這有時稱為自動認可模式或隱含模式）。

當會話進入交易時，在該會話的資料存放區中完成的所有工作都是該交易的一部分，而且會被認可或中止為單一單位。 （這有時稱為手動認可模式）。

交易支援是提供者特有的。 如果您所使用的提供者支援交易，則支援 `ITransaction` 和 `ITransactionLocal` 的會話物件可以進入（非 nested）交易。 OLE DB 範本類別[CSession](../../data/oledb/csession-class.md)支援這些介面，而且是在視覺效果C++中執行交易支援的建議方式。

## <a name="starting-and-ending-the-transaction"></a>開始和結束交易

您會在取用者的資料列集物件中呼叫 `StartTransaction`、`Commit`和 `Abort` 方法。

呼叫 `ITransactionLocal::StartTransaction` 會啟動新的本機交易。 當您啟動交易時，在您認可交易之前，後續作業所強制進行的任何變更都不會套用至資料存放區。

呼叫 `ITransaction::Commit` 或 `ITransaction::Abort` 結束交易。 `Commit` 會使交易範圍內的所有變更套用至資料存放區。 `Abort` 會取消交易範圍內的所有變更，而且資料存放區會保留在交易啟動之前的狀態。

## <a name="nested-transactions"></a>嵌套交易

當您在會話上已經有使用中的交易時，當您開始新的本機交易時，就會發生[nested 交易](/previous-versions/windows/desktop/ms716985(v=vs.85))。 新交易會啟動為目前交易底下的嵌套交易。 如果提供者不支援已進行的交易，當會話上已經有使用中的交易時，呼叫 `StartTransaction`，就會傳回 XACT_E_XTIONEXISTS。

## <a name="distributed-transactions"></a>分散式交易

分散式交易是更新分散式資料的交易;也就是，在多個網路電腦系統上的資料。 如果您想要透過分散式系統支援交易，您應該使用 .NET Framework，而不是 OLE DB 的交易支援。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)
