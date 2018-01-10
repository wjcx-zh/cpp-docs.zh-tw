---
title: "結構宣告 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aada86ec63ccade17577f5410ced62cb4d5cf03f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="structure-declarations"></a>結構宣告
「結構宣告」會命名一個類型，並指定可能具有不同類型之變數值的序列 (稱為結構的「成員」或「欄位」)。 選擇性識別項 (稱為「標記」) 會為結構類型提供名稱，並且可以在後續參考結構類型時使用。 該結構類型的變數會保留由該類型定義的整個序列。 C 中的結構類似於其他語言中稱為「記錄」的類型。  
  
## <a name="syntax"></a>語法  
 *struct-or-union-specifier*：  
 *struct-or-union identifier* opt**{** *struct-declaration-list* **}**  
  
 *struct-or-union identifier*  
  
 *struct-or-union*：  
 **struct**  
  
 **union**  
  
 *struct-declaration-list*：  
 *struct-declaration*  
  
 *struct-declaration-list struct-declaration*  
  
 結構的內容定義為  
  
 *struct-declaration*：  
 *specifier-qualifier-list struct-declarator-list*  **;**  
  
 *specifier-qualifier-list*：  
 *type-specifier specifier-qualifier-list* opt  
  
 *type-qualifier specifier-qualifier-list* opt  
  
 *struct-declarator-list*：  
 *struct-declarator*  
  
 *struct-declarator-list*  **,**  *struct-declarator*  
  
 *struct-declarator*：  
 `declarator`  
  
 結構類型的宣告並沒有為結構預留空間。 它只是一個樣板，供稍後宣告結構變數時使用。  
  
 先前定義的 *identifier* (標記) 可用來參考在其他位置定義的結構類型。 在這種情況下，只要這個定義是可見的，*struct-declaration-list* 就不可以重複。 為結構類型的結構和 typedef 宣告的指標，可以在定義結構類型之前使用結構標記。 不過，必須實際使用欄位的大小之前進行結構定義。 這是類型和類型標記的不完整定義。 若要讓這個定義完整，類型定義稍後必須出現在相同範圍中。  
  
 *struct-declaration-list* 會指定結構成員的類型和名稱。 *struct-declaration-list* 引數包含一個或多個變數或位元欄位宣告。  
  
 *struct-declaration-list* 中宣告的每個變數都會定義為結構類型的成員。 *struct-declaration-list* 中的變數宣告與本節所討論的其他變數宣告都具有相同的形式，不同的是，這些宣告不能包含儲存類別規範或初始設定式。 除了類型 `void`、不完整的類型或函式類型之外，結構成員可以擁有任何變數類型。  
  
 成員不可以宣告為具有其出現位置中的結構類型。 不過，只要結構類型具有標記，成員就可以宣告為其所在位置中結構類型的指標。 這可讓您建立結構的連結清單。  
  
 結構遵循與其他識別項相同的範圍。 結構識別項必須與具有相同可視性的其他結構、等位和列舉標記有所區別。  
  
 *struct-declaration-list* 中的每個 *struct-declaration* 必須是清單中唯一的項目。 不過，*struct-declaration-list* 中的識別項名稱不需要與一般變數名稱，或其他結構宣告清單中的識別項有所區別。  
  
 巢狀結構也可以存取，如同它們是在檔案範圍層級中宣告一樣。 例如，指定以下宣告：  
  
```  
struct a  
{  
    int x;  
    struct b  
    {  
      int y;  
    } var2;  
} var1;  
```  
  
 這些宣告都是合法的：  
  
```  
struct a var3;  
struct b var4;  
```  
  
## <a name="examples"></a>範例  
 這些範例說明結構宣告：  
  
```  
struct employee   /* Defines a structure variable named temp */  
{  
    char name[20];  
    int id;  
    long class;  
} temp;  
```  
  
 `employee` 結構有三個成員：`name`、`id` 和 `class`。 `name` 成員是一個 20 個元素的陣列，而 `id` 和 `class` 分別是具有 `int` 和 **long** 類型的簡單成員。 識別項 `employee` 為結構識別項。  
  
```  
struct employee student, faculty, staff;  
```  
  
 此範例定義三個結構變數：`student`、`faculty` 和 `staff`。 每個結構具有三個成員的相同清單。 成員宣告為具有結構類型 `employee`，定義在先前的範例中。  
  
```  
struct           /* Defines an anonymous struct and a */  
{                /* structure variable named complex  */  
    float x, y;  
} complex;  
```  
  
 `complex` 結構具有兩個類型為 **float** 的成員，即 `x` 和 `y`。 結構類型沒有標記，因此為未命名或匿名的。  
  
```  
struct sample   /* Defines a structure named x */  
{  
    char c;  
    float *pf;  
    struct sample *next;  
} x;  
```  
  
 結構的前兩個成員為 `char` 變數和 **float** 值的指標。 第三個成員 `next` 宣告為所定義結構類型 (`sample`) 的指標。  
  
 不需要標記名稱時，匿名結構會很有用。 當某個宣告會定義所有結構執行個體時，就會發生這種情況。 例如:   
  
```  
struct  
{  
    int x;  
    int y;  
} mystruct;  
```  
  
 內嵌結構通常是匿名的。  
  
```  
struct somestruct  
{  
    struct    /* Anonymous structure */  
    {  
        int x, y;  
    } point;  
    int type;  
} w;  
```  
  
 **Microsoft 特定的**  
  
 編譯器允許使用一個可變大小或大小為零的陣列，做為結構的最後一個成員。 在各種情況下使用時，如果常數陣列的大小不同，這會非常有幫助。 此類結構的宣告如下所示：  
  
 `struct` *identifier***{** *set-of-declarations* *type array-name***[ ];};**  
  
 可變大小陣列只可以顯示為結構的最後一個成員。 只要未在任何封閉結構中宣告其他成員，包含可變大小陣列的宣告可以巢狀的方式放置於其他結構內。 不允許使用此類結構的陣列。 `sizeof` 運算子，套用至此類型的變數或類型本身時，會假設陣列的大小為 0。  
  
 當它們是另一個結構或等位的成員時，也可以指定不含宣告子的結構宣告。 欄位名稱會提升至封閉結構中。 例如，無名稱的結構如下所示：  
  
```  
struct s  
{  
    float y;  
    struct  
    {  
        int a, b, c;  
    };  
    char str[10];  
} *p_s;  
.  
.  
.  
p_s->b = 100;  /* A reference to a field in the s structure */  
```  
  
 如需結構參考的資訊，請參閱[結構和等位成員](../c-language/structure-and-union-members.md)。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [宣告子和變數宣告](../c-language/declarators-and-variable-declarations.md)