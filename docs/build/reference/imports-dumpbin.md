---
title: -IMPORTS (DUMPBIN) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /imports
dev_langs:
- C++
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5b3b1e3a74fea278bc142d02f793308b6b0e054
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713566"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

此選項會顯示 dll (兩者都以靜態方式連結並[延遲載入](../../build/reference/linker-support-for-delay-loaded-dlls.md))，從每個這些 Dll 的匯入至可執行檔或 DLL 和所有個別的匯入。

選擇性`file`規格可讓您指定只有該 DLL 的匯入將會顯示。 例如: 

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>備註

此選項所顯示的輸出會類似[/exports](../../build/reference/dash-exports.md)輸出。

只有[/HEADERS](../../build/reference/headers.md) DUMPBIN 選項只適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](../../build/reference/dumpbin-options.md)