---
title: "連結器工具警告 LNK4221 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4221"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4221"
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 連結器工具警告 LNK4221
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由於此物件檔案不會定義先前未定義的任何公用符號，因此使用這個程式庫的所有連結作業均不使用此物件檔案  
  
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
  
 若要編譯檔案並建立兩個物件檔案，請在命令提示字元中執行 **cl \/c a.cpp b.cpp**。  如果您透過執行 **link \/lib \/out:test.lib a.obj b.obj** 來連結物件檔案，將會收到 LNK4221 警告。  如果您透過執行 **link \/lib \/out:test.lib b.obj a.obj** 來連結物件，則不會收到任何警告。  
  
 由於連結器是以後進先出 \(LIFO\) 的模式作業，因此在第二個案例中將不會發出任何警告。  在第一個案例中，b.obj 是在 a.obj 之前處理的，且 a.obj 沒有任何可新增的新符號。  只要指示連接器先處理 a.obj，您便能避免收到警告。  
  
 這個錯誤的常見原因是當兩個原始程式檔使用與 \[**先行編譯標頭檔**\] 欄位中所指定的相同標頭檔名指定 [\/Yc \(建立先行編譯標頭檔\)](../../build/reference/yc-create-precompiled-header-file.md) 選項時。  這個問題的常見原因則與 stdafx.h 有關，因為在預設的情況下，stdafx.cpp 含有 stdafx.h，且不會新增任何新符號。  如果其他原始程式檔利用 **\/Yc** 納入 stdafx.h，且相關聯的 .obj 檔案則是在 stdafx.obj 之前處理的，則連接器將會擲回 LNK4221。  
  
 一個解決此問題的方法是確認每個先行編譯標頭檔中，只有一個原始程式檔利用 **\/Yc** 將其納入。  其他所有原始程式檔都必須使用先行編譯標頭檔。  如需如何變更此設定的詳細資訊，請參閱 [\/Yu \(使用先行編譯標頭檔\)](../../build/reference/yu-use-precompiled-header-file.md)。