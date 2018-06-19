---
title: 編譯器警告 （層級 1） C4176 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4176
dev_langs:
- C++
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1e00e4bdc18b8adeb95d2425c8b122ffde867cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274858"
---
# <a name="compiler-warning-level-1-c4176"></a>編譯器警告 (層級 1) C4176
'subcomponent': #pragma 元件瀏覽器的未知子元件  
  
 **component** pragma 包含無效的子元件。 若要排除特定名稱的參考，您必須在名稱前面使用 **參考** 選項。  
  
## <a name="example"></a>範例  
  
```  
// C4176.cpp  
// compile with: /W1 /LD  
#pragma component(browser, off, i)  // C4176  
#pragma component(browser, off, references, i) // ok  
```