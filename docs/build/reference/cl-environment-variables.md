---
title: CL 環境變數
ms.date: 05/06/2019
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 620ec386e06b1a0eed91c94e9b2b891d9955fd00
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217629"
---
# <a name="cl-environment-variables"></a>CL 環境變數

CL 工具使用下列環境變數：

- CL 和\_CL\_，如果已定義。 CL 工具前面加上選項和引數的命令列引數，CL 環境變數中定義，並將附加選項和引數中定義\_CL\_，處理之前。

- 包含必須指向 Visual Studio 安裝的 \include 子目錄。

- LIBPATH，指定要搜尋參考的中繼資料檔案的目錄[#using](../../preprocessor/hash-using-directive-cpp.md)。 如需 LIBPATH 的詳細資訊，請參閱 `#using`。

您可以設定 CL 或\_CL\_環境變數，使用下列語法：

> 設定 CL = [[*選項*]...[*檔案*]...][/ link>*連結-opt* ...]設定\_CL\_= [[*選項*]...[*檔案*]...][/ link>*連結-opt* ...]

如需有關加入 CL 引數及\_CL\_環境變數，請參閱[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)。

您可以使用這些環境變數來定義您最常使用的檔案與選項，並使用命令列來定義用於特定用途的特定檔案和選項。 CL 和\_CL\_環境變數僅限於 1024年個字元 （命令列輸入限制）。

您無法使用 /D 選項來定義使用等號 (=) 的符號。 您可以將等號取代為數字符號 (#)。 如此一來，您可以使用 CL 或\_CL\_環境變數來定義明確的值與前置處理器常數 — 例如`/DDEBUG#1`來定義`DEBUG=1`。

如需相關資訊，請參閱[設定環境變數](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="examples"></a>範例

以下是設定 CL 環境變數的範例：

> 設定 CL = / Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE。OBJ

當此環境變數設定時，如果您輸入`CL INPUT.C`在命令列中，這是有效的命令：

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C

下列範例會造成一般 CL 命令編譯原始程式檔 FILE1.c 和 FILE2.c，然後再連結物件檔案 FILE1.obj、FILE2.obj 和 FILE3.obj：

> SET CL=FILE1.C FILE2.C SET \_CL\_=FILE3.OBJ CL

這個範例具有與下列命令列相同的效果：

> CL FILE1。C FILE2。C FILE3。OBJ

## <a name="see-also"></a>另請參閱

[設定編譯器選項](compiler-command-line-syntax.md)<br/>
[MSVC 編譯器選項](compiler-options.md)
