---
title: 使用多個結果集從某個預存程序 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac30f74a593f79cea7f252c454f19b85260e27b8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078503"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>從預存程序使用多重結果集

大多數的預存程序會傳回多個結果集。 這類預存程序通常包含一個或多個 select 陳述式。 取用者需要考慮加入此項目來處理所有結果集。

## <a name="to-handle-multiple-result-sets"></a>若要處理多個結果集

1. 建立`CCommand`類別搭配`CMultipleResults`作為範本引數，並使用您的選擇，通常是動態或手動存取子的存取子。 如果您使用另一種存取子，您可能會無法決定每個資料列集的輸出資料行。

1. 如往常般執行預存程序和繫結資料行 (請參閱[How Do I 擷取資料嗎？](../../data/oledb/fetching-data.md))。

1. 使用的資料。

1. 呼叫`GetNextResult`上`CCommand`類別。 如果另一個結果資料列集可供使用，`GetNextResult`傳回 S_OK，如果您使用手動存取子，您應該繫結資料行。 如果`GetNextResult`會傳回錯誤，有提供任何進一步的結果集。

## <a name="see-also"></a>另請參閱

[使用預存程序](../../data/oledb/using-stored-procedures.md)