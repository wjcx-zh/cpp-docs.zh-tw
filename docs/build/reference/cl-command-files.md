---
title: CL 命令檔 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8458462304a9b739c61997505724d21bb56763f6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708665"
---
# <a name="cl-command-files"></a>CL 命令檔

命令檔是包含選項和檔案名稱，否則您會在輸入的文字檔[命令列](../../build/reference/compiler-command-line-syntax.md)或使用指定[CL 環境變數](../../build/reference/cl-environment-variables.md)。 CL 可以接受做為引數在 CL 環境變數，或在命令列編譯器的命令檔。 與命令列或 CL 環境變數不同的是，命令檔可讓您使用多行選項和檔名。

根據位置命令檔名稱在 CL 環境變數，或在命令列上的處理選項和命令檔中的檔案名稱。 不過，如果 /link 選項出現在 命令檔，在其餘的列上的所有選項的動作就會都傳遞至連結器。 編譯器選項，仍接受後續行命令檔中所列的選項和命令列上的命令檔引動過程後的選項。 如需有關選項的順序如何影響其解譯的詳細資訊，請參閱[CL 選項的順序](../../build/reference/order-of-cl-options.md)。

命令檔不能包含 CL 命令。 每個選項必須開始和結束的同一行;您無法使用反斜線 (**\\**) 來結合跨越兩行的選項。

所指定的命令檔 at 符號 (**\@**) 後面接著檔案名稱; 檔案名稱可以指定絕對或相對路徑。

比方說，如果是名為 回應檔案中的下列命令：

```
/Og /link LIBC.LIB
```

指定下列 CL 命令：

```
CL /Ob2 @RESP MYAPP.C
```

CL 命令如下所示：

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

請注意命令列] 和 [命令檔命令會有效地結合。

## <a name="see-also"></a>另請參閱

[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)