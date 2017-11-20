---
title: "陣列宣告 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 74cfdf5393487ddd2cda7d478c0940c6db74b35a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="array-declarations"></a>陣列宣告
「陣列宣告」會為陣列命名並指定其元素的類型。 它也可以定義陣列中元素的數目。 具有陣列類型的變數會視為是陣列元素類型的指標。  
  
## <a name="syntax"></a>語法  
 `declaration`：  
 *declaration-specifiers init-declarator-list* opt**;**  
  
 *init-declarator-list*：  
 *init-declarator*  
  
 *init-declarator-list* **、**  *init-declarator*  
  
 *init-declarator*：  
 *declarator*  
  
 *declarator*  **=**  *initializer*  
  
 `declarator`：  
 *pointer* opt*direct-declarator*  
  
 *direct-declarator*：  
 *direct-declarator*  **[**  *constant-expression* opt**]**  
  
 因為 *constant-expression* 是選擇性的，所以其語法有兩種形式：  
  
-   第一個形式會定義陣列變數。 括弧內的 *constant-expression* 引數會指定陣列中的元素數目。 *constant-expression* (如果有的話) 必須具有整數類型與大於零的值。 每個元素都具有 *type-specifier* 所指定的類型，可以是除了 `void` 以外的任何類型。 陣列元素不可為函式類型。  
  
-   第二個形式會宣告一個已在其他地方定義的變數。 它省略了方括弧中的 *constant-expression* 引數，但未省略括弧。 只有當您先前初始化陣列、將其宣告為參數，或已在程式的其他位置明確將其宣告為陣列的參考時，才可以使用這個形式。  
  
 這兩種形式中，*direct-declarator*會為變數命名，而且可以修改變數的類型。 方括弧 (**[ ]**) 加上後面的 *direct-declarator* 會將宣告子修改為陣列類型。  
  
 類型限定詞可以出現在陣列類型物件的宣告中，不過，限定詞會套用到元素，而不會套用到陣列本身。  
  
 您可以宣告陣列的陣列 (「多維」陣列)，方法是以下列形式，在陣列宣告子後方使用括號括住常數運算式清單：  
  
```  
  
type-specifier  
declarator [constant-expression] [constant-expression] ...  
```  
  
 方括弧中的每個 *constant-expression* 都會定義指定維度的元素數目：二維陣列具有兩個以括弧括住的運算式、三維陣列有三個，依此類推。 只有在您先前已初始化陣列、將其宣告為參數，或已在程式的其他位置明確將其宣告為陣列的參考時，才可以忽略第一個常數運算式。  
  
 您可以使用複雜的宣告子定義各種物件類型的指標陣列，如[解譯更複雜的宣告子](../c-language/interpreting-more-complex-declarators.md)中所述。  
  
 陣列會依資料列儲存。 例如，下列陣列由二個資料列和三個資料行所組成，其中：  
  
```  
char A[2][3];  
```  
  
 三個資料行中的第一個資料列會先儲存，再儲存三個資料行中的第二個資料列。 這表示最後一個註標變化的速度最快。  
  
 若要參考陣列的個別元素，請使用一個註標運算式，如[後置運算子](../c-language/postfix-operators.md)中所述。  
  
## <a name="examples"></a>範例  
 這些範例說明陣列宣告：  
  
```  
float matrix[10][15];  
```  
  
 名為 `matrix` 的二維陣列中一共有 150 個元素，每個都是 **float** 類型。  
  
```  
struct {  
    float x, y;  
} complex[100];  
```  
  
 這是結構陣列的宣告。 這個陣列具有 100 個元素，每個元素都是一種包含兩個成員的結構。  
  
```  
extern char *name[];  
```  
  
 這個陳述式會將陣列的類型和名稱宣告為 `char` 的指標。 `name` 的實際定義位於其他地方。  
  
 **Microsoft 特定的**  
  
 保留陣列大小上限所需的整數類型為 **size_t** 的大小。 **size_t** 定義在標頭檔 STDDEF.H 中，是一個範圍從 0x00000000 到 0x7CFFFFFF 的 `unsigned int`。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [宣告子和變數宣告](../c-language/declarators-and-variable-declarations.md)