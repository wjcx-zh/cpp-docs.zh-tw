---
title: 連結器工具警告 LNK4221 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4221
dev_langs:
- C++
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8906c4308b8586d5b1312739921f58063e820deb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4221"></a>連結器工具警告 LNK4221
這個物件檔案沒有定義任何以前未定義的公用符號，所以不會使用任何使用這個程式庫的連結作業  
  
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
  
 若要編譯程式檔建立兩個物件的檔案，執行**cl /c a.cpp b.cpp**在命令提示字元。 如果您藉由執行連結的目的檔**連結/lib /out:test.lib a.obj b.obj**，您會收到 LNK4221 警告。 如果您將物件連結執行**連結/lib /out:test.lib b.obj a.obj**，您不會收到警告。  
  
 在第二個案例中會不發出任何警告，因為連結器運作後進先出 (LIFO) 的方式。 在第一個案例中，b.obj 會處理之前 a.obj，而且 a.obj 有加入任何新的符號。 藉由指示連結器，以處理 a.obj 第一次，您可以避免此警告。  
  
 此錯誤的常見原因是當兩個原始程式檔指定選項[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)同名標頭檔中指定**先行編譯標頭**欄位。 因為根據預設，stdafx.cpp 包含 stdafx.h 而且不加入任何新的符號 stdafx.h 處理這個問題的常見原因。 如果另一個來源檔案包含與 stdafx.h **/Yc**和相關聯的.obj 檔案處理 stdafx.obj 前、 連結器將會擲回 LNK4221。  
  
 其中一種方式解決此問題是，確定每個先行編譯標頭，沒有只能有一個來源檔案，其中包含與 **/Yc**。 所有其他原始程式檔必須使用先行編譯標頭。 如需如何變更此設定的詳細資訊，請參閱[/Yu （使用先行編譯標頭檔）](../../build/reference/yu-use-precompiled-header-file.md)。