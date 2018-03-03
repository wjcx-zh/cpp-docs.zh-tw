---
title: "嚴重錯誤 C1853 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 05c29c266aad095517734fdcac776e12467d34ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1853"></a>嚴重錯誤 C1853
  
> '*filename*' 先行編譯標頭檔來自較舊版本的編譯器，或者先行編譯標頭是 c + +，而先使用自 C （反之亦然）  
  
可能的原因：  
  
-   先前版本的編譯器編譯先行編譯標頭。 請嘗試重新編譯的標頭使用目前的編譯器。  
  
-   先行編譯標頭是 c + +，而您使用它從 c 與 C 搭配使用的標頭所指定的其中一個[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項，或將原始程式檔的後置詞變更為"c"。 如需詳細資訊，請參閱[先行編譯程式碼的兩個選擇](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。