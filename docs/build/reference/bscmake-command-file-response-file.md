---
title: BSCMAKE 命令檔 (回應檔)
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
ms.openlocfilehash: 6a55fd616a00aeb3ade229bf7cff8220f86085b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295041"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE 命令檔 (回應檔)

> [!WARNING]
> 雖然 BSCMAKE 仍隨著 Visual Studio 安裝，IDE 已不再使用它。 從 Visual Studio 2008 起，瀏覽和符號資訊會自動儲存在方案資料夾的 SQL Server .sdf 檔案中。

您可以提供的命令檔中的命令列輸入部分或全部。 指定命令檔，請使用下列語法：

```
BSCMAKE @filename
```

允許只有一個命令檔。 您可以指定的路徑*filename*。 在前面*檔名*使用 at 符號 (**\@**)。 BSCMAKE 不採用擴充功能。 您可以指定額外*sbrfiles*之後在命令列*filename*。 命令檔是文字檔，其中包含 BSCMAKE 的相同順序的輸入，如同您會在命令列上指定它。 使用一或多個空格、 定位點或新行字元分隔的命令列引數。

下列命令會呼叫 BSCMAKE 使用的命令檔：

```
BSCMAKE @prog1.txt
```

以下是範例的命令檔：

```
/n /v /o main.bsc /El
/S (
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```

## <a name="see-also"></a>另請參閱

[BSCMAKE 參考](bscmake-reference.md)
