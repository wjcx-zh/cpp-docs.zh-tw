---
title: CL 環境變數 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74ac2cb1ad28720cc45aec4f6258d1152a55e861
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722731"
---
# <a name="cl-environment-variables"></a>CL 環境變數

CL 工具使用下列環境變數：

- CL 和\_CL\_，如果已定義。 CL 工具前面加上選項和引數的命令列引數，CL 環境變數中定義，並將附加選項和引數中定義\_CL\_，處理之前。

- INCLUDE，必須指向 Visual C++ 安裝的 \include 子目錄。

- LIBPATH，指定要搜尋參考的中繼資料檔案的目錄[#using](../../preprocessor/hash-using-directive-cpp.md)。 如需 LIBPATH 的詳細資訊，請參閱 `#using`。

您可以設定 CL 或\_CL\_環境變數，使用下列語法：

> 設定 CL = [[*選項*]...[*檔案*]...][/ link>*連結-opt* ...]設定\_CL\_= [[*選項*]...[*檔案*]...][/ link>*連結-opt* ...]

如需有關加入 CL 引數及\_CL\_環境變數，請參閱[編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)。

您可以使用這些環境變數來定義您最常使用的檔案與選項，並使用命令列來定義用於特定用途的特定檔案和選項。 CL 和\_CL\_環境變數僅限於 1024年個字元 （命令列輸入限制）。

您無法使用 /D 選項來定義使用等號 (=) 的符號。 您可以將等號取代為數字符號 (#)。 如此一來，您可以使用 CL 或\_CL\_環境變數來定義明確的值與前置處理器常數 — 例如`/DDEBUG#1`來定義`DEBUG=1`。

如需相關資訊，請參閱[設定環境變數](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="examples"></a>範例

以下是設定 CL 環境變數的範例：

> 設定 CL = / Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE。OBJ

當此環境變數設定時，如果您輸入`CL INPUT.C`在命令列中，這是有效的命令：

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE。OBJ 輸入。C

下列範例會造成一般 CL 命令編譯原始程式檔 FILE1.c 和 FILE2.c，然後再連結物件檔案 FILE1.obj、FILE2.obj 和 FILE3.obj：

> 設定 CL = FILE1。C FILE2。C 組\_CL\_= FILE3。OBJ CL

這個範例具有與下列命令列相同的效果：

> CL FILE1。C FILE2。C FILE3。OBJ

## <a name="see-also"></a>另請參閱

[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)
