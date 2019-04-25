---
title: 連結器工具警告 LNK4221
ms.date: 11/04/2016
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: baea8643001c550aeb3cb35dc6fe414e4330c0c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160376"
---
# <a name="linker-tools-warning-lnk4221"></a>連結器工具警告 LNK4221

這個物件檔案不會定義任何以前未定義的公用符號，所以不會使用任何使用這個程式庫的連結作業

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

若要編譯的檔案，並建立兩個物件的檔案，執行**cl /c a.cpp b.cpp**在命令提示字元。 如果您藉由執行連結的物件檔案**連結/lib /out:test.lib a.obj b.obj**，您會收到 LNK4221 警告。 如果您將物件連結執行**連結/lib /out:test.lib b.obj a.obj**，您不會收到一則警告。

在第二個案例中會不發出任何警告，因為連結器運作後進先出 (LIFO) 的方式。 在第一個案例中，b.obj 處理之前 a.obj，且 a.obj 加入任何新的符號。 藉由指示連結器，以處理 a.obj 第一次，您可以避免出現警告。

兩個原始程式檔指定選項時，此錯誤的常見原因[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)具有相同的標頭檔案名稱中指定**先行編譯標頭**欄位。 因為根據預設，stdafx.cpp 包含 stdafx.h 而且不加入任何新的符號 stdafx.h 處理此問題的常見原因。 如果另一個原始程式檔包含與 stdafx.h **/Yc** stdafx.obj 之前處理相關聯的.obj 檔案時，連結器將會擲回 LNK4221。

其中一種方式解決此問題是，確定每個先行編譯標頭，沒有只能有一個包含它的原始程式檔 **/Yc**。 所有其他原始程式檔必須使用先行編譯標頭。 如需如何變更此設定的詳細資訊，請參閱[/Yu （使用先行編譯標頭檔）](../../build/reference/yu-use-precompiled-header-file.md)。