---
title: 使用擷取運算子
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 1fc6ffd2f033dfe3df60260f734d93b79d6824f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626222"
---
# <a name="using-extraction-operators"></a>使用擷取運算子

擷取運算子 (`>>`) 已針對所有標準 C++ 資料類型進行預先程式設計，是從輸入資料流物件取得位元組的最簡單方式。

格式化的文字輸入擷取運算子會仰賴空白字元以分隔內送的資料值。 當文字欄位包含多個文字，或是當使用逗號來分隔數字時，這很不方便。 在這種情況下，其中一個替代方法是使用未格式化的輸入成員函式 [istream::getline](../standard-library/basic-istream-class.md#getline) 來讀取包含空白字元的文字區塊，然後使用特殊函式剖析該區塊。 另一個方法是使用成員函式 (例如 `GetNextToken`) 來衍生輸入資料流類別，該函式可以呼叫 istream 成員來擷取和格式化字元資料。

## <a name="see-also"></a>另請參閱

[輸入資料流](../standard-library/input-streams.md)<br/>
