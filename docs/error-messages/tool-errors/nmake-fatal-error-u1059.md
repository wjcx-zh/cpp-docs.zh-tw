---
title: NMAKE 嚴重錯誤 U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 3c148bf2feb7ba12686e00b29f5bf90cb9f2f2d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367287"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 嚴重錯誤 U1059

> 語法錯誤: '}' 相依中遺漏

相依的搜尋路徑的指定不正確。 可能是有空格的路徑或右大括號中 (**}**) 已省略。

相依的目錄規格的語法是

> **{** *directories* **}dependent**

何處*目錄*指定一個或多個路徑，每個以分號分隔 (**;**)。 允許不含空格。

如果以巨集取代部分或全部的搜尋路徑，請確定巨集展開中沒有空格。