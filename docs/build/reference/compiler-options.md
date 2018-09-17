---
title: 編譯器選項 |Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler
- x86 Visual C++ compiler
- ARM Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 76ab322dc4573863a30092b296e87e90c41619ab
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716206"
---
# <a name="compiler-options"></a>編譯器選項

cl.exe 是控制的 Microsoft Visual c + + (MSVC) C 和 c + + 編譯器和連結器工具。 cl.exe 可以只在支援 Microsoft Visual Studio 的 Windows 作業系統上執行。

> [!NOTE]
> 您可以啟動此工具只能從 Visual Studio 開發人員命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。 如需詳細資訊，請參閱 <<c0> [ 命令列上的建置 C/c + + 程式碼](../building-on-the-command-line.md)。

編譯器會產生通用物件檔案格式 (COFF) 目的檔 (.obj)。 連結器會產生可執行檔 (.exe) 或動態連結程式庫 (Dll)。

請注意，所有的編譯器選項是區分大小寫。 您可以使用正斜線 (`/`) 或破折號 (`-`) 指定編譯器選項。

若要編譯而不要連結，使用[/c](../../build/reference/c-compile-without-linking.md)選項。

## <a name="find-a-compiler-option"></a>尋找編譯器選項

若要尋找特定的編譯器選項，請參閱下列清單之一：

- [依字母順序排列的編譯器選項](../../build/reference/compiler-options-listed-alphabetically.md)

- [依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>指定編譯器選項

每個編譯器選項的主題討論如何在開發環境中設定。 開發環境外部指定選項的資訊，請參閱：

- [編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)

- [CL 命令檔](../../build/reference/cl-command-files.md)

- [CL 環境變數](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>相關的建置工具

[連結器選項](../../build/reference/linker-options.md)也會影響您的程式的建置方式。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[快速編譯](../../build/reference/fast-compilation.md)<br/>
[CL 叫用連結器](../../build/reference/cl-invokes-the-linker.md)
