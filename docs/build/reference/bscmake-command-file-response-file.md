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
ms.openlocfilehash: 43f5a886dd41941a0675e31bc8c9d3f23c607023
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426234"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE 命令檔 (回應檔)

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

[BSCMAKE 參考](../../build/reference/bscmake-reference.md)
