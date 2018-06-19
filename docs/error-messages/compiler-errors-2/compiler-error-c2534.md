---
title: 編譯器錯誤 C2534 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2534
dev_langs:
- C++
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae52374e09852ffb68c5807353155d9928924eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228234"
---
# <a name="compiler-error-c2534"></a>編譯器錯誤 C2534
'identifier': 建構函式無法傳回值  
  
 建構函式無法傳回值或具有傳回型別 (甚至`void`傳回型別)。  
  
 這項錯誤可能會修正藉由移除`return`陳述式從建構函式定義。  
  
 下列範例會產生 C2534:  
  
```  
// C2534.cpp  
class A {  
public:  
   int i;  
   A() { return i; }   // C2534  
};  
```