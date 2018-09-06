---
title: 連結器工具警告 LNK4197 |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4197
dev_langs:
- C++
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55044ce511e2584e2859b7e8a8d723cbe0976105
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894482"
---
# <a name="linker-tools-warning-lnk4197"></a>連結器工具警告 LNK4197

> 匯出 '*exportname*' 指定了多次; 使用第一個規格

在多個指定的匯出和不同的方式。 連結器會使用第一個規格，並忽略其餘部分。

如果您重建 C 執行階段程式庫，您可以忽略此訊息。

如果匯出指定完全相同的方式很多次，則連結器不會發出警告。

例如，在.def 檔的下列內容會導致此警告：

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 指定相同的匯出都在命令列上 (透過匯出:) 和.def 檔案中。

2. 相同的匯出會列出兩次.def 檔案中有不同的屬性。