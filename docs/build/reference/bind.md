---
title: /BIND
ms.date: 11/04/2016
f1_keywords:
- /bind
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
ms.openlocfilehash: 671a26268ab07db4a38ae241ae1e0867dd0eb43c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470846"
---
# <a name="bind"></a>/BIND

```
/BIND[:PATH=path]
```

## <a name="remarks"></a>備註

這個選項會設定為可執行檔或 DLL 的匯入位址表格中的進入點位址。 使用此選項，以降低載入程式的時間。

指定程式的可執行檔和中的 Dll*檔案*EDITBIN 命令列上的引數。 選擇性*路徑*/BIND 引數會指定所指定的檔案使用的 Dll 的位置。 以分號分隔多個目錄 (**;**)。 如果*路徑*未指定，EDITBIN 搜尋路徑環境變數中指定的目錄。 如果*路徑*會指定 EDITBIN 忽略 PATH 變數。

根據預設，程式載入器載入程式時設定進入點的位址。 此程序所花費的時間量會根據 Dll 的數字和程式中參考的進入點的數目而有所不同。 如果程式已修改其中 /BIND，而且如果基底位址的可執行檔，而且其 Dll 尚未載入的 Dll 不會衝突，作業系統就不需要設定這些位址。 不正確地以檔案的情況下，作業系統會重新放置到程式的 Dll，並重新計算的進入點位址，這會新增至程式的載入時間。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](../../build/reference/editbin-options.md)