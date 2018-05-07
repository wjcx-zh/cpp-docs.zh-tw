---
title: 支援 OLE DB 中的異動 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ecd5b7274e62508289a83d6c0420d5f76e239e4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="supporting-transactions-in-ole-db"></a>支援 OLE DB 中的異動
A[交易](../../data/transactions-mfc-data-access.md)是群組，或批次，一系列的資料來源的更新，讓不是全部成功就無法認可一次就 （如果有任何一個將會失敗） 就無法認可任何的方法和回復整個交易。 此程序可確保資料來源上的結果的完整性。  
  
 OLE DB 支援交易，與下列三種方法：  
  
-   [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)  
  
-   [ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx)  
  
-   [ITransaction::Abort](https://msdn.microsoft.com/en-us/library/ms709833.aspx)  
  
## <a name="relationship-of-sessions-and-transactions"></a>工作階段和交易的關聯性  
 單一資料來源物件可以建立一或多個工作階段物件，其中每一個都可以是內部或外部交易，以在指定的時間範圍。  
  
 當工作階段不進入交易時，每個方法呼叫上立即認可完成該工作階段資料存放區上的所有工作。 （這有時候稱為自動認可模式或隱含的模式。）  
  
 當工作階段進入交易時，完成該工作階段資料存放區上的所有工作是該交易的一部分並認可或中止當做單一單位。 （這有時候稱為手動認可模式。）  
  
 提供者特定交易支援。 如果您使用的提供者支援交易，支援工作階段物件**itransaction::** 和**ITransactionLocal**可以輸入簡單 (亦即，非巢狀) 交易。 OLE DB 樣板類別[CSession](../../data/oledb/csession-class.md)支援這些介面，而且在 Visual c + + 中實作交易支援的建議的方式。  
  
## <a name="starting-and-ending-the-transaction"></a>開始和結束交易  
 您呼叫`StartTransaction`，**認可**，和**中止**消費者中的資料列集物件中的方法。  
  
 呼叫**itransactionlocal:: Starttransaction**啟動新的本機交易。 當您啟動交易時，任何後續作業所完成的變更不會實際套用到資料存放區之前認可的交易。  
  
 呼叫**itransaction:: Commit**或**itransaction:: Abort**結束交易。 **認可**會導致套用至資料存放區異動範圍內的所有變更。 **中止**交易啟動之前要取消交易和資料存放區的範圍內的所有變更會都處於狀態它的原因。  
  
## <a name="nested-transactions"></a>巢狀的交易  
 A[巢狀交易](https://msdn.microsoft.com/en-us/library/ms716985.aspx)發生於當使用中交易已經存在於工作階段，啟動新的本機交易。 以巢狀交易在目前交易下啟動新交易。 如果提供者不支援巢狀的交易，則呼叫`StartTransaction`工作階段上已有使用中交易時傳回**XACT_E_XTIONEXISTS**。  
  
## <a name="distributed-transactions"></a>分散式異動  
 分散式的交易是更新分散式的資料; 交易也就是一個以上的網路的電腦系統上的資料。 如果您想要透過分散式系統支援交易，您應該使用.NET Framework，而不是 OLE DB 交易支援。  
  
## <a name="see-also"></a>另請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)