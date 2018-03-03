---
title: "編譯器警告 C4746 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f92bae0e75d9a09de874cd999c044e703b3f3171
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4746"></a>編譯器警告 C4746
暫時性存取 '\<運算式 >' 受限於 /volatile: [iso &#124; ms] 設定; 請考慮使用 __iso_volatile_load/store 內建函式。  
  
 每當 volatile 變數直接存取時就會發出 C4746。 它要協助開發人員識別受目前指定的特定暫時性模型的程式碼位置 (這可以控制與[/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項)。 特別是，當使用 /volatile:ms 時，有助於尋找編譯器產生的硬體記憶體屏障。  
  
 __iso_volatile_load/store 內建可用來明確存取揮發性記憶體，而不受暫時性模型影響。 使用這些內建函式不會觸發 C4746。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。