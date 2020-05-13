---
title: 編譯器警告(級別 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5d005fccc5920aea61698a65edf9284d56366a1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377082"
---
# <a name="compiler-warning-level-1-c4274"></a>編譯器警告(級別 1) C4274

\#標識被忽略;請參閱文件,瞭解#pragma註釋(exestr,"字串")

該`#ident`指令在物件或可執行檔中插入使用者指定的字串,該指令將被棄用。 因此,編譯器忽略該指令。

> [!CAUTION]
> 警告 C4274 建議您使用[#pragma注释(exestr,"字串")](../../preprocessor/comment-c-cpp.md)指令。 但是,此建議被棄用,並將在編譯器的未來版本中進行修訂。 如果使用此`#pragma`指令,連結器工具 (LINK.exe) 會忽略這個指令產生的註解紀錄,並發出警告[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)。 我們建議您在應用程式中`#ident`使用檔案版本資源字串,而不是該指令。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 刪除`#ident "`*字串*`"`指令。

## <a name="see-also"></a>另請參閱

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[連結器工具警告 LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[使用資源檔](../../windows/working-with-resource-files.md)
