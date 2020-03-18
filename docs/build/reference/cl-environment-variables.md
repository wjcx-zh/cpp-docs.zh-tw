---
title: CL 環境變數
ms.date: 06/06/2019
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 4d6b1982b1e544459a025d6cb7bee75666e7130e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440254"
---
# <a name="cl-environment-variables"></a>CL 環境變數

CL 工具使用下列環境變數：

- CL 和 \_CL_ （如果有定義的話）。 CL 工具會將 CL 環境變數中定義的選項和引數加到命令列引數，並在處理之前附加 \_CL_ 中定義的選項和引數。

- 包含，它必須指向 Visual Studio 安裝的 \include 子目錄。

- LIBPATH，它會指定目錄，以搜尋[#using](../../preprocessor/hash-using-directive-cpp.md)所參考的中繼資料檔案。 如需 LIBPATH 的詳細資訊，請參閱[#using](../../preprocessor/hash-using-directive-cpp.md)。

您可以使用下列語法來設定 CL 或 \_CL_ 環境變數：

> SET CL = [[*選項*] .。。[*file*] ...][/link*連結-選擇*...]\
> 設定 \_CL\_= [[*選項*] .。。[*file*] ...][/link*連結-選擇*...]

如需 CL 和 \_CL_ 環境變數之引數的詳細資訊，請參閱[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)。

您可以使用這些環境變數來定義您最常使用的檔案和選項。 然後使用命令列，針對特定目的，將更多檔案和選項提供給 CL。 CL 和 \_CL_ 環境變數限制為1024個字元（命令列輸入限制）。

您無法使用[/d](d-preprocessor-definitions.md)選項來定義使用等號（ **=** ）的符號。 相反地，您可以使用數位記號（ **#** ）進行等號。 如此一來，您就可以使用 CL 或 \_CL_ 環境變數，以明確的值定義預處理器常數，例如，`/DDEBUG#1` 來定義 `DEBUG=1`。

如需相關資訊，請參閱[設定環境變數](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="examples"></a>範例

下列命令是設定 CL 環境變數的範例：

> SET CL =/Zp2/Ox/I\INCLUDE\MYINCLS \LIB\BINMODE。OBJ

設定 CL 環境變數時，如果您在命令列中輸入 `CL INPUT.C`，有效的命令會變成：

> CL/Zp2/Ox/I\INCLUDE\MYINCLS \LIB\BINMODE。OBJ 輸入。C

下列範例會造成一般 CL 命令編譯原始程式檔 FILE1.c 和 FILE2.c，然後再連結物件檔案 FILE1.obj、FILE2.obj 和 FILE3.obj：

> SET CL = FILE1。C FILE2。C
> 設定 \_CL_ = FILE3。OBJ
> CL

這些環境變數會讓呼叫 CL 的效果與下列命令列相同：

> CL FILE1。C FILE2。C FILE3。OBJ

## <a name="see-also"></a>另請參閱

[設定編譯器選項](compiler-command-line-syntax.md) \
[MSVC 編譯器選項](compiler-options.md)
