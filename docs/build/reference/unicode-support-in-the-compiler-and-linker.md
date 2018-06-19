---
title: 編譯器和連結器中的 Unicode 支援 |Microsoft 文件
ms.custom: ''
ms.date: 12/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
dev_langs:
- C++
helpviewer_keywords:
- Unicode, Visual C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec0b84cd62f3fcca378ab55de16006925e685b37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376188"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>編譯器和連結器中的 Unicode 支援

大部分的 Visual c + + 建置工具支援 Unicode 輸入和輸出。

## <a name="filenames"></a>檔案名稱

在命令列上或編譯器指示詞指定的檔名 (例如`#include`) 可能包含 Unicode 字元。

## <a name="source-code-files"></a>原始程式檔

在識別項、 巨集、 字串和字元常值和註解中支援 Unicode 字元。  也支援通用字元名稱。

Unicode 可以輸入下列編碼中的原始程式碼檔：

- Utf-16 很少位元組由小到大位元組順序標示 (BOM) 不論

- 使用或不具有 BOM utf-16 big endian

- Utf-8 有 BOM

## <a name="output"></a>輸出

在編譯期間，編譯器會輸出診斷，以 utf-16 主控台。  在您的主控台可顯示的字元取決於主控台視窗的內容。  編譯器輸出重新導向至檔案是以目前的 ANSI 主控台字碼頁。

## <a name="linker-response-files-and-def-files"></a>連結器回應檔和。DEF 檔案

回應檔案和.DEF 檔可以是任一個 utf-16 BOM，或 ANSI。

## <a name="asm-and-cod-dumps"></a>.asm 和.cod 傾印

.asm 和.cod 傾印的 ANSI 預設了與 MASM 的相容性。 使用[/FAu](../../build/reference/fa-fa-listing-file.md)輸出 utf-8。 請注意，如果您指定 **/FAs**，混合的原始程式碼會直接列印和看起來可能亂碼，例如，如果原始碼為 utf-8，而您並未指定 **/fasu 時**。

## <a name="see-also"></a>另請參閱

[在命令列上建置 C/C++ 程式碼](../../build/building-on-the-command-line.md)