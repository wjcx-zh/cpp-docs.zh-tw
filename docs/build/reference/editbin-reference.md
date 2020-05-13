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
ms.openlocfilehash: 266347de063b4e050cb032aa2d8d74e7934b8081
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328341"
---
# <a name="editbin-reference"></a>EDITBIN 參考

微軟 COFF 二進位檔編輯器(EDITBIN)。EXE) 修改常見物件檔案格式 (COFF) 二進位檔案。 您可以使用 EDITBIN 修改物件檔、執行檔和動態連結庫 (DLL)。

> [!NOTE]
> 只能從可視化工作室命令提示符啟動此工具。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

EDITBIN 不適用於使用[/GL](gl-whole-program-optimization.md)編譯器選項生成的檔。 任何修改二進位檔與 /GL 將必須通過重新編譯和連結來實現。

- [EDITBIN 命令列](editbin-command-line.md)

- [EDITBIN 選項](editbin-options.md)

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](c-cpp-build-tools.md)
