---
title: "編譯器錯誤 C3398 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
ms.openlocfilehash: 66bd229369456da18d8bed60b25b6e6b07e03f27
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3398"></a>編譯器錯誤 C3398
'operator' : 無法從 'function_signature' 轉換成 'function_pointer'。 來源運算式必須是函式符號  
  
 當[__clrcall](../../cpp/clrcall.md)編譯時呼叫慣例未指定**/clr**，編譯器會產生兩個進入點 （位址） 的每個函式、 原生進入點和 managed 的進入點。  
  
 根據預設，編譯器會傳回原生進入點，但有些情況需要 Managed 進入點 (例如，將位址指派給 `__clrcall` 函式指標時)。 為了讓編譯器可靠地選擇指派中的 Managed 進入點，右邊必須是函式符號。
