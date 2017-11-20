---
title: "-堆疊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /stack
dev_langs: C++
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae6696123ffa016a1c3f64ed2310efe571b55978
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="stack"></a>/STACK
```  
/STACK:reserve[,commit]  
```  
  
## <a name="remarks"></a>備註  
 此選項設定堆疊的大小 （位元組），並以十進位或 C 語言標記法會採用引數。 /STACK 選項僅適用於可執行檔。  
  
 *保留*引數指定虛擬記憶體中堆疊配置總量。 EDITBIN 會無條件進位到最接近的 4 個位元組指定的值。  
  
 選擇性`commit`引數受限於作業系統所解譯。 在 Windows NT、 Windows 95 和 Windows 98、`commit`指定一次配置的實體記憶體數量。 已認可的虛擬記憶體會造成要保留在分頁檔的空間。 較高`commit`值可以節省的時間，當應用程式需要較多的堆疊空間，但會增加記憶體需求且可能啟動時間。  
  
## <a name="see-also"></a>另請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)