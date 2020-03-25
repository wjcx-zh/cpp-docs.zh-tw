---
title: 編譯器警告（層級1） C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5f2350f275f883e7bf18aa1621d08b34132e8dfb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175842"
---
# <a name="compiler-warning-level-1-c4274"></a>編譯器警告（層級1） C4274

已忽略 \#ident;請參閱 #pragma 批註的檔（exestr，' string '）

在物件或可執行檔中插入使用者指定之字串的 `#ident` 指示詞已被取代。 因此，編譯器會忽略指示詞。

> [!CAUTION]
>  警告 C4274 會建議您使用[#pragma 批註（exestr，' string '）](../../preprocessor/comment-c-cpp.md)指示詞。 不過，這項建議已被取代，將在未來的編譯器版本中修訂。 如果您使用 `#pragma` 指示詞，連結器工具（LINK .exe）會忽略指示詞所產生的批註記錄，併發出警告[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)。 我們建議您在應用程式中使用檔案版本資源字串，而不是 `#ident` 指示詞。

## <a name="to-correct-this-error"></a>若要改正這項錯誤

- 移除 `#ident "`*字串*`"` 指示詞。

## <a name="see-also"></a>另請參閱

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[連結器工具警告 LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[使用資源檔](../../windows/working-with-resource-files.md)
