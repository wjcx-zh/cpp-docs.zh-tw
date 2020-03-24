---
title: 編譯器警告 (層級 3) C4622
ms.date: 11/04/2016
f1_keywords:
- C4622
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
ms.openlocfilehash: 295a183afb24121a2abefd336f6ea92110220155
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185500"
---
# <a name="compiler-warning-level-3-c4622"></a>編譯器警告 (層級 3) C4622

覆寫在目的檔中建立先行編譯標頭檔期間產生的偵錯資訊: 'file'

所指定檔案中的 CodeView 資訊在使用 [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (使用先行編譯標頭檔) 選項編譯時遺失。

建立或使用先行編譯標頭檔時，請重新命名物件檔案 (使用 [/Fo](../../build/reference/fo-object-file-name.md))，或者使用新的物件檔案進行連結。
