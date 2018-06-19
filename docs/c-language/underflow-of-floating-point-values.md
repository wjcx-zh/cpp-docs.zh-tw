---
title: 浮點值反向溢位 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ceaa41dcaca88c7857a03c16ccccabdba086fd0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387820"
---
# <a name="underflow-of-floating-point-values"></a>浮點值反向溢位
**ANSI 4.5.1** 數學函式是否在反向溢位範圍錯誤上將整數運算式 `errno` 設定為巨集 `ERANGE` 的值  
  
 浮點反向溢位不會將運算式 `errno` 設定為 `ERANGE`。 當值趨近於零，最終造成反向溢位時，會將其值設定為零。  
  
## <a name="see-also"></a>請參閱  
 [程式庫函式](../c-language/library-functions.md)