---
title: "編譯器警告 （層級 1 和 4） C4115 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4115
dev_langs:
- C++
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: bcddaf9da3fd05d66e219ec2134799bc49e30f9d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>編譯器警告 (層級 1 和 4) C4115
'type': 括弧中未命名類型的定義  
  
 這個指定的符號可用來定義括弧運算式內的結構、等位或列舉類型。 定義的範圍可能不如預期。  
  
 在 C 函式呼叫中，此定義具有全域範圍。 在 C++ 呼叫中，此定義與正在呼叫之函式的範圍相同。  
  
 這個警告也可能是由括弧內不是括號運算式的宣告子 (例如原型) 所造成。  
  
 在 ANSI 相容性 (/Za) 下所編譯的 C++ 和 C 程式中，這是層級 1 警告。 其他情況下則為層級 3。
