---
title: "運算式評估工具錯誤 CXX0064 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0064
dev_langs: C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2edeb05e39c6d2e70cb2c9dde562a89e85921301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0064"></a>運算式評估工具錯誤 CXX0064
無法在繫結的虛擬成員函式上設定中斷點  
  
 設定中斷點上的虛擬成員函式，透過指標至物件，例如：  
  
```  
pClass->vfunc( int );  
```  
  
 虛擬函式，可以設定中斷點，輸入此類別，例如：  
  
```  
Class::vfunc( int );  
```  
  
 這個錯誤是與 can0064 相同。