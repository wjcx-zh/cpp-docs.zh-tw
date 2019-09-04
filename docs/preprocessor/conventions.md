---
title: 檔慣例
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, conventions
ms.assetid: 469ce448-dc6c-4d0e-ba2b-e2e7a10155e1
ms.openlocfilehash: bb826b879b71edd3631c11a717320cee51c87175
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220368"
---
# <a name="document-conventions"></a>檔慣例

許多慣例會針對語法的不同元件使用不同的字型屬性。 符號和字型如下：

| 屬性 | 描述 |
|---------------|-----------------|
| *nonterminal* | 斜體類型表示非終端項。 |
| **#include** | 粗體類型的終端項為必須依下述方式輸入的常值保留字和符號。 此內容中的字元一律區分大小寫。 |
| <sub>opt</sub> | 後面接著非終端項的 <sub>opt</sub> 一律為選擇項。|
| 預設字樣 | 集合中以這個字樣描述或列出的字元可以做為陳述式中的終端頂使用。 |

接著非終端項的冒號 ( **:** ) 會引入其定義。 替代定義則會在其他行列出。

在程式碼語法區塊中, 預設字樣中的這些符號具有特殊意義:

| 符號 | 描述 |
|---|---|
| \[ ] | 方括弧會括住選擇性元素。 |
| { \| } | 大括弧括住以分隔號分隔的替代元素。 |
| ... | 表示可以重複先前的元素模式。 |

在程式碼語法區塊中,`,`逗號 ()、`.`句點 ()、分號 (`;`)、冒號 (`:`)、括弧 (`( )`)、雙引號 (`"`) 和單引號 (`'`) 都是常值。

## <a name="see-also"></a>另請參閱

[文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)
