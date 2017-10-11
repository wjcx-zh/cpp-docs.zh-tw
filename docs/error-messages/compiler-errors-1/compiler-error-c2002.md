---
title: "編譯器錯誤 C2002 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d8f6fc5983a462850581f69ca32dd7c305f9e847
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2002"></a>編譯器錯誤 C2002
無效的寬字元常數  
  
 多位元組字元常數無效。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  寬字元常數中包含比預期更多的位元組。  
  
2.  標準標頭檔 STDDEF.h 就不會包含。  
  
3.  無法使用一般的字串常值串連的寬字元。  
  
4.  寬字元常數必須加上 'L' 字元：  
  
    ```  
    L'mbconst'  
    ```  
  
5.  Microsoft c + + 前置處理器指示詞的文字引數必須是 ASCII。 例如，指示詞`#pragma message(L"string")`，不正確。
