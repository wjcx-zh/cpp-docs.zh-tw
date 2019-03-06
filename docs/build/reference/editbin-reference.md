---
title: EDITBIN 參考
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
ms.openlocfilehash: 39fdcfd3221599f20617092118e5cef5267e3d2b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418785"
---
# <a name="editbin-reference"></a>EDITBIN 參考

Microsoft COFF 二進位檔案編輯器 (EDITBIN。EXE) 修改通用物件檔案格式 (COFF) 二進位檔。 您可以使用 EDITBIN 來修改物件的檔案、 可執行檔，以及動態連結程式庫 (DLL)。

> [!NOTE]
>  您可以啟動此工具只能從 Visual Studio 命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

EDITBIN 不適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。 /GL 與所產生的二進位檔案的任何修改就必須重新編譯並連結來達成。

- [EDITBIN 命令列](../../build/reference/editbin-command-line.md)

- [EDITBIN 選項](../../build/reference/editbin-options.md)

## <a name="see-also"></a>另請參閱

[C/C++ 建置工具](../../build/reference/c-cpp-build-tools.md)
