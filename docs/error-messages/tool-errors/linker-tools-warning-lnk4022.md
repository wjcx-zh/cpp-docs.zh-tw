---
title: "連結器工具警告 LNK4022 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4022
dev_langs: C++
helpviewer_keywords: LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e35974a72de349f94f2189f676b6dc955c48fab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4022"></a>連結器工具警告 LNK4022
找不到符號 'symbol' 的唯一相符項目  
  
 連結或 LIB 找到多個比對指定的未裝飾符號，並無法解析模稜兩可。 會不產生任何輸出檔 （.exe、.dll、.exp 或.lib）。 這個警告後面其中一個警告[LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md)每個重複的符號時，最後接著嚴重錯誤[LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)。  
  
 若要避免這個警告，指定以其裝飾形式的符號。 執行[DUMPBIN](../../build/reference/dumpbin-options.md)上物件，以檢視裝飾名稱。