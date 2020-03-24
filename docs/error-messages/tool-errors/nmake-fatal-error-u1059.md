---
title: NMAKE 嚴重錯誤 U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 33be3312e1f0aaa7f1e8aad64b44ea9aefd25346
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182834"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 嚴重錯誤 U1059

> 語法錯誤：相依中遺漏 '} '

未正確指定相依的搜尋路徑。 路徑中有空格或已省略右大括弧（ **}** ）。

相依目錄規格的語法為

> **{** *directory* **} 相依**

其中，*目錄*會指定一或多個路徑，並以分號（ **;** ）分隔。 不允許空格。

如果部分或所有搜尋路徑已由宏取代，請確定宏展開中沒有任何空格。
