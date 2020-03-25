---
title: 連結器工具警告 LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 92702864a00455e4b70f00dfc9988bfb754e2e64
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183276"
---
# <a name="linker-tools-warning-lnk4197"></a>連結器工具警告 LNK4197

> 已多次指定匯出 '*exportname*';使用第一個規格

匯出是以多種和不同的方式指定。 連結器會使用第一個規格，並忽略其餘的。

如果您要重建 C 執行時間程式庫，可以忽略此訊息。

如果以相同方式多次指定匯出，連結器將不會發出警告。

例如，下列 .def 檔案的內容會導致此警告：

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 在命令列上指定相同的匯出（透過匯出：）和 .def 檔案中的和。

2. 相同的匯出會在 .def 檔案中以不同的屬性列出兩次。
