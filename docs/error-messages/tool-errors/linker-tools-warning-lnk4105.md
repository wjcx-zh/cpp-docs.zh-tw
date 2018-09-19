---
title: 連結器工具警告 LNK4105 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4411421741cf8bf7c714a6322d58bd177e7e7270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024979"
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