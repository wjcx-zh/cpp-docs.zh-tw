---
title: 編譯器警告 （層級 1） C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: f73fa8e09baab127e7755ebe3def69c2fb585744
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028456"
---
# <a name="compiler-warning-level-1-c4274"></a>編譯器警告 （層級 1） C4274

\#ident ignored; see documentation for #pragma comment(exestr, 'string')

`#ident`指示詞，將使用者指定的字串插入的物件或可執行檔，已被取代。 因此，編譯器會忽略指示詞。

> [!CAUTION]
>  警告 C4274 會建議您將[#pragma 註解 （exestr，'string'）](../../preprocessor/comment-c-cpp.md)指示詞。 不過，這項建議已被取代，而且將在編譯器的未來版本中經過修改。 如果您使用`#pragma`指示詞，連結器工具 (LINK.exe) 會忽略指示詞所產生的註解記錄，並且會發出警告[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)。 而不是`#ident`指示詞時，我們建議您在應用程式中使用的檔案版本資源字串。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 移除`#ident "`*字串*`"`指示詞。

## <a name="see-also"></a>另請參閱

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[連結器工具警告 LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[使用資源檔](../../windows/working-with-resource-files.md)