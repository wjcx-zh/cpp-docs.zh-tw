---
title: 編譯器錯誤 C3398 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b870479977bfb49ff39d5a15fe19fc700ed66b8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255826"
---
# <a name="compiler-error-c3398"></a>編譯器錯誤 C3398
'operator' : 無法從 'function_signature' 轉換成 'function_pointer'。 來源運算式必須是函式符號  
  
 使用 [/clr](../../cpp/clrcall.md) 編譯時，如果未指定 **__clrcall**呼叫慣例，編譯器會為每個函式產生兩個進入點 (位址)：原生進入點和 Managed 進入點。  
  
 根據預設，編譯器會傳回原生進入點，但有些情況需要 Managed 進入點 (例如，將位址指派給 `__clrcall` 函式指標時)。 為了讓編譯器可靠地選擇指派中的 Managed 進入點，右邊必須是函式符號。