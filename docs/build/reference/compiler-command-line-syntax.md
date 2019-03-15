---
title: MSVC 編譯器的命令列語法
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 5cee76d5c053dbcfef33a191dc38a958338e4a82
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821488"
---
# <a name="compiler-command-line-syntax"></a>編譯器命令列語法

CL 命令列使用下列語法：

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

下表描述 CL 命令的輸入。

|進入|意義|
|-----------|-------------|
|*option*|一或多個[CL 選項](compiler-options.md)。 請注意，所有選項都會都套用至所有指定的原始程式檔。 選項會指定正斜線 （/） 或破折號 （-）。 如果選項需要引數，此選項的描述文件，是否允許選項和引數之間的空格。 （除了 /HELP 選項） 的選項名稱會區分大小寫。 請參閱[CL 選項的順序](order-of-cl-options.md)如需詳細資訊。|
|`file`|一或多個原始程式檔、.obj 檔案或程式庫的名稱。 CL 編譯原始程式檔，並將.obj 檔案和程式庫的名稱傳遞給連結器。 請參閱[CL 檔名語法](cl-filename-syntax.md)如需詳細資訊。|
|*lib*|一或多個程式庫名稱。 CL 會將這些名稱傳遞給連結器。|
|*command-file*|包含多個選項和檔名的檔案。 請參閱[CL 命令檔](cl-command-files.md)如需詳細資訊。|
|*link-opt*|一或多個[MSVC 連結器選項](linker-options.md)。 CL 會將這些選項給連結器。|

只要在命令列上的字元數目不超過 1024 個，取決於作業系統的限制，您可以指定任意數目的選項、 檔名，以及程式庫名稱。

Cl.exe 的傳回值的詳細資訊，請參閱[的 cl.exe 的傳回值](return-value-of-cl-exe.md)。

> [!NOTE]
>  1024 個字元的命令列輸入的限制不保證維持不變的 Windows 未來版本中。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)
