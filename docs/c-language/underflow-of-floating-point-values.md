---
title: "浮點值反向溢位 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
caps.latest.revision: 7
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 6383f383221bb18c1dc58223e7183531bfd3c2d2
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="underflow-of-floating-point-values"></a>浮點值反向溢位
**ANSI 4.5.1** 數學函式是否在反向溢位範圍錯誤上將整數運算式 `errno` 設定為巨集 `ERANGE` 的值  
  
 浮點反向溢位不會將運算式 `errno` 設定為 `ERANGE`。 當值趨近於零，最終造成反向溢位時，會將其值設定為零。  
  
## <a name="see-also"></a>另請參閱  
 [程式庫函式](../c-language/library-functions.md)
