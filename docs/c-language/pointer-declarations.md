---
title: "指標宣告 | Microsoft Docs"
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
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
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
translationtype: Human Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 02f33a5cd41dbbf45047915e3ad890311eba8cca
ms.lasthandoff: 04/04/2017

---
# <a name="pointer-declarations"></a>指標宣告
「指標宣告」用於命名指標變數，並且會指定變數所指向的物件類型。 宣告為指標的變數會保留記憶體位址。  
  
## <a name="syntax"></a>語法  
 *declarator*：  
 &nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*  
  
 *direct-declarator*：  
 &nbsp;&nbsp;*identifier*  
  
 &nbsp;&nbsp;**(** *declarator* **)**  
  
 &nbsp;&nbsp;*direct-declarator* **[** *constant-expression*<sub>opt</sub> **]**  
  
 &nbsp;&nbsp;*direct-declarator* **(** *parameter-type-list* **)**  
  
 &nbsp;&nbsp;*direct-declarator* **(** *identifier-list*<sub>opt</sub> **)**  
  
 *pointer*：  
 &nbsp;&nbsp;**\*** *type-qualifier-list*<sub>opt</sub>  
  
 &nbsp;&nbsp;**\*** *type-qualifier-list*<sub>opt</sub> *pointer*  
  
 *type-qualifier-list*：  
 &nbsp;&nbsp;*type-qualifier*  
  
 &nbsp;&nbsp;*type-qualifier-list* *type-qualifier*  
  
 *type-specifier* 會為物件提供類型，它可以是任何基本、結構或等位類型。 指標變數也可以指向函式、陣列和其他指標  (如需宣告和解譯更複雜指標類型的詳細資訊，請參閱[解譯更複雜的宣告子](../c-language/interpreting-more-complex-declarators.md))。  
  
 您可以將 *type-specifier* 設定為 **void**，以藉此延後指定指標參考的類型。 這類項目稱為「**void** 的指標」，書寫方式為 `void *`。 宣告為 *void* 指標的變數可用來指向任何類型的物件。 不過，若要在指標或指標所指向的物件上執行大部分作業，則必須為每項作業明確指定指標所指向的類型  (**char \*** 類型和 **void \*** 類型的變數可在不進行類型轉換的情況下與指派相容)。這類轉換可以利用類型轉換完成 (如需詳細資訊，請參閱[類型轉換](../c-language/type-cast-conversions.md))。  
  
 *type-qualifier* 可以是 **const** 或 **volatile**，或兩者都是。 這兩者會分別指定，指標不可由程式本身修改 (**const**)，或是指標可由非程式所控制的某個處理序合法修改 (**volatile**) (如需 **const** 和 **volatile** 的詳細資訊，請參閱[類型限定詞](../c-language/type-qualifiers.md))。  
  
 *declarator* 會為變數命名，並且可以包含類型修飾詞。 例如，如果 *declarator* 代表陣列，則指標的類型會修改為陣列的指標。  
  
 您可以在定義結構、等位或列舉類型之前，宣告結構、等位或列舉類型的指標。 使用結構或等位標記即可宣告指標，如下列範例所示。 由於編譯器不需要知道結構或等位的大小，也能為指標變數配置空間，因此允許使用這類宣告。  
  
## <a name="examples"></a>範例  
 下列範例將示範指標宣告。  
  
```  
char *message; /* Declares a pointer variable named message */  
```  
  
 *message* 指標會指向 **char** 類型的變數。  
  
```  
int *pointers[10];  /* Declares an array of pointers */  
```  
  
 *pointers* 陣列中有 10 個項目，每個項目都是 **int** 類型變數的指標。  
  
```  
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */  
```  
  
 *pointer* 變數會指向具有 10 個項目的陣列。 這個陣列中的每個項目都具有 **int** 類型。  
  
```  
int const *x;      /* Declares a pointer variable, x,  
                      to a constant value */   
```  
  
 *x* 指標可以修改為指向不同的 **int** 值，不過它所指向的值無法修改。  
  
```  
const int some_object = 5 ;  
int other_object = 37;  
int *const y = &fixed_object;  
int volatile *const z = &some_object;  
int *const volatile w = &some_object;  
```  
  
 這些宣告中的變數 *y* 會宣告為 **int** 值的常數指標。 它所指向的值可以修改，不過指標本身必須一律指向相同位置：*fixed_object* 的位址。 同樣地，*z* 是常數指標，不過它也會宣告為指向 **int**，且程式不可修改其值。 額外的 **volatile** 指定名稱指出，雖然程式無法修改 *z* 所指向的 **const int** 值，但是該值可以由與程式同時執行的處理序合法修改。 *w* 的宣告會指定程式無法變更所指向的值，而且程式無法修改指標。  
  
```  
struct list *next, *previous; /* Uses the tag for list */  
```  
  
 這個範例會宣告兩個指標變數 *next* 和 *previous*，這兩個變數會指向結構類型 *list*。 只要 *list* 類型定義與宣告具有相同的可視性，這個宣告就可以在定義 *list* 結構類型之前出現 (請參閱下一個範例)。  
  
```  
struct list   
{  
    char *token;  
    int count;  
    struct list *next;  
} line;  
```  
  
 變數 *line* 具有名為 *list* 的結構類型。 *list* 結構類型有三個成員：第一個成員是 **char** 值的指標，第二個是 **int** 值，而第三個是另一個 *list* 結構的指標。  
  
```  
struct id   
{  
    unsigned int id_no;  
    struct name *pname;  
} record;  
```  
  
 變數 *record* 具有結構類型 *id*。 請注意，*pname* 會宣告為另一個名為 *name* 之結構類型的指標。 這個宣告可以在定義 *name* 類型之前出現。  
  
## <a name="see-also"></a>另請參閱  
 [宣告子和變數宣告](../c-language/declarators-and-variable-declarations.md)
