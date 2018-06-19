---
title: 編譯器錯誤 C2002 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01124fc839d6e788ff2dccae325f01f7d4337f5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164862"
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