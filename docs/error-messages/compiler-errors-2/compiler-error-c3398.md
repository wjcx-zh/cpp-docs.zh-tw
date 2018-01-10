---
title: "編譯器錯誤 C3398 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3398
dev_langs: C++
helpviewer_keywords: C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4b332346dd8e8b7e906e961c86805ad0564f0f79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3398"></a>編譯器錯誤 C3398
'operator' : 無法從 'function_signature' 轉換成 'function_pointer'。 來源運算式必須是函式符號  
  
 使用 [/clr](../../cpp/clrcall.md) 編譯時，如果未指定 **__clrcall**呼叫慣例，編譯器會為每個函式產生兩個進入點 (位址)：原生進入點和 Managed 進入點。  
  
 根據預設，編譯器會傳回原生進入點，但有些情況需要 Managed 進入點 (例如，將位址指派給 `__clrcall` 函式指標時)。 為了讓編譯器可靠地選擇指派中的 Managed 進入點，右邊必須是函式符號。