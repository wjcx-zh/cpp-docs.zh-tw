---
title: CL 環境變數
ms.date: 06/06/2019
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 0f7930728ef1bf6bea50c4388d52d30c569a8795
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821529"
---
# <a name="cl-environment-variables"></a>CL 環境變數

CL 工具使用下列環境變數：

- CL 和\_CL_，如果定義。 CL 工具前面加上選項和命令列引數，CL 環境變數中定義的引數，並將附加選項和引數中所定義\_CL_，處理之前。

- 包含必須指向 Visual Studio 安裝的 \include 子目錄。

- LIBPATH，指定要搜尋參考的中繼資料檔案的目錄[#using](../../preprocessor/hash-using-directive-cpp.md)。 如需 LIBPATH 的詳細資訊，請參閱[#using](../../preprocessor/hash-using-directive-cpp.md)。

您可以設定 CL 或\_CL_ 環境變數，使用下列語法：

> 設定 CL = [[*選項*]...[*檔案*]...][/ link>*連結-opt* ...] \
> 設定\_CL\_= [[*選項*]...[*檔案*]...][/ link>*連結-opt* ...]

如需有關加入 CL 引數及\_CL_ 環境變數，請參閱[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)。

您可以使用這些環境變數來定義的檔案與您最常使用的選項。 然後使用命令列來加入 CL 提供更多的檔案和選項，針對特定用途。 CL 和\_CL_ 環境變數僅限於 1024年個字元 （命令列輸入限制）。

您無法使用[/D](d-preprocessor-definitions.md)選項來定義符號使用等號 ( **=** )。 相反地，您可以使用數字符號 ( **#** ) 將等號。 如此一來，您可以使用 CL 或\_CL_ 環境變數來定義明確的值與前置處理器常數 — 例如，`/DDEBUG#1`定義`DEBUG=1`。

如需相關資訊，請參閱[設定環境變數](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="examples"></a>範例

下列命令是設定 CL 環境變數的範例：

> 設定 CL = / Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE。OBJ

當 CL 環境變數設定時，如果您輸入`CL INPUT.C`在命令列中，有效的命令會變成：

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C

下列範例會造成一般 CL 命令編譯原始程式檔 FILE1.c 和 FILE2.c，然後再連結物件檔案 FILE1.obj、FILE2.obj 和 FILE3.obj：

> 設定 CL = FILE1。C FILE2。C \
> SET \_CL_=FILE3.OBJ \
> CL

這些環境變數進行的呼叫，以 CL 有下列的命令列相同的效果：

> CL FILE1。C FILE2。C FILE3。OBJ

## <a name="see-also"></a>另請參閱

[設定編譯器選項](compiler-command-line-syntax.md) \
[MSVC 編譯器選項](compiler-options.md)
