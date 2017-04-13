---
title: "編譯器警告 C4962 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4962
dev_langs:
- C++
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 9daeb42e0a6b0eea6d0f3e98656e3b0bd2416142
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4962"></a>編譯器警告 C4962
'function': 特性指引最佳化已停用，因為最佳化導致分析資料變成不一致  
  
 函式並不是使用 /LTCG:PGO 進行編譯，因為函式的計數 (分析) 資料不可靠。 請重做分析，以重新產生包含該函式不可靠分析資料的 .pgc 檔。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱[編譯器警告為關閉的預設](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
