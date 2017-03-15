---
title: "等位宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "union 關鍵字 [C], 宣告"
  - "等位"
  - "variant 記錄"
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 等位宣告
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「等位宣告」會指定一組變數值，以及選擇性地指定命名等位的標記。  變數值稱為等位的「成員」，而且可以具有不同的類型。  等位類似其他語言中的「變異記錄」。  
  
## 語法  
 *struct\-or\-union\-specifier*:  
 *struct\-or\-union identifier*  opt **{** *struct\-declaration\-list* **}**  
  
 *struct\-or\-union identifier*  
  
 *struct\-or\-union*:  
 **struct**  
  
 **union**  
  
 *struct\-declaration\-list*:  
 *struct\-declaration*  
  
 *struct\-declaration\-list struct\-declaration*  
  
 等位的內容定義為  
  
 *struct\-declaration*:  
 *specifier\-qualifier\-list struct\-declarator\-list*  **;**  
  
 *specifier\-qualifier\-list*:  
 *type\-specifier specifier\-qualifier\-list*  opt  
  
 *type\-qualifier specifier\-qualifier\-list*  opt  
  
 *struct\-declarator\-list*:  
 *struct\-declarator*  
  
 *struct\-declarator\-list*  **,**  *struct\-declarator*  
  
 **union** 類型的變數會儲存該類型所定義的其中一個值。  相同規則可管理結構和等位宣告。  等位也可以具有位元欄位。  
  
 等位的成員不能有不完整類型，也就是 `void` 類型或函式類型。  因此，成員不可以是等位的執行個體，但可以是所宣告等位類型的指標。  
  
 等位類型宣告只是一個樣板。  在變數宣告之前，記憶體不會保留。  
  
> [!NOTE]
>  如果宣告了兩種類型的等位並且儲存一個值，但等位是以另一種類型存取，則結果不可靠。  例如，宣告了 **float** 和 `int` 的等位。  儲存了 **float** 值，但是程式之後將值當做 `int` 存取。  在這種情況下，值會取決於 **float** 值的內部儲存區。  整數值會變得不可靠。  
  
## 範例  
 以下是等位的範例：  
  
```  
union sign   /* A definition and a declaration */  
{  
    int svar;  
    unsigned uvar;  
} number;  
```  
  
 這個範例會定義 `sign` 類型的等位變數，並宣告名為 `number` 且具有兩個成員的變數：`svar` 是帶正負號的整數，`uvar` 是不帶正負號的整數。  這個宣告可讓 `number` 的目前值儲存為帶正負號或不帶正負號的值。  與這個等位類型相關聯的標記為 `sign`。  
  
```  
union               /* Defines a two-dimensional */  
{                   /*  array named screen */  
    struct      
    {   
      unsigned int icon : 8;    
      unsigned color : 4;  
    } window1;  
    int screenval;  
} screen[25][80];  
```  
  
 `screen` 陣列包含 2,000 個元素。  陣列的每個元素都是具有兩個成員的個別等位：`window1` 和 `screenval`。  `window1` 成員是具有兩個位元欄位成員 `icon` 和 `color` 的結構。  `screenval` 成員為 `int`。  在任何特定時間，每個 union 項目都會保留 `screenval` 所表示的 `int`，或 `window1` 所表示的結構。  
  
 **Microsoft 特定的**  
  
 巢狀等位可以用匿名方式宣告 \(如果它們是另一個結構或等位的成員\)。  這是無名稱等位的範例：  
  
```  
struct str  
{  
    int a, b;  
    union            / * Unnamed union */  
    {  
      char c[4];  
      long l;  
      float f;  
   };  
   char c_array[10];  
} my_str;  
.  
.  
.  
my_str.l == 0L;  /* A reference to a field in the my_str union */  
```  
  
 等位在包括提供等位中任何特定時間所包含資料類型之欄位的結構中經常為巢狀。  這是這類等位的宣告範例：  
  
```  
struct x  
{  
    int type_tag;  
    union  
    {  
      int x;  
      float y;  
    }  
}  
```  
  
 如需參考等位的詳細資訊，請參閱[結構和等位成員](../c-language/structure-and-union-members.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [宣告子和變數宣告](../c-language/declarators-and-variable-declarations.md)