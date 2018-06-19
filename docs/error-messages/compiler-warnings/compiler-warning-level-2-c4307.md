---
title: 編譯器警告 （層級 2） C4307 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4307
dev_langs:
- C++
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52914fc5825bda5647308c006b853538f3d6225e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292028"
---
# <a name="compiler-warning-level-2-c4307"></a>編譯器警告 (層級 2) C4307
'operator': 整數常數溢位  
  
 整數常數溢位為它配置的空間會導致運算式中使用的運算子。 您可能需要使用較大的類型常數。 A**帶正負號 int**保存較小的值比`unsigned int`因為**帶正負號 int**使用一個位元表示正負號。  
  
 下列範例會產生 C4307:  
  
```  
// C4307.cpp  
// compile with: /W2  
int i = 2000000000 + 2000000000;   // C4307  
int j = (unsigned)2000000000 + 2000000000;   // OK  
  
int main()  
{  
}  
```