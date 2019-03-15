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
ms.openlocfilehash: 71458ab345670c0a5715576a7da80c4e6ff2955b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807497"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>編譯器和連結器中的 Unicode 支援

大部分的 Visual c + + 建置工具支援 Unicode 輸入和輸出。

## <a name="filenames"></a>檔案名稱

在命令列上或編譯器指示詞中指定的檔案名稱 (例如`#include`) 可能包含 Unicode 字元。

## <a name="source-code-files"></a>原始程式碼檔

在識別項、 巨集、 字串和字元常值和註解，都支援 Unicode 字元。  也支援通用字元名稱。

Unicode 可以輸入下列編碼方式中的原始程式碼檔案：

- Utf-16 位元組由小到大和位元組順序標記 (BOM)

- Utf-16 big endian 使用或不加 BOM

- Bom 的 utf-8

## <a name="output"></a>輸出

在編譯期間，編譯器會輸出到主控台以 utf-16 的診斷。  可以在您的主控台中顯示的字元取決於主控台視窗的內容。  編譯器輸出重新導向至檔案是目前的 ANSI 主控台字碼頁。

## <a name="linker-response-files-and-def-files"></a>連結器回應檔和。DEF 檔

回應檔和 DEF 檔案可以是 utf-16 BOM，或 ANSI。

## <a name="asm-and-cod-dumps"></a>.asm 和.cod dumps

.asm 和.cod dumps 是以 ANSI 預設會針對與 MASM 相容。 使用[/FAu](fa-fa-listing-file.md)輸出 utf-8。 請注意，如果您指定 **/FAs**，會直接列印混合的原始程式碼，並可能看起來像亂碼，例如，如果原始程式碼是 utf-8，而您並未指定 **/fasu 時**。

## <a name="see-also"></a>另請參閱

[使用 MSVC 工具組，從命令列](../building-on-the-command-line.md)