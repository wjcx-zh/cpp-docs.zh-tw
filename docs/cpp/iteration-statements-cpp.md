---
title: "反覆運算陳述式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: e00939a9ff383be4cf84c098ee7e93af307a1536
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="iteration-statements-c"></a>反覆運算陳述式 (C++)
反覆項目陳述式會使陳述式 (或複合陳述式) 依據某種迴圈終止準則執行零次或多次。 當這些陳述式是複合陳述式時，它們會執行順序，除非其中一個[中斷](../cpp/break-statement-cpp.md)陳述式或[繼續](../cpp/continue-statement-cpp.md)遇到陳述式。  
  
 C + + 提供四個反覆項目陳述式 —[時](../cpp/while-statement-cpp.md)，[不要](../cpp/do-while-statement-cpp.md)，[如](../cpp/for-statement-cpp.md)，和[範圍架構 for](../cpp/range-based-for-statement-cpp.md)。 每一種會逐一查看其終止運算式判斷值為零 (false)，或以強制終止迴圈為止**中斷**陳述式。 下表摘要說明這些陳述式及它們的動作，而且每一個陳述式會在後續章節中詳細討論。  
  
### <a name="iteration-statements"></a>反覆運算陳述式  
  
|陳述式|評估位置|初始化|遞增|  
|---------------|------------------|--------------------|---------------|  
|`while`|迴圈頂端|否|否|  
|**do**|迴圈底部|否|否|  
|**for**|迴圈頂端|是|是|  
|**範圍架構 for**|迴圈頂端|是|是|  
  
 反覆項目陳述式的陳述式部分不可以是宣告。 不過，它可以是包含宣告的複合陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 陳述式概觀](../cpp/overview-of-cpp-statements.md)
