---
title: 連結器工具錯誤 LNK1107 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1107
dev_langs:
- C++
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73a1643d10ea9adc6ac6979eb2de023593ba8d01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060703"
---
# <a name="linker-tools-error-lnk1107"></a>連結器工具錯誤 LNK1107

檔案無效或損毀： 無法讀取位置

此工具無法讀取檔案。 重新建立檔案。

如果您嘗試傳遞模組也會發生 LNK1107 (使用建立的.dll 或.netmodule 副檔名[/clr:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md)或是[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)) 連結器傳遞.obj 檔改為。

如果您編譯下列範例：

```
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

然後指定**link> LNK1107.dll**命令列中，您會看到 LNK1107。  若要解決此錯誤，指定**link> LNK1107.obj**改。