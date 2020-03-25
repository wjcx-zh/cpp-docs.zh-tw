---
title: 編譯器警告 (層級 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: bc8131665c970c3b86bb1e84e39636ae8f93897b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199538"
---
# <a name="compiler-warning-level-1-c4651"></a>編譯器警告 (層級 1) C4651

為先行編譯標頭指定的 ' definition '，但不適用於目前的編譯

定義是在產生先行編譯標頭檔時指定，但不是在此編譯中。

定義會在先行編譯的標頭內生效，但不會在其餘的程式碼中。

如果先行編譯標頭檔是以/DSYMBOL 建立，則如果/Yu 編譯沒有/DSYMBOL.，編譯器會產生這個警告。  將/DSYMBOL 新增至/Yu 命令列會解決此警告。
