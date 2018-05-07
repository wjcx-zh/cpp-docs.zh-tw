---
title: 編譯器錯誤 C2129 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2129
dev_langs:
- C++
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d151c774672b1788ca893a9812deb3e41100dc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2129"></a>編譯器錯誤 C2129
靜態函式 'function' 宣告但未定義  
  
 向前參考對`static`從未被定義的函式。  
  
 A`static`函式必須在檔案範圍內定義。 如果函式定義於另一個檔案，也必須宣告`extern`。