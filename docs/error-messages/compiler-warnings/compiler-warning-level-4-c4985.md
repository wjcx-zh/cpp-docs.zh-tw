---
title: "編譯器警告 （層級 4） C4985 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
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
ms.openlocfilehash: 4a36692420ea9d5547f236c1e5dfeaa269afbb67
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4985"></a>編譯器警告 (層級 4) C4985
'symbol name': 屬性不存在先前的宣告中。  
  
 目前方法宣告或定義的 Microsoft 原始程式碼註釋語言 (SAL) 註釋與先前宣告的註釋不同。 方法的定義和宣告中必須使用相同的 SAL 註釋。  
  
 SAL 提供一組註釋，可讓您用來描述某個函式如何使用其參數、建立與其相關的假設，以及使其完成的保證。 這些註釋會在 sal.h header 標頭檔中定義。  
  
 請注意，除非專案已 SAL 巨集不會展開[/ 分析](../../build/reference/analyze-code-analysis.md)指定旗標。 當您指定 **/analyze**時，編譯器可能會擲回 C4985，即使出現的警告或錯誤都含有 **/analyze**亦然。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  對方法的定義及其所有宣告使用相同的 SAL 註釋。  
  
## <a name="see-also"></a>另請參閱  
 [SAL 註釋](../../c-runtime-library/sal-annotations.md)
