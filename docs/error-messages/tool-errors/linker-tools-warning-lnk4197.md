---
title: 連結器工具警告 LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 0abad1b98ff4782f077312752603ec17fd611c12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527331"
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