---
title: "編譯器錯誤 C2129 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2129
dev_langs:
- C++
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e2c5bd1b79960f83ef6effeb064375d6b49e8f20
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2129"></a>編譯器錯誤 C2129
靜態函式 'function' 宣告但未定義  
  
 向前參考對`static`從未被定義的函式。  
  
 A`static`函式必須在檔案範圍內定義。 如果函式定義於另一個檔案，也必須宣告`extern`。
