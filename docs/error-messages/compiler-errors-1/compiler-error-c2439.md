---
title: 編譯器錯誤 C2439 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33bfe8ebf00850a54020b2a3f21159daf28b7224
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2439"></a>編譯器錯誤 C2439
'identifier': 無法初始化成員  
  
 無法初始化類別、 結構或等位成員。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  嘗試初始化間接基底類別或結構。  
  
2.  嘗試初始化繼承的類別或結構的成員。 繼承的成員必須初始化由類別或結構的建構函式。