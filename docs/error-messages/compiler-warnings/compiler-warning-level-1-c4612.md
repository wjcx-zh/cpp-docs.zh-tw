---
title: "編譯器警告 （層級 1） C4612 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4612
dev_langs: C++
helpviewer_keywords: C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a2d5ddc76271df594c2bd5b2ae1707933510338
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4612"></a>編譯器警告 (層級 1) C4612
Include 檔檔名錯誤  
  
 當檔案名稱不正確或遺漏時， **#pragma include_alias** 會發生這個錯誤。  
  
 引數**#pragma include_alias**陳述式可以使用引號 (**"***filename***"**) 或角括弧格式 (**\<**  *filename***>**)，但兩端都必須使用相同的格式。  
  
## <a name="example"></a>範例  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```