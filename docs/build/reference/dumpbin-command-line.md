---
title: DUMPBIN 命令列
ms.date: 11/04/2016
helpviewer_keywords:
- DUMPBIN program, command line
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
ms.openlocfilehash: 4f663a74fd57f52aa559270d61df4a130cf7e86f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440066"
---
# <a name="dumpbin-command-line"></a>DUMPBIN 命令列

若要執行 DUMPBIN，請使用下列語法：

```
DUMPBIN [options] files...
```

指定一或多個二進位檔案，以及控制資訊所需的任何選項。 DUMPBIN 會將資訊顯示為標準輸出。 您可以將它重新導向至檔案，或使用/OUT 選項來指定輸出的檔案名。

當您在檔案上執行 DUMPBIN 但未指定選項時，DUMPBIN 會顯示/SUMMARY 輸出。

當您在沒有任何其他命令列輸入的情況下輸入命令 `dumpbin`，DUMPBIN 會顯示使用方式語句來摘要說明其選項。

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](c-cpp-build-tools.md)<br/>
[DUMPBIN 參考](dumpbin-reference.md)
