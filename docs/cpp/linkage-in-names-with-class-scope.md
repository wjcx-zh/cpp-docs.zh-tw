---
title: "類別範圍的名稱連結 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 20e8204510f6f6e924e205b89dc9f95734b4b893
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linkage-in-names-with-class-scope"></a>類別範圍的名稱連結
下列連結規則適用於具有類別範圍的名稱：  
  
-   靜態類別成員具有外部連結。  
  
-   類別成員函式具有外部連結。  
  
-   列舉程式和 `typedef` 名稱沒有連結。  
  
 **Microsoft 特定的**  
  
-   宣告為 `friend` 函式的函式必須具有外部連結。 將靜態函式宣告為 `friend` 會產生錯誤。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)