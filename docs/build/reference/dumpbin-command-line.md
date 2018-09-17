---
title: DUMPBIN 命令列 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dumpbin
dev_langs:
- C++
helpviewer_keywords:
- DUMPBIN program, command line
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9028cebd7c75bb37bbfa958186ebb2e5d206094
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724761"
---
# <a name="dumpbin-command-line"></a>DUMPBIN 命令列

若要執行 DUMPBIN，使用下列語法：

```
DUMPBIN [options] files...
```

指定一或多個二進位檔案，以及任何所需選項來控制的資訊。 DUMPBIN 至標準輸出，顯示的資訊。 您可以將它重新導向至檔案，或是使用 /OUT 選項指定輸出檔案名稱。

DUMPBIN 當您在檔案上執行 DUMPBIN 不指定選項時，會顯示沒有指定 /SUMMARY 輸出。

當您輸入命令`dumpbin`而無需任何其他命令列的輸入，DUMPBIN 顯示摘要說明其選項的使用方式陳述式。

## <a name="see-also"></a>另請參閱

[C/C++ 建置工具](../../build/reference/c-cpp-build-tools.md)<br/>
[DUMPBIN 參考](../../build/reference/dumpbin-reference.md)