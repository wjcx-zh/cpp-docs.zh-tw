---
title: "編譯器錯誤 C2021 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2021
dev_langs:
- C++
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fd62bc02ce871f87101ebd255690e2ff3d81d176
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2021"></a>編譯器錯誤 C2021
必須是指數值，而非 'character'  
  
 浮點常數的指數所用的字元不是有效的數字。 請務必使用在範圍內的指數。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2021:  
  
```  
// C2021.cpp  
float test1=1.175494351E;   // C2021  
```  
  
## <a name="example"></a>範例  
 可能的解決方式：  
  
```  
// C2021b.cpp  
// compile with: /c  
float test2=1.175494351E8;  
```