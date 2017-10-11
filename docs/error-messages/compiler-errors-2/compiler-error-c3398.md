---
title: "編譯器錯誤 C3398 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 54241a6e57bdfd8795d6f894a1410c1e6c90cf49
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3398"></a>編譯器錯誤 C3398
'operator' : 無法從 'function_signature' 轉換成 'function_pointer'。 來源運算式必須是函式符號  
  
 使用 [/clr](../../cpp/clrcall.md) 編譯時，如果未指定 **__clrcall**呼叫慣例，編譯器會為每個函式產生兩個進入點 (位址)：原生進入點和 Managed 進入點。  
  
 根據預設，編譯器會傳回原生進入點，但有些情況需要 Managed 進入點 (例如，將位址指派給 `__clrcall` 函式指標時)。 為了讓編譯器可靠地選擇指派中的 Managed 進入點，右邊必須是函式符號。
