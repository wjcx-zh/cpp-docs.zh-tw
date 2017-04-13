---
title: "編譯器警告 (層級 1) C4729 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4729
dev_langs:
- C++
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
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
ms.openlocfilehash: 57a83903ac31b7f05ee1892cca011c9ef9d8fe74
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4729"></a>編譯器警告 (層級 1) C4729
依據 flow graph 產生的警告，發現函式太大  
  
 如果要編譯的函式太大，無法可靠地檢查將產生警告的情況，則會產生這個警告。 這個警告才時產生[/Od](../../build/reference/od-disable-debug.md)時所使用的編譯器選項。  
  
 若要解決這個警告，請將函式分為較小的函式。
