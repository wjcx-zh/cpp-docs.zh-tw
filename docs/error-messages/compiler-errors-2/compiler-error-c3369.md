---
title: "編譯器錯誤 C3369 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3369
dev_langs: C++
helpviewer_keywords: C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 62cd3de9bca4e695d051e150c7dfa45dca28936a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3369"></a>編譯器錯誤 C3369
'module name': 已定義 idl_module  
  
 定義 DLL 的 [idl_module](../../windows/idl-module.md) 用法只能在程式中出現一次。  
  
 下列範例會產生 C3369：  
  
```  
// C3369.cpp  
// compile with: /c  
[idl_module(name="name1", dllname="x.dll")]; // C3369  
[idl_module(name="name1", dllname="x.dll")];  
```