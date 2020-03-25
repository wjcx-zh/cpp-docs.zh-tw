---
title: 連結器工具警告 LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 706ab843f4b079b507033af76a7f407816fce820
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183354"
---
# <a name="linker-tools-warning-lnk4092"></a>連結器工具警告 LNK4092

共用可寫入區段 ' section ' 包含重定位;映射可能無法正確執行

每當您有一個共用區段來警告您可能嚴重的問題時，連結器就會發出此警告。

在多個進程之間共用資料的一種方式，是將區段標示為「共用」。 不過，將區段標示為共用可能會造成問題。 例如，您有一個 DLL，其中包含在共用資料區段中的宣告，如下所示：

```
int var = 1;
int *pvar = &var;
```

連結器無法解析 `pvar`，因為它的值取決於 DLL 載入記憶體中的位置，因此它會將重新配置記錄放在 DLL 中。 將 DLL 載入記憶體時，可以解析 `var` 的位址，並 `pvar` 指派。 如果另一個進程載入相同的 DLL，但無法將它載入相同的位址，則會針對第二個進程更新 `var` 位址的重新配置，而第一個處理常式的位址空間將會指向錯誤的位址。
