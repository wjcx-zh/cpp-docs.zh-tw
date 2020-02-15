---
title: DUMPBIN 選項
description: Microsoft DUMPBIN 公用程式命令列選項的參考指南。
ms.date: 02/09/2020
f1_keywords:
- dumpbin
helpviewer_keywords:
- DUMPBIN program, options
ms.assetid: 563b696e-7599-4480-94b9-014776289ec8
ms.openlocfilehash: 98a4fd221d66b93f945667deadaba3180f8d3e66
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257724"
---
# <a name="dumpbin-options"></a>DUMPBIN 選項

選項包含*選項規範*，也就是破折號（`-`）或正斜線（`/`），後面接著選項的名稱。 選項名稱不可以是縮寫。 有些選項會採用冒號（`:`）後面指定的引數。 選項規格中不允許有空格或索引標籤。 在命令列上使用一或多個空格或索引標籤來分隔選項規格。 選項名稱及其關鍵字或檔案名引數不區分大小寫。 大部分的選項都適用于所有二進位檔案，但少數只適用于特定類型的檔案。 根據預設，DUMPBIN 會將資訊傳送至標準輸出。 使用[/out](out-dumpbin.md)選項，將輸出傳送至檔案。

## <a name="options-list"></a>選項清單

DUMPBIN 有下列選項：

- [/ALL](all.md)

- [/ARCHIVEMEMBERS](archivemembers.md)

- [/CLRHEADER](clrheader.md)

- [/DEPENDENTS](dependents.md)

- [/DIRECTIVES](directives.md)

- [/DISASM\[： {BYTES\|NOBYTES}\]](disasm.md)

- [/ERRORREPORT： {NONE |提示 |佇列 |SEND}](errorreport-dumpbin-exe.md) （已淘汰）

- [/EXPORTS](dash-exports.md)

- [/FPO](fpo.md)

- [/HEADERS](headers.md)

- [/IMPORTS\[： filename\]](imports-dumpbin.md)

- [/LINENUMBERS](linenumbers.md)

- [/LINKERMEMBER\[： {1 | 2}\]](linkermember.md)

- [/LOADCONFIG](loadconfig.md)

- [/NOPDB](nopdb.md)

- [/OUT： filename](out-dumpbin.md)

- [/PDATA](pdata.md)

- [/PDBPATH\[： VERBOSE\]](pdbpath.md)

- [/RANGEE： vaMin\[、vaMax\]](range.md)

- [/RAWDATA\[： {NONE\|1\|2\|4\|8}\[，#\]\]](rawdata.md)

- [/RELOCATIONS](relocations.md)

- [/SECTION：名稱](section-dumpbin.md)

- [/SUMMARY](summary.md)

- [/SYMBOLS](symbols.md)

- [/TLS](tls.md)

若要列出 DUMPBIN 在命令列上支援的選項，請使用 **/？** 選項。

## <a name="see-also"></a>另請參閱

[其他 MSVC build 工具](c-cpp-build-tools.md)\
[DUMPBIN 命令列](dumpbin-command-line.md)\
[DUMPBIN 參考](dumpbin-reference.md)
