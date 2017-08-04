---
title: "簡單變數宣告 | Microsoft Docs"
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
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
caps.latest.revision: 9
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
ms.openlocfilehash: 03d3939ef04a6a1a8bc5e3cd3ec5bfe56236ca0f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="simple-variable-declarations"></a>簡單變數宣告
簡單變數的宣告 (直接宣告子的最簡單形式) 會指定變數的名稱和類型。 另外也會指定變數的儲存類別和資料類型。  
  
 儲存類別或類型 (或兩者皆是) 為變數宣告中所必要。 不具類型的變數 (例如 `var;`) 會產生警告。  
  
## <a name="syntax"></a>語法  
 `declarator`：  
 *pointer* opt  
  
 *direct-declarator*  
  
 *direct-declarator*：  
 *identifier*  
  
 *identifier*:  
 *nondigit*  
  
 *identifier nondigit*  
  
 *identifier digit*  
  
 對於算術、結構、等位、列舉和 void 類型，以及 `typedef` 名稱所代表的類型，簡單宣告子可以在宣告中使用，因為類型規範會提供所有類型相關資訊。 指標、陣列和函式類型都需要更複雜的宣告子。  
  
 您可以使用以逗號分隔 (**,**) 的識別項清單，在相同的宣告中指定數個變數。 宣告中定義的所有變數都會具有相同的基底類型。 例如：  
  
```  
int x, y;        /* Declares two simple variables of type int */  
int const z = 1; /* Declares a constant value of type int */  
```  
  
 變數 `x` 和 `y` 可以保存集合中以特定實作的 `int` 類型定義的任何值。 簡單物件 `z` 會初始化為值 1，而且不可修改。  
  
 如果 `z` 是針對未初始化的靜態變數或是在檔案範圍內宣告，就會收到初始值 0，而且該值不可修改。  
  
```  
unsigned long reply, flag; /* Declares two variables  
                              named reply and flag     */  
```  
  
 在這個範例中，`reply` 和 `flag` 這兩個變數都具有 `unsigned long` 類型並且保存不帶正負號的整數值。  
  
## <a name="see-also"></a>另請參閱  
 [宣告子和變數宣告](../c-language/declarators-and-variable-declarations.md)
