---
title: "外部層級宣告的儲存類別指定名稱 | Microsoft Docs"
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
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 36adb7213c479a4324a34b0d750e9b012759b1d2
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>外部層級宣告的儲存類別指定名稱
外部變數是指在檔案範圍的變數。 這些變數是在任何函式之外定義，因此可能可供許多函式使用。 由於函式只能在外部層級定義，因此不可為巢狀。 根據預設，對相同名稱之外部變數和函式的所有參考都是相同物件的參考，這表示它們具有「外部連結」 (您可以使用 **static** 關鍵字覆寫此項。 如需有關 **static** 的詳細資訊，請參閱本節稍後的資訊)。  
  
 外部層級的變數宣告為變數的定義 (「定義宣告」)，或是於他處定義之變數的參考 (「參考宣告」)。  
  
 若外部變數宣告也會初始化變數 (隱含或明確)，則是定義變數的宣告。 外部層級的定義可採用數種形式：  
  
-   使用 **static** 儲存類別指定名稱宣告的變數。 您可以使用常數運算式來明確初始化 **static** 變數，如[初始化](../c-language/initialization.md)中所述。 如果您省略初始設定式，則預設會將變數初始化為 0。 例如，這兩個陳述式都視為變數 `k` 的定義。  
  
    ```  
    static int k = 16;  
    static int k;  
    ```  
  
-   您在外部層級明確初始化的變數。 例如，`int j = 3;` 是變數 `j` 的定義。  
  
 在外部層級 (也就是在所有函式之外) 的變數宣告中，您可以使用 **static** 或 `extern` 儲存類別指定名稱，或完全省略儲存類別指定名稱。 您無法在外部層級使用 **auto** 和 **register** *storage-class-specifier* 終端項。  
  
 一旦在外部層級定義變數，該變數在轉譯單位的所有其餘部分就會是可見狀態。 變數在相同原始程式檔中宣告之前為不可見。 此外，除非參考宣告讓該變數成為可見，否則它在程式的其他原始程式檔中也不可見，如下所述。  
  
 與 **static** 相關的規則包括：  
  
-   在所有區塊之外宣告且沒有 **static** 關鍵字的變數，在整個程式中一律會保留其值。 若要限制對特定轉譯單位的存取，您必須使用 **static** 關鍵字。 這樣做會為其提供「內部連結」。 若要讓變數在整個程式中成為全域，請省略明確儲存類別或使用關鍵字 `extern` (請參閱下一個清單中的規則)。 這樣做會為其提供「外部連結」。 內部和外部連結也將在[連結](../c-language/linkage.md)中加以討論。  
  
-   您只能在程式內於外部層級定義變數一次。 您可以在不同的轉譯單位中，定義另一個具有相同名稱和 **static** 儲存類別指定名稱的變數。 由於每個 **static** 定義只有在自己的轉譯單位內才可見，因此不會發生衝突。 這樣做提供了一種實用的方式，可以隱藏必須在單一轉譯單位的多個函式之間共用，但是不對其他轉譯單位顯示的識別項名稱。  
  
-   **static** 儲存類別指定名稱也可以套用至函式。 如果您將函式宣告為 **static**，它的名稱在宣告所在的檔案之外就不可見。  
  
 使用 `extern` 的規則包括：  
  
-   `extern` 儲存類別規範會宣告於他處定義之變數的參考。 您可以使用 `extern` 宣告讓定義在另一個原始程式檔中變成可見，或是讓變數在相同原始程式檔中定義之前變成可見。 一旦在外部層級宣告了變數的參考，變數就會在所宣告參考出現之轉譯單位的所有其餘部分變成可見。  
  
-   若要讓 `extern` 參考成為有效，它所參考的變數必須只能在外部層級定義一次。 這個定義 (沒有 `extern` 儲存類別) 可以位於組成程式的任何轉譯單位中。  
  
## <a name="example"></a>範例  
 下列範例將說明外部宣告：  
  
```  
/******************************************************************  
                      SOURCE FILE ONE   
*******************************************************************/  
#include <stdio.h>  
  
extern int i;                // Reference to i, defined below   
void next( void );           // Function prototype              
  
int main()  
{  
    i++;  
    printf_s( "%d\n", i );   // i equals 4   
    next();  
}  
  
int i = 3;                  // Definition of i  
  
void next( void )  
{  
    i++;  
    printf_s( "%d\n", i );  // i equals 5  
    other();  
}  
  
/******************************************************************  
                      SOURCE FILE TWO   
*******************************************************************/  
#include <stdio.h>  
  
extern int i;              // Reference to i in   
                           // first source file   
void other( void )  
{  
    i++;  
    printf_s( "%d\n", i ); // i equals 6   
}  
```  
  
 這個範例中的兩個原始程式檔總共包含三個 `i` 的外部宣告。 其中只有一個宣告為「定義宣告」。 該宣告：  
  
```  
int i = 3;  
```  
  
 會定義全域變數 `i` 並以初始值 3 將它初始化。 第一個原始程式檔頂端使用 `i` 之 `extern` 的「參考」宣告，會讓全域變數在檔案中它的定義宣告之前成為可見。 第二個原始程式檔中 `i` 的參考宣告也會讓變數在該原始程式檔中成為可見。 如果轉譯單位中未提供定義變數的執行個體，編譯器會假設有  
  
```  
extern int x;  
```  
  
 參考宣告，而且定義參考  
  
```  
int x = 0;  
```  
  
 出現在程式的另一個轉譯單位中。  
  
 這三個函式 `main`、`next` 和 `other` 全都會執行相同的工作：它們會增加並列印 `i`。 列印的值為 4、5 和 6。  
  
 如果變數 `i` 尚未初始化，則會自動設為 0。 在這種情況下會列印值 1、2 和 3。 如需變數初始化的詳細資訊，請參閱[初始化](../c-language/initialization.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C 儲存類別](../c-language/c-storage-classes.md)
