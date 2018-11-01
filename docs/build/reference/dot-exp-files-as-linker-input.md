---
title: .Exp 檔做為連結器輸入
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
ms.openlocfilehash: 4f70aad2fa91431da771f8e5be47956ae2db45a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661925"
---
# <a name="exp-files-as-linker-input"></a>.Exp 檔做為連結器輸入

匯出 (.exp) 檔案包含匯出函式和資料的項目的相關資訊。 當程式庫建立匯入程式庫時，它也會建立.exp 檔。 當您連結至匯出和匯入從另一個程式，直接或間接的程式，您可以使用.exp 檔。 如果您連結.exp 檔，連結不會產生匯入程式庫，因為它假設 LIB 已經建立一個。 如需有關.exp 檔案和匯入程式庫的詳細資訊，請參閱[使用 匯入程式庫和匯出檔案](../../build/reference/working-with-import-libraries-and-export-files.md)。

## <a name="see-also"></a>另請參閱

[LINK 輸入檔](../../build/reference/link-input-files.md)<br/>
[連結器選項](../../build/reference/linker-options.md)