---
title: "運算子多載的一般規則 |Microsoft 文件"
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
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 199db318eb847687d10044e0376b70c8d6d44feb
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="general-rules-for-operator-overloading"></a>運算子多載的一般規則
下列規則限制多載運算子的實作方式。 不過，它們不會套用到[新](../cpp/new-operator-cpp.md)和[刪除](../cpp/delete-operator-cpp.md)個別說明的運算子。  
  
-   您無法定義新的運算子，例如 **。  
  
-   將運算子套用於內建資料類型時，您就無法重新定義運算子的意義。  
  
-   多載運算子必須為非靜態類別成員函式或全域函式。 全域函式需要存取私用的或受保護的類別成員，必須宣告為該類別的 friend。 全域函式必須至少接受一個為類別或列舉類型或為類別或列舉類型參考的引數。 例如:   
  
    ```  
    // rules_for_operator_overloading.cpp  
    class Point  
    {  
    public:  
        Point operator<( Point & );  // Declare a member operator   
                                     //  overload.  
        // Declare addition operators.  
        friend Point operator+( Point&, int );  
        friend Point operator+( int, Point& );  
    };  
  
    int main()  
    {  
    }  
    ```  
  
     上述程式碼範例將小於運算子宣告為成員函式；不過，加法運算子會宣告為具有 friend 存取權限的全域函式。 請注意，可以對指定運算子提供一個以上的實作。 上述加法運算子的範例中，提供了兩個實作以協助交替。 可能可以實作將 `Point` 加入至 `Point`、將 `int` 加入至 `Point` 及諸如此類的運算子。  
  
-   運算子會遵守其優先順序、群組，以及其搭配內建類型使用時指定的運算元數目。 因此，沒有方式能夠表示概念 」 類型的物件中加入 2 和 3 `Point`，「 卻預期將 2 加入至*x*座標而將 3 加入至*y*協調。  
  
-   宣告為成員函式的一元運算子不接受任何引數；如果宣告為全域函式，則會接受一個引數。  
  
-   宣告為成員函式的二元運算子接受一個引數；如果宣告為全域函式，則會接受兩個引數。  
  
-   如果運算子可用來當做一元或二元運算子 (**&**，  **\*** ，  **+** ，和 **-** )，您可以個別多載每次使用。  
  
-   多載運算子不可以有預設引數。  
  
-   除了指派 (`operator=`)，所有的多載運算子都由衍生類別繼承。  
  
-   成員函式多載運算子的第一個引數，一定是叫用運算子之物件的類別類型 (宣告該運算子的類別，或者從該類別衍生的類別)。 不會對第一個引數提供任何轉換。  
  
 請注意，您可以完全改變任何運算子的意義。 其中包含位址的意義 (**&**)，指派 (**=**)，以及函式呼叫運算子。 此外，還可使用運算子多載變更內建類型所依賴的識別。 例如，下列四個陳述式若進行完整評估，通常是相等的：  
  
```  
var = var + 1;  
var += 1;  
var++;  
++var;  
```  
  
 多載運算子的類別類型無法依賴這個識別。 此外，就多載運算子而言，基本類型使用這些運算子的某些隱含條件比較不嚴謹。 例如，套用於基本類型時，加法/指派運算子 `+=` 會要求左運算元是左值；多載運算子時則沒有此項要求。  
  
> [!NOTE]
>  為求一致，最好的作法通常是在定義多載運算子時遵循內建類型的模型。 如果多載運算子的語意與其在其他內容中的意義大不相同，可能會比較容易混淆。  
  
## <a name="see-also"></a>另請參閱  
 [運算子多載](../cpp/operator-overloading.md)