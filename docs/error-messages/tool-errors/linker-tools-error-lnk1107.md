---
title: 連結器工具錯誤 LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: c75966d9c6c22f1bd2123fb30282bb2bed467130
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991024"
---
# <a name="linker-tools-error-lnk1107"></a>連結器工具錯誤 LNK1107

檔案無效或損毀：無法讀取位置

此工具無法讀取檔案。 重新建立檔案。

如果您嘗試將以[/clr： noAssembly](../../build/reference/clr-common-language-runtime-compilation.md)或[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)建立的模組（.dll 或. .netmodule 副檔名）傳遞至連結器，也可能會發生 LNK1107;請改為傳遞 .obj 檔案。

如果您編譯下列範例：

```cpp
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

然後在命令列上指定**LINK LNK1107** ，您就會收到 LNK1107。  若要解決此錯誤，請改為指定**連結 LNK1107** 。
