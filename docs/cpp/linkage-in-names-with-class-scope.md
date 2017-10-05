---
title: "類別範圍的名稱連結 |Microsoft 文件"
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
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- classes [C++], scope
- external linkage, scope linkage rules
- class names [C++], linkage
- classes [C++], names
- scope [C++], class names
- class scope [C++], linkage in names with
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 37a0dcca1da0ae56a8144adf862eda89bfb1c4d6
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="linkage-in-names-with-class-scope"></a>類別範圍的名稱連結
下列連結規則適用於具有類別範圍的名稱：  
  
-   靜態類別成員具有外部連結。  
  
-   類別成員函式具有外部連結。  
  
-   列舉程式和 `typedef` 名稱沒有連結。  
  
 **Microsoft 特定的**  
  
-   宣告為 `friend` 函式的函式必須具有外部連結。 將靜態函式宣告為 `friend` 會產生錯誤。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)
