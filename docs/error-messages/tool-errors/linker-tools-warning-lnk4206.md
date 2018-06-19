---
title: 連結器工具警告 LNK4206 |Microsoft 文件
ms.date: 12/05/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4206
dev_langs:
- C++
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0cb74776f307affb0455d972e27e594e6d06294
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300868"
---
# <a name="linker-tools-warning-lnk4206"></a>連結器工具警告 LNK4206

> 找不到; 先行編譯的類型資訊'*filename*' 未連結或覆寫; 如同沒有偵錯資訊般連結物件

*Filename*使用編譯的目的檔[/Yc](../../build/reference/yc-create-precompiled-header-file.md)、 未指定 LINK 命令中或已被覆寫。

這個警告的常見案例是.obj 檔以 /Yc 編譯時程式庫，而沒有從您的程式碼.obj 檔的符號參考。  在此情況下，連結器將無法使用 （或甚至看到）.obj 檔案。  在此情況下，您應該重新編譯您的程式碼，並使用[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)使用編譯的物件[/Yu](../../build/reference/yu-use-precompiled-header-file.md)。