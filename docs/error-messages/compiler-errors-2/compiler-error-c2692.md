---
title: 編譯器錯誤 C2692 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a02110750a748b5c520df7d202a87957f227a802
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2692"></a>編譯器錯誤 C2692
'function_name': 完全原型函式中使用的 C 編譯器所需 '/ /clr' 選項  
  
 當編譯的.NET managed 程式碼時，C 編譯器需要 ANSI 函式宣告。 此外，如果函式可不接受任何參數，它必須明確宣告`void`做為參數類型。