---
title: 編譯器警告 （層級 1） C4076 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cfa28469e099dbf2b6bd43213073c304d0b2894
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275469"
---
# <a name="compiler-warning-level-1-c4076"></a>編譯器警告 (層級 1) C4076
'typemod': 無法與類型 'typename' 搭配使用  
  
 類型修飾詞 (不論是 **signed** 還是 `unsigned`) 不能與非整數類型搭配使用。 會忽略***typemod*** 。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4076：  
  
```  
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```