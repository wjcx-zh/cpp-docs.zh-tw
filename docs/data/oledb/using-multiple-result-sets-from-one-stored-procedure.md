---
title: 從預存程序使用多重結果集
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 6163eb8bf18edfc3d205f1d012de0c64c5570693
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209283"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>從預存程序使用多重結果集

大部分的預存程式會傳回多個結果集。 這種預存程式通常包含一或多個 select 語句。 取用者必須考慮此包含來處理所有結果集。

## <a name="to-handle-multiple-result-sets"></a>若要處理多個結果集

1. 建立 `CCommand` 類別，其中具有 `CMultipleResults` 作為樣板引數，並使用您選擇的存取子（通常是動態或手動存取子）。 如果您使用其他類型的存取子，則可能無法判斷每個資料列集的輸出資料行。

1. 如往常般執行預存程式並系結資料行（請參閱[如何提取資料？](../../data/oledb/fetching-data.md)）。

1. 使用資料。

1. 呼叫 `CCommand` 類別上的 `GetNextResult`。 如果有另一個結果資料列集可供使用，`GetNextResult` 會傳回 S_OK 而如果您使用手動存取子，則應該重新系結資料行。 如果 `GetNextResult` 傳回錯誤，則沒有進一步的結果集可用。

## <a name="see-also"></a>另請參閱

[使用預存程序](../../data/oledb/using-stored-procedures.md)
