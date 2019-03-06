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
ms.openlocfilehash: 2e3605b636bbcb16a1c6f543bc9090d2b212a60b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418566"
---
# <a name="supporting-transactions-in-ole-db"></a>支援 OLE DB 中的異動

A[交易](../../data/transactions-mfc-data-access.md)可以群組或批次，一系列的資料來源的更新，讓所有成功，而且會一次認可或 （如果有任何其中一個失敗） 都已認可和回復整個交易。 此程序可確保資料來源之結果的完整性。

OLE DB 支援使用下列三個方法的交易：

- [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction::Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction::Abort](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>工作階段和交易的關聯性

單一資料來源物件可以建立一或多個工作階段物件，其中每一個可以是內部或外部交易，以在指定的時間範圍。

當工作階段不輸入交易時，該工作階段內完成資料存放區的所有工作立即都認可上每個方法呼叫。 （這有時候稱為自動認可模式或隱含的模式。）

當工作階段輸入交易時，完成該工作階段資料存放區的所有工作是該交易的一部分並認可或中止當做單一單位。 （這有時候稱為手動認可模式。）

提供者特定交易支援。 如果您使用的提供者支援交易，支援工作階段物件`ITransaction`和`ITransactionLocal`可以輸入 （非巢狀） 的交易。 OLE DB 範本類別[CSession](../../data/oledb/csession-class.md)支援這些介面，而且是在 Visual c + + 中實作交易支援的建議的方式。

## <a name="starting-and-ending-the-transaction"></a>開始和結束交易

您呼叫`StartTransaction`， `Commit`，和`Abort`消費者中的資料列集物件中的方法。

呼叫`ITransactionLocal::StartTransaction`啟動新的本機交易。 當您啟動交易時，更新作業所完成的任何變更無法套用至資料存放區，直到認可交易。

呼叫`ITransaction::Commit`或`ITransaction::Abort`結束交易。 `Commit` 會導致套用至資料存放區交易範圍內的所有變更。 `Abort` 交易開始之前取消交易和資料存放區的範圍內的所有變更會都停留在狀態，它的原因。

## <a name="nested-transactions"></a>巢狀的交易

A[巢狀交易](/previous-versions/windows/desktop/ms716985(v=vs.85))發生於當使用中交易已經存在於工作階段啟動新的本機交易。 做為巢狀交易，在目前交易下啟動新的交易。 如果提供者不支援巢狀的交易，呼叫`StartTransaction`時已經有使用中交易的工作階段上傳回 XACT_E_XTIONEXISTS。

## <a name="distributed-transactions"></a>分散式異動

分散式的交易是交易中更新分散式的資料;也就是一個以上的網路的電腦系統上的資料。 如果您想要透過分散式系統支援交易，您應該使用.NET Framework，而不是 OLE DB 異動支援。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)