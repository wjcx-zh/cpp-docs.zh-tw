---
title: "連結的類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
- linkage [C++], types of
- types [C++], linkage
- internal linkage, types of linkage
- external linkage, linkage types
ms.assetid: 41326c7f-4602-4bad-a648-697604858ba0
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: b4d5aca80e7b074c86a1446fabb9852f3b9fe3a9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="types-of-linkage"></a>連結的類型
物件和函式的名稱在轉譯單位之間共用的方式稱為「連結」(Linkage)。 這些名稱內可以包含：  
  
-   內部連結。在這種情況下，名稱只會參考本身轉譯單位內的程式項目，而不會與其他轉譯單位共用。  
  
     另一個轉譯單位中的相同名稱可能會參考不同的物件或不同的類別。 包含內部連結的名稱有時是指在其轉譯單位上。  
  
     包含內部連結的名稱宣告範例為：  
  
    ```  
    static int i;   // The static keyword ensures internal linkage.  
    ```  
  
-   外部連結。在這種情況下，它們會參考程式中任何轉譯單位的程式項目，程式項目會在轉譯單位之間共用。  
  
     另一個轉譯單位中的相同名稱一定會參考相同的物件或類別。 具有外部連結的名稱有時會稱為全域。  
  
     包含外部連結的名稱宣告範例為：  
  
    ```  
    extern int i;  
    ```  
  
-   無連結。在這種情況下，它們會參考唯一實體。 在另一個範圍內的相同名稱可能不會參考相同的物件。 範例為列舉  (不過，請注意，您可以將傳遞沒有連結之物件的指標。 這樣就可以在其他轉譯單位中存取該物件)。  
  
## <a name="see-also"></a>另請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)
