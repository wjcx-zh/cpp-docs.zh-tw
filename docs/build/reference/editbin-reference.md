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
ms.openlocfilehash: 45c2967a55e85ae31bb77bb2e8d50415eafbea46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293026"
---
# <a name="editbin-reference"></a>EDITBIN 參考

Microsoft COFF 二進位檔案編輯器 (EDITBIN。EXE) 修改通用物件檔案格式 (COFF) 二進位檔。 您可以使用 EDITBIN 來修改物件的檔案、 可執行檔，以及動態連結程式庫 (DLL)。

> [!NOTE]
>  您可以啟動此工具只能從 Visual Studio 命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

EDITBIN 不適用於所產生的檔案上[/GL](gl-whole-program-optimization.md)編譯器選項。 /GL 與所產生的二進位檔案的任何修改就必須重新編譯並連結來達成。

- [EDITBIN 命令列](editbin-command-line.md)

- [EDITBIN 選項](editbin-options.md)

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](c-cpp-build-tools.md)
