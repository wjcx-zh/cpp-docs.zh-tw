---
title: "樣板和名稱解析 |Microsoft 文件"
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
ms.assetid: 519ba7b5-cd25-4549-865a-9a7b9dffdc28
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cb6708a8b7631551a6e245c0777bcc6c9fb1a92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="templates-and-name-resolution"></a>樣板和名稱解析

在樣板定義中共有三種類型的名稱。  
  
-   區域宣告名稱，包括樣板的名稱本身和樣板定義中宣告的任何名稱。  
  
-   來自樣板定義封閉範圍之外的名稱。  
  
-   以某種方式取決於樣板引數的名稱，也稱為相依名稱。  
  
 雖然前兩個名稱也屬於類別和函式範圍，不過在樣板定義中需要使用名稱解析的特殊規則來處理相依名稱增加的複雜度。 這是因為編譯器在樣板具現化之前對這些名稱幾乎一無所知，它們可能是完全不同的類型，取決於所使用的樣板引數。 非相依名稱會根據一般規則和樣板的定義點進行搜尋。 這些名稱 (與樣板引數無關) 只會針對所有樣板特製化搜尋一次。 相依名稱會在樣板具現化之後再進行搜尋，並且會分別對每個特製化進行搜尋。  
  
 類型取決於其相關的樣板引數。 具體來說，類型是相依的，如果其符合下列各項：  
  
-   樣板引數本身：  
  
    ```cpp
    T  
    ```  
  
-   具有限定性的限定名稱，包含一個相依類型：  
  
    ```cpp
    T::myType  
    ```  
  
-   一個限定名稱，但未限定部可識別一個相依類型：  
  
    ```cpp
    N::T  
    ```  
  
-   基底類型為相依類型的 const 或 volatile 類型：  
  
    ```cpp
    const T  
    ```  
  
-   以相依類型為基礎的指標、參考、陣列或函式指標類型：  
  
    ```cpp
    T *, T &, T [10], T (*)()  
    ```  
  
-   一個陣列，其大小取決於樣板參數：  
  
    ```cpp
    template <int arg> class X {  
    int x[arg] ; // dependent type  
    }  
    ```  
  
-   從樣板參數建構的範本類型：  
  
    ```cpp
    T<int>, MyTemplate<T>  
    ```  
  
## <a name="type-dependence-and-value-dependence"></a>類型相依和值相依

 相依於樣板參數的名稱和運算式會分類為類型相依或值相依，取決於樣板參數是型別參數或值參數。 此外，在具有類型相依的樣板中宣告的所有識別項在樣板引數上視為值相依，如使用值相依運算式初始化的整數或列舉類型。  
  
 類型相依和值相依運算式是一種包含類型相依或值相依變數的運算式。 根據範本所使用的參數，這些運算式可能會有不同的語意。  
  
## <a name="see-also"></a>請參閱

 [範本](../cpp/templates-cpp.md)
