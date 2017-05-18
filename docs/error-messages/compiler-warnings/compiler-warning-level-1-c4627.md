---
title: "編譯器警告 （層級 1） C4627 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: 3
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
ms.openlocfilehash: a435eef7397eb98ca500be1c99e92efcb55c8be6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4627"></a>編譯器警告 (層級 1) C4627
'\<識別碼 >': 尋找先行編譯標頭使用時略過  
  
 當搜尋時使用先行編譯標頭位置，編譯器遇到`#include`指示詞*\<識別碼 >* include 檔。 編譯器會忽略`#include`指示詞，但發出警告**C4627**如果先行編譯標頭尚未包含*\<識別碼 >* include 檔。  
  
## <a name="see-also"></a>另請參閱  
 [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)
