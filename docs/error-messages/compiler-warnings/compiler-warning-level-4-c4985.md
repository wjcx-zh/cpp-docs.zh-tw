---
title: 編譯器警告 （層級 4） C4985 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8f0b62a72d61ee061fd996f93638acba9e7ebb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4985"></a>編譯器警告 (層級 4) C4985
'symbol name': 屬性不存在先前的宣告中。  
  
 目前方法宣告或定義的 Microsoft 原始程式碼註釋語言 (SAL) 註釋與先前宣告的註釋不同。 方法的定義和宣告中必須使用相同的 SAL 註釋。  
  
 SAL 提供一組註釋，可讓您用來描述某個函式如何使用其參數、建立與其相關的假設，以及使其完成的保證。 這些註釋會在 sal.h header 標頭檔中定義。  
  
 請注意，除非專案已指定 [/analyze](../../build/reference/analyze-code-analysis.md) 旗標，否則 SAL 巨集不會展開。 當您指定 **/analyze**時，編譯器可能會擲回 C4985，即使出現的警告或錯誤都含有 **/analyze**亦然。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  對方法的定義及其所有宣告使用相同的 SAL 註釋。  
  
## <a name="see-also"></a>另請參閱  
 [SAL 註釋](../../c-runtime-library/sal-annotations.md)