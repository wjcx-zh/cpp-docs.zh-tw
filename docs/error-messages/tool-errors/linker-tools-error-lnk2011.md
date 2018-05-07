---
title: 連結器工具錯誤 LNK2011 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2011
dev_langs:
- C++
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f60dce4cb260c670f5ee82aa88b9f106f3f14e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2011"></a>連結器工具錯誤 LNK2011
先行編譯的物件; 中沒有被連結映像可能無法執行  
  
 如果您使用先行編譯標頭時，連結要求的所有物件檔案建立先行編譯標頭必須連結中。 如果您有原始程式檔，您用來產生其他原始程式檔使用的先行編譯標頭，您現在必須包含與先行編譯標頭一起建立的物件檔。  
  
 比方說，如果您編譯檔案，稱為 STUB.cpp 來建立其他原始程式檔使用的先行編譯標頭，您必須連結 stub.obj 或您會收到這個錯誤。 在下列的命令列中，一行一個用於建立先行編譯標頭 COMMON.pch 可搭配 PROG1.cpp 和 PROG2.cpp 二及第三行中。 STUB.cpp 只包含的檔案`#include`線條 (相同`#include`如 PROG1.cpp 及 PROG2.cpp 行)，僅用於產生先行編譯標頭。 中的最後一行，STUB.obj 中必須連結以避免 LNK2011。  
  
```  
cl /c /Yccommon.h stub.cpp  
cl /c /Yucommon.h prog1.cpp  
cl /c /Yucommon.h prog2.cpp  
link /out:prog.exe stub.obj prog1.obj prog2.obj  
```