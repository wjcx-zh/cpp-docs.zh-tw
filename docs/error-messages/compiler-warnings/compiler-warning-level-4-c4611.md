---
title: 編譯器警告 （層級 4） C4611 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5946c10b5e0e0e7e08f1ee37c77120896937adb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4611"></a>編譯器警告 (層級 4) C4611
'function' 和 c + + 物件解構間的互動是不可移植  
  
 在某些平台，包括的函式**攔截**可能不支援 c + + 物件語意解構時超出範圍。  
  
 若要避免非預期的行為，請避免使用**攔截**有建構函式和解構函式的函式中。  
  
 這個警告，才會發出一次。請參閱[pragma 警告](../../preprocessor/warning.md)。