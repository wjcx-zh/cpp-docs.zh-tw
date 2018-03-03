---
title: "編譯器錯誤 C2930 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2930
dev_langs:
- C++
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b107f2daa9190b2f1c27e81a31b596cc9c850743
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2930"></a>編譯器錯誤 C2930
'class': type-class-id 重新定義為 'enum identifier' 的列舉值  
  
 您無法使用泛型或樣板類別作為列舉的成員。  
  
 此錯誤可能是大括弧不對稱所造成。  
  
 下列範例會產生 C2930：  
  
```  
// C2930.cpp  
// compile with: /c  
template<class T>   
class x{};  
enum SomeEnum { x };   // C2930  
  
class y{};  
enum SomeEnum { y };  
```  
  
 使用泛型時，也會發生 C2930：  
  
```  
// C2930c.cpp  
// compile with: /clr /c  
generic<class T>   
ref struct GC {};  
enum SomeEnum { GC };   // C2930  
  
ref struct GC2 {};  
enum SomeEnum2 { GC2 };  
```