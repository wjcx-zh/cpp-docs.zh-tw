---
title: 編譯器選項 |Microsoft 文件
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
ms.openlocfilehash: bea07361a292ee5e7cde99cedad2d5ac4c8a53aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374269"
---
# <a name="compiler-options"></a>編譯器選項

cl.exe 是工具，可控制 Microsoft Visual c + + (MSVC) C 和 c + + 編譯器和連結器。 cl.exe 可以只在支援 Microsoft Visual Studio for Windows 作業系統上執行。

> [!NOTE]  
> 您可以啟動這個工具只會從 Visual Studio 開發人員命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。 如需詳細資訊，請參閱[命令列上的建置 C/c + + 程式碼](../building-on-the-command-line.md)。

編譯器會產生通用物件檔案格式 (COFF) 物件檔 (.obj)。 連結器會產生可執行檔 (.exe) 或動態連結程式庫 (Dll)。

請注意，所有的編譯器選項是區分大小寫。 您可以使用正斜線 (`/`) 或破折號 (`-`) 指定編譯器選項。

若要編譯而不連結，請使用[/c](../../build/reference/c-compile-without-linking.md)選項。

## <a name="find-a-compiler-option"></a>尋找編譯器選項

若要尋找特定的編譯器選項，請參閱下列的清單：

- [依字母順序排列的編譯器選項](../../build/reference/compiler-options-listed-alphabetically.md)

- [依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>指定編譯器選項

每個編譯器選項的主題討論如何在開發環境中設定。 如需指定在開發環境以外的選項資訊，請參閱：

- [編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)

- [CL 命令檔](../../build/reference/cl-command-files.md)

- [CL 環境變數](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>相關的建置工具

[連結器選項](../../build/reference/linker-options.md)也會影響您的程式的建置方式。

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  
[快速編譯](../../build/reference/fast-compilation.md)  
[CL 叫用連結器](../../build/reference/cl-invokes-the-linker.md)  
