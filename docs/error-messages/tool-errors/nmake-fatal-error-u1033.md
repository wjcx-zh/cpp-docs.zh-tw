---
title: NMAKE 嚴重錯誤 U1033 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7492e5fd77f8e88b2191174f84c298c6166d8d89
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066373"
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE 嚴重錯誤 U1033

語法錯誤: 'string' 非預期

字串不以 makefile 的有效語法的一部分。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 如果在結尾的角括弧組 (**<<**) inline 檔不在行開頭，就會發生下列錯誤：

    ```
    syntax error : 'EOF' unexpected
    ```

1. Makefile 中的巨集定義如果包含等號 (**=**) 沒有前面名稱，或如果所定義的名稱會展開為無巨集，就會發生下列錯誤：

    ```
    syntax error : '=' unexpected
    ```

1. 如果分號 (**;**) 工具中的註解資料行中。INI 不在行首就會發生下列錯誤：

    ```
    syntax error : ';' unexpected
    ```

1. 如果 makefile 已經格式化的文字處理器，就會發生下列錯誤：

    ```
    syntax error : ':' unexpected
    ```