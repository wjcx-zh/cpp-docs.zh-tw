---
title: NMAKE 嚴重錯誤 U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 4511b15c84479c3531a3bea85964e2768de0181f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173383"
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE 嚴重錯誤 U1033

語法錯誤：未預期的 ' string '

字串不是 makefile 有效語法的一部分。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 如果內嵌檔案的右角括弧（ **<<** ）集合不在行首，則會發生下列錯誤：

    ```
    syntax error : 'EOF' unexpected
    ```

1. 如果 makefile 中的巨集定義包含不含前面名稱的等號（ **=** ），或如果要定義的名稱不是展開為任何內容的宏，則會發生下列錯誤：

    ```
    syntax error : '=' unexpected
    ```

1. 如果工具中的批註行中的分號（ **;** ）。INI 不在行的開頭，發生下列錯誤：

    ```
    syntax error : ';' unexpected
    ```

1. 如果 makefile 已由字處理器格式化，則可能會發生下列錯誤：

    ```
    syntax error : ':' unexpected
    ```
