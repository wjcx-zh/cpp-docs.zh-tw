---
title: MSVC 編譯器命令列語法
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 6a56474b537d78a3d0bea8a74d9082007cd2e295
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320538"
---
# <a name="compiler-command-line-syntax"></a>編譯器命令列語法

CL 命令列使用以下文法:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

下表描述了對 CL 命令的輸入。

|項目|意義|
|-----------|-------------|
|*選項*|一個或多個[CL 選項](compiler-options.md)。 請注意,所有選項都適用於所有指定的源檔。 選項由前斜杠 (/) 或破折號 (-) 指定。 如果選項採用參數,則該選項的說明將記錄選項和參數之間是否允許空格。 選項名稱(/HELP 選項除外)區分大小寫。 關於詳細資訊[,請參考 CL 選項的順序](order-of-cl-options.md)。|
|`file`|一個或多個源檔案、.obj 檔案或庫的名稱。 CL 編譯源檔並將 .obj 檔案和庫的名稱傳遞給連結器。 關於詳細資訊[,請參閱 CL 檔名語法](cl-filename-syntax.md)。|
|*自由*|一個或多個庫名稱。 CL 將這些名稱傳遞給連結器。|
|*指令檔案*|包含多個選項和檔名的檔。 有關詳細資訊,請參閱[CL 命令檔](cl-command-files.md)。|
|*連結選取*|一個或多個[MSVC 連結器選項](linker-options.md)。 CL將這些選項傳遞給連結器。|

只要命令列上的字元數不超過 1024,即作業系統規定的限制,就可以指定任意數量的選項、檔名和庫名。

有關 cl.exe 的傳回值的資訊,請參閱[cl.exe 的傳回值](return-value-of-cl-exe.md)。

> [!NOTE]
> 在 Windows 的未來版本中,不能保證 1024 個字元的命令行輸入限制保持不變。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)
