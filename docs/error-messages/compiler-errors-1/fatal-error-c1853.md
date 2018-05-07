---
title: 嚴重錯誤 C1853 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9aa6a67c13f76b0bf43159b9e9de95068102a2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1853"></a>嚴重錯誤 C1853
  
> '*filename*' 先行編譯標頭檔來自較舊版本的編譯器，或者先行編譯標頭是 c + +，而先使用自 C （反之亦然）  
  
可能的原因：  
  
-   先前版本的編譯器編譯先行編譯標頭。 請嘗試重新編譯的標頭使用目前的編譯器。  
  
-   先行編譯標頭是 c + +，而您使用它從 c 與 C 搭配使用的標頭所指定的其中一個[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項，或將原始程式檔的後置詞變更為"c"。 如需詳細資訊，請參閱[先行編譯程式碼的兩個選擇](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。