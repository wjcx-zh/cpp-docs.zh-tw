---
title: 連結器工具錯誤 LNK1107 |Microsoft 文件
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
ms.openlocfilehash: fee2105cb0c12287cd2b47636f0e47011854a608
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298346"
---
# <a name="linker-tools-error-lnk1107"></a>連結器工具錯誤 LNK1107
檔案無效或損毀： 無法讀取位置  
  
 此工具無法讀取檔案。 重新建立檔案。  
  
 如果您嘗試將模組也會發生 LNK1107 (.dll 或.netmodule 延伸模組，以建立[/clr:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md)或[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)) 至連結器; 傳遞的.obj 檔案改為。  
  
 如果您將編譯下列的範例：  
  
```  
// LNK1107.cpp  
// compile with: /clr /LD  
public ref class MyClass {  
public:  
   void Test(){}  
};  
```  
  
 然後指定**連結 LNK1107.dll**命令列中，您會收到 LNK1107。  若要解決此錯誤，指定**連結 LNK1107.obj**改為。