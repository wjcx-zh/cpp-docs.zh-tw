---
title: CL 命令檔
description: MSVC 編譯器可讓您指定包含命令列選項的命令檔。
ms.date: 07/08/2020
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 6deab4b11dcc6c53beb5b4fa8b014a56020c3420
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180938"
---
# <a name="cl-command-files"></a>CL 命令檔

命令檔是包含編譯器選項和檔案名的文字檔。 它會提供您在[命令列](compiler-command-line-syntax.md)上輸入的選項，或使用[CL 環境變數](cl-environment-variables.md)來指定。 CL 會在 CL 環境變數中或在命令列上，接受編譯器命令檔做為引數。 與命令列或 CL 環境變數不同的是，您可以在命令檔中使用多行選項和檔案名。

當 CL 環境變數或命令列中出現命令檔案名時，會處理命令檔中的選項和檔案名。 不過，如果 **`/link`** 選項出現在命令檔中，則會將該行其餘部分的所有選項傳遞至連結器。 命令檔的後續程式列中的選項，以及命令檔叫用之後命令列上的選項，仍然會接受為編譯器選項。 如需選項順序如何影響其轉譯的詳細資訊，請參閱[CL 選項的順序](order-of-cl-options.md)。

命令檔不能包含 CL 命令。 每個選項都必須在同一行開始和結束;您不能使用反斜線 (**`\`**) 來結合兩行的選項。

命令檔是由位於 sign (**`@`**) 後面接著檔案名所指定。 檔案名可以指定絕對或相對路徑。

例如，如果下列命令位於名為 RESP 的檔案中：

```cmd
/Ot /link LIBC.LIB
```

您可以指定下列 CL 命令：

```cmd
CL /Ob2 @RESP MYAPP.C
```

CL 的命令如下所示：

```cmd
CL /Ob2 /Ot MYAPP.C /link LIBC.LIB
```

您可以在這裡看到命令列和命令檔命令如何有效結合。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[MSVC 編譯器選項](compiler-options.md)
