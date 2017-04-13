---
title: "編譯器警告 （層級 1） C4810 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4810
dev_langs:
- C++
helpviewer_keywords:
- C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: af66e9908d27b1f49680c72a14ad1c1b5ddf948e
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4810"></a>編譯器警告 (層級 1) C4810
pragma pack(show) 的值 == n  
  
 當您使用時，會發出這個警告**顯示**選項[套件](../../preprocessor/pack.md)pragma。 *n* 是目前的 pack 值。  
  
 例如，下列程式碼顯示 C4810 警告如何使用 pack pragma：  
  
```  
// C4810.cpp  
// compile with: /W1 /LD  
// C4810 expected  
#pragma pack(show)  
#pragma pack(4)  
#pragma pack(show)  
```
