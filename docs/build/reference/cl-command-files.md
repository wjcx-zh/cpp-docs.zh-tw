---
title: CL 命令檔
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 1dc2d6bffe4d0681a04b875383215a0bbfc1a720
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440260"
---
# <a name="cl-command-files"></a>CL 命令檔

命令檔是一個文字檔，其中包含您在[命令列](compiler-command-line-syntax.md)上輸入或使用[CL 環境變數](cl-environment-variables.md)指定的選項和檔案名。 CL 接受編譯器命令檔做為 CL 環境變數或命令列中的引數。 與命令列或 CL 環境變數不同的是，命令檔可讓您使用多行選項和檔名。

命令檔中的選項和檔案名會根據 CL 環境變數或命令列中的命令檔案名位置進行處理。 不過，如果在命令檔中出現/link 選項，則會將該行其餘部分的所有選項傳遞至連結器。 命令檔的後續程式列中的選項，以及命令檔叫用後命令列上的選項，仍然會當做編譯器選項接受。 如需選項順序如何影響其轉譯的詳細資訊，請參閱[CL 選項的順序](order-of-cl-options.md)。

命令檔不能包含 CL 命令。 每個選項都必須在同一行開始和結束;您不能使用反斜線（ **\\** ）結合兩行的選項。

命令檔是由 @ 符號（ **\@** ）指定，後面接著檔案名;檔案名可以指定絕對或相對路徑。

例如，如果下列命令位於名為 RESP 的檔案中：

```
/Og /link LIBC.LIB
```

您可以指定下列 CL 命令：

```
CL /Ob2 @RESP MYAPP.C
```

CL 的命令如下所示：

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

請注意，命令列和命令檔命令會有效率地結合。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[MSVC 編譯器選項](compiler-options.md)
