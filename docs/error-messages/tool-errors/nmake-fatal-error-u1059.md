---
title: NMAKE 嚴重錯誤 U1059 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b54919398c757bfe05f747ff57341f31decfc61
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200786"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 嚴重錯誤 U1059

> 語法錯誤: '}' 相依中遺漏

相依的搜尋路徑的指定不正確。 可能是有空格的路徑或右大括號中 (**}**) 已省略。

相依的目錄規格的語法是

> **{** *目錄* **} 相依**

何處*目錄*指定一個或多個路徑，每個以分號分隔 (**;**)。 允許不含空格。

如果以巨集取代部分或全部的搜尋路徑，請確定巨集展開中沒有空格。