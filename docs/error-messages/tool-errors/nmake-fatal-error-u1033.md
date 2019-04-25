---
title: NMAKE 嚴重錯誤 U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 3b1df28e3cd7b27a9e7a130d9d71c1af68db9aec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324359"
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