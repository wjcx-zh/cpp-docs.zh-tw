---
title: 編譯器和連結器中的 Unicode 支援
ms.date: 12/15/2017
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
helpviewer_keywords:
- Unicode, Visual C++
ms.openlocfilehash: 420b01263320cf86df3f99da4523cc2b8bb4d4b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168833"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>編譯器和連結器中的 Unicode 支援

大部分的C++ Visual build 工具都支援 Unicode 輸入和輸出。

## <a name="filenames"></a>檔案名稱

在命令列或編譯器指示詞（例如 `#include`）中指定的檔案名可能包含 Unicode 字元。

## <a name="source-code-files"></a>原始程式碼檔

識別碼、宏、字串和字元常值和批註中都支援 Unicode 字元。  也支援通用字元名稱。

Unicode 可以輸入至原始程式碼檔案中的下列編碼方式：

- UTF-16 小數位序，包含或不含位順序標記（BOM）

- UTF-16 big endian （含或不含 BOM）

- UTF-8 with BOM

## <a name="output"></a>輸出

在編譯期間，編譯器會將診斷輸出至以 UTF-16 表示的主控台。  可在主控台中顯示的字元取決於主控台視窗屬性。  重新導向至檔案的編譯器輸出會在目前的 ANSI 主控台字碼頁中。

## <a name="linker-response-files-and-def-files"></a>連結器回應檔和。DEF 檔案

回應檔和 DEF 檔案可以是具有 BOM 的 UTF-16 或 ANSI。

## <a name="asm-and-cod-dumps"></a>.asm 和。

基於與 MASM 的相容性，.asm 和. # 傾印預設為 ANSI。 使用[/FAu](fa-fa-listing-file.md)來輸出 utf-8。 請注意，如果您指定 **/FAs**，則只會直接列印混合的來源，而且可能看起來不正確，例如，如果原始程式碼是 utf-8，而且您未指定 **/FAsu**。

## <a name="see-also"></a>另請參閱

[從命令列使用 MSVC 工具組](../building-on-the-command-line.md)
