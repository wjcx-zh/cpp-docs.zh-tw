---
title: 連結器工具警告 LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 880c8519a530f492d0c322575a1386af8a7d0187
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475581"
---
# <a name="linker-tools-warning-lnk4105"></a>連結器工具警告 LNK4105

使用選項 'option'; 指定任何引數忽略選項

只會發生這個警告時[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項設定。 如果未指定目錄則使用此選項時，連結器會忽略此選項，並會產生這則警告訊息。

如果您不需要覆寫現有的環境的文件庫設定，請從連結器命令列移除 /LIBPATH 選項。 如果您想要用於程式庫中的其他搜尋路徑，指定下列 /LIBPATH 選項的替代路徑。

## <a name="example"></a>範例

```
link /libpath:c:\filepath\lib bar.obj
```

會指示連結器所需的程式庫中搜尋`c:\filepath\lib`之前在預設位置中搜尋。