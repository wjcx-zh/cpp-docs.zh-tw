---
title: /IMPORTS (DUMPBIN)
ms.date: 11/04/2016
f1_keywords:
- /imports
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
ms.openlocfilehash: c8b0f88b38eb657fe4d3916ef0df13972e985cbe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291834"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

此選項會顯示 dll (兩者都以靜態方式連結並[延遲載入](linker-support-for-delay-loaded-dlls.md))，從每個這些 Dll 的匯入至可執行檔或 DLL 和所有個別的匯入。

選擇性`file`規格可讓您指定只有該 DLL 的匯入將會顯示。 例如: 

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>備註

此選項所顯示的輸出會類似[/exports](dash-exports.md)輸出。

只有[/HEADERS](headers.md) DUMPBIN 選項只適用於所產生的檔案上[/GL](gl-whole-program-optimization.md)編譯器選項。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](dumpbin-options.md)
