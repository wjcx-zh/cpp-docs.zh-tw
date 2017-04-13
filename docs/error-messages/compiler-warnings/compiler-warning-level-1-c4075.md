---
title: "編譯器警告 （層級 1） C4075 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4075
dev_langs:
- C++
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
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
ms.openlocfilehash: f4ff41114e108ec4bcf1afb68bfa67716fd9bdd5
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4075"></a>編譯器警告 (層級 1) C4075
初始設定式置於無法辨識的初始化區域  
  
 A [#pragma init_seg](../../preprocessor/init-seg.md)會使用無法辨識的區段名稱。 編譯器會忽略 **pragma** 命令。  
  
 下列範例會產生 C4075：  
  
```  
// C4075.cpp  
// compile with: /W1  
#pragma init_seg("mysegg")   // C4075  
  
// try..  
// #pragma init_seg(user)  
  
int main() {  
}  
```
