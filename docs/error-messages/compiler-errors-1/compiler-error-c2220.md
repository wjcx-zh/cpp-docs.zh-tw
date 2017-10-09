---
title: "編譯器錯誤 C2220 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: dc31519b2153c66ea9bab42f536ba7c6be5b2a10
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2220"></a>編譯器錯誤 C2220
將警告視為錯誤-沒有產生的物件檔案  
  
 [/WX](../../build/reference/compiler-option-warning-level.md)告訴編譯器將所有警告視為錯誤。 因為如果發生了錯誤，沒有產生任何目的檔或可執行檔。  
  
 此錯誤只會**/WX**旗標設定，並在編譯期間發生警告。 若要更正這個錯誤，您必須排除專案中的每個警告。  
  
### <a name="to-fix-use-one-of-the-following-techniques"></a>若要修正，請使用下列其中一種技術  
  
-   修正在專案中產生警告的問題。  
  
-   在較低的警告層級編譯 — 比方說，使用**/W3**而不是**/W4**。  
  
-   使用[警告](../../preprocessor/warning.md)pragma 來停用或隱藏特定的警告。  
  
-   請勿使用**/WX**編譯。
