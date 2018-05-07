---
title: 編譯器警告 （層級 4） C4268 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4268
dev_langs:
- C++
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef62649af39df950c3966ef93dddb6c71ec2fd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4268"></a>編譯器警告 (層級 4) C4268
'identifier': 'const' 編譯器產生預設建構函式初始化的靜態/全域資料填滿零的物件  
  
 A **const**編譯器產生的預設建構函式初始化全域或靜態的非一般類別的執行個體。  
  
## <a name="example"></a>範例  
  
```  
// C4268.cpp  
// compile with: /c /LD /W4  
class X {  
public:  
   int m_data;  
};  
  
const X x1;   // C4268  
```  
  
 因為這個類別的執行個體**const**，值`m_data`無法變更。