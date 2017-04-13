---
title: "編譯器警告 （層級 1） C4176 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4176
dev_langs:
- C++
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
caps.latest.revision: 6
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
ms.openlocfilehash: 1ac13214355dd6005130297a944df17afac202eb
ms.lasthandoff: 04/12/2017

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
