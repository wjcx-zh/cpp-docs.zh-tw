---
title: "extern 儲存類別指定名稱 | Microsoft Docs"
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
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: be8f7e83ef2157157c2cea241eefe49453e0060f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="extern-storage-class-specifier"></a>extern 儲存類別指定名稱
使用 `extern` 儲存類別規範宣告的變數是一個變數的參考，其與在任何程式原始程式檔的外部層級定義的變數具有相同名稱。 內部 `extern` 宣告用來使外部層級的變數定義在區塊內可見。 除非另外在外部層次宣告，否則使用 `extern` 關鍵字宣告的變數只有在其宣告的區塊中才可見。  
  
## <a name="example"></a>範例  
 下列範例說明內部和外部層級宣告：  
  
```  
// extern_StorageClassSpecified.c  
#include <stdio.h>  
  
void other( void );  
  
int main()  
{  
    // Reference to i, defined below:   
    extern int i;  
  
    // Initial value is zero; a is visible only within main:   
    static int a;  
  
    // b is stored in a register, if possible:   
    register int b = 0;  
  
    // Default storage class is auto:   
    int c = 0;  
  
    // Values printed are 1, 0, 0, 0:   
    printf_s( "%d\n%d\n%d\n%d\n", i, a, b, c );  
    other();  
    return;  
}  
  
int i = 1;  
  
void other( void )  
{  
    // Address of global i assigned to pointer variable:  
    static int *external_i = &i;  
  
    // i is redefined; global i no longer visible:   
    int i = 16;  
  
    // This a is visible only within the other function:   
    static int a = 2;  
  
    a += 2;  
    // Values printed are 16, 4, and 1:  
    printf_s( "%d\n%d\n%d\n", i, a, *external_i );  
}  
```  
  
 在此範例中，變數 `i` 是定義在外部層級，初始值為 1。 在 `extern` 函式中宣告 `main` 可用來宣告對外部層級 `i` 的參考。 因為省略了初始設定式，所以預設會將 **static** 變數 `a` 初始化為 0。 呼叫 `printf` 會列印值 1、0、0、和 0。  
  
 在 `other` 函式中，全域變數 `i` 的位址會用來初始化 **static** 指標變數 `external_i`。 因為全域變數具有 **static** 存留期，也就是說它的位址不會在程式執行期間變更，所以才能這樣運作。 接著，變數 `i` 會重新定義為初始值為 16 的區域變數。 這個重新定義不會影響外部層級 `i` 的值，它已由使用其區域變數的名稱所隱藏。 全域 `i` 的值現在只能在這個區塊中透過指標 `external_i` 進行間接存取。 嘗試將 **auto** 變數 `i` 的位址指派給指標將無法運作，因為每次進入區塊時可能會不同。 變數 `a` 會宣告為 **static** 變數並初始化為 2。 這個 `a` 與 `main` 中的 `a` 並不衝突，因為在內部層級的 **static** 變數只有在宣告變數的區塊內才可見。  
  
 變數 `a` 會增加 2，結果會是 4。 如果在同一個程式內再次呼叫 `other` 函式，`a` 的初始值將會是 4。 當程式結束然後重新進入其宣告區塊時，內部 **static** 變數會保留其值。  
  
## <a name="see-also"></a>另請參閱  
 [內部層級宣告的儲存類別規範](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
