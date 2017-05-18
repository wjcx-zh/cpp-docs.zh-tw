---
title: "編譯器警告 （層級 4） C4960 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4960
dev_langs:
- C++
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
caps.latest.revision: 8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: c61350cebf8601d706e7efec9273c967008bd6fd
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4960"></a>編譯器警告 (層級 4) C4960
'function' 太大而無法分析  
  
 當使用[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md)，編譯器偵測到函式大於 65,535 個指令的輸入的模組。 這類大型函式不適用於特性指引最佳化。  
  
 若要解決這個警告，請減少函式的大小。
