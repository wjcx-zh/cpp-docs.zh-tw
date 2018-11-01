---
title: 連結器工具警告 LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: dc81df89609f59834c8a3271dd64f3b99b281f90
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613628"
---
# <a name="linker-tools-warning-lnk4206"></a>連結器工具警告 LNK4206

> 找不到; 的先行編譯的類型資訊'*filename*' 未連結或覆寫; 如同沒有偵錯資訊般連結物件

*檔名*使用編譯的目的檔[/Yc](../../build/reference/yc-create-precompiled-header-file.md)、 未指定在 [連結] 命令，或已被覆寫。

這個警告的常見案例是.obj 檔以 /Yc 編譯時在程式庫，而沒有從您的程式碼.obj 檔的符號參考。  在此情況下，連結器會使用 （或甚至看到）.obj 檔案。  在此情況下，您應該重新編譯程式碼，並使用[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)使用編譯的物件[/Yu](../../build/reference/yu-use-precompiled-header-file.md)。