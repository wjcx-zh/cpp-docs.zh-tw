---
title: 連結器工具警告 LNK4221
ms.date: 08/19/2019
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: 299c3ef76006b347d6770d45ca317ff0eb941ffa
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630808"
---
# <a name="linker-tools-warning-lnk4221"></a>連結器工具警告 LNK4221

這個物件檔案不會定義任何先前未定義的公用符號, 因此任何使用此程式庫的連結操作都不會使用它

請考慮下列兩個程式碼片段。

```
// a.cpp
#include <atlbase.h>
```

```
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}
```

若要編譯檔案並建立兩個物件檔案, 請在命令提示字元中執行**cl/c a .cpp b.** 。 如果您藉由執行**連結/lib/out: test .lib**來連結化物件檔案, 將會收到 LNK4221 警告。 如果您藉由執行**連結/lib/out: test. .lib a .obj**來連結化物件, 則不會收到警告。

第二個案例中不會發出警告, 因為連結器會以後進先出 (LIFO) 的方式運作。 在第一個案例中, 會在 .obj 之前處理 b .obj, 而 .obj 沒有新的符號可新增。 藉由指示連結器先處理 .obj, 您就可以避免出現警告。

::: moniker range=">=vs-2019"

這項錯誤的常見原因是當兩個來源檔案指定 [ [/yc (建立先行編譯標頭檔)](../../build/reference/yc-create-precompiled-header-file.md) ] 選項, 並在 [先行**編譯頭**欄位] 中指定相同的標頭檔名稱。 這個問題的常見原因是處理*pch* , 因為根據預設, *pch*會包含*pch* , 而且不會加入任何新的符號。 如果另一個來源檔案包含含有 **/yc**的*pch* , 而且相關聯的 .obj 檔案在 pch 之前處理, 則連結器會擲回 LNK4221。

::: moniker-end

::: moniker range="<=vs-2017"

這項錯誤的常見原因是當兩個來源檔案指定 [ [/yc (建立先行編譯標頭檔)](../../build/reference/yc-create-precompiled-header-file.md) ] 選項, 並在 [先行**編譯頭**欄位] 中指定相同的標頭檔名稱。 此問題的常見原因是處理*stdafx.h* , 因為根據預設, *stdafx.h*包含*stdafx.h* , 而且不會新增任何新的符號。 如果另一個原始檔包含*stdafx.h*和 **/yc** , 而相關聯的 .obj 檔案則在 stdafx.h 之前處理, 則連結器會擲回 LNK4221。

::: moniker-end

解決這個問題的方法之一, 是要確定每個先行編譯的標頭只有一個原始程式檔, 其中包含 **/yc**。 所有其他來源檔案都必須使用先行編譯標頭檔。 如需有關如何變更此設定的詳細資訊, 請參閱[/yu (使用先行編譯標頭檔)](../../build/reference/yu-use-precompiled-header-file.md)。
