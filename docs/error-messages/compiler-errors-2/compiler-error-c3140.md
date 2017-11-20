---
title: "編譯器錯誤 C3140 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3140
dev_langs: C++
helpviewer_keywords: C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e809ddaaa278e0c6a2660fbb71b84323dcd40018
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3140"></a>編譯器錯誤 C3140
在相同編譯單位中不能有多個 'module' 屬性  
  
 [模組](../../windows/module-cpp.md)屬性只能定義一次每個專案。  
  
 下列範例會產生 C3140:  
  
```  
// C3140.cpp  
// compile with: /c  
[emitidl];  
[module(name = "MyLibrary")];  
[module(name = "MyLibrary2")];   // C3140  
```