---
title: 編譯器錯誤 C2220 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d23476de35e0af45b46a775683ba8673b4959346
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171489"
---
# <a name="compiler-error-c2220"></a>編譯器錯誤 C2220
將警告視為錯誤-沒有產生的物件檔案  
  
 [/WX](../../build/reference/compiler-option-warning-level.md)告訴編譯器將所有警告視為錯誤。 因為如果發生了錯誤，沒有產生任何目的檔或可執行檔。  
  
 此錯誤只會 **/WX**旗標設定，並在編譯期間發生警告。 若要更正這個錯誤，您必須排除專案中的每個警告。  
  
### <a name="to-fix-use-one-of-the-following-techniques"></a>若要修正，請使用下列其中一種技術  
  
-   修正在專案中產生警告的問題。  
  
-   在較低的警告層級編譯 — 比方說，使用 **/W3**而不是 **/W4**。  
  
-   使用[警告](../../preprocessor/warning.md)pragma 來停用或隱藏特定的警告。  
  
-   請勿使用 **/WX**編譯。