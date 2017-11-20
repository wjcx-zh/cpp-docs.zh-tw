---
title: "編譯器警告 （層級 1） C4124 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4124
dev_langs: C++
helpviewer_keywords: C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3de13cb50444530fc0917330771b693f60a7e5f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4124"></a>編譯器警告 （層級 1） C4124
__fastcall 與堆疊檢查沒有效率  
  
 `__fastcall`關鍵字搭配堆疊檢查已啟用。  
  
 `__fastcall`慣例會產生更快的程式碼，但堆疊檢查會導致較慢的程式碼。 當使用`__fastcall`，關閉堆疊檢查與**check_stack** pragma 或 /Gs。  
  
 只會針對第一個函式宣告在這些情況下，會發出這個警告。