---
title: 編譯器錯誤 C2998 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2998
dev_langs:
- C++
helpviewer_keywords:
- C2998
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19c37ef7ce1a1257f25c76bdf31efbdc25ae6ae3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33241882"
---
# <a name="compiler-error-c2998"></a>編譯器錯誤 C2998
'identifier' : 不可為範本定義  
  
 編譯器無法處理範本定義中使用的語法。  
  
 下列範例會產生 C2998：  
  
```  
// C2998.cpp  
// compile with: /c  
template <class T> int x = 1018; // C2998  
```