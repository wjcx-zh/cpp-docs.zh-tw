---
title: "Catch 區塊的方式進行評估 （c + +） |Microsoft 文件"
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
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
caps.latest.revision: 7
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1098529effb3a15d8f6260ed7167c5553b226857
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="how-catch-blocks-are-evaluated-c"></a>評估 Catch 區塊的方式 (C++)
C++ 可讓您擲回任何類型的例外狀況，不過，一般建議擲回衍生自 std::exception 的類型。 可以攔截 c + + 例外狀況**攔截**指定相同的型別，擲回的例外狀況，或可以攔截任何類型的例外狀況處理常式的處理常式。  
  
 如果擲回的例外狀況類型是類別，而該類別同時擁有一個或多個基底類別，則可以使用接受例外狀況類型的基底類別，以及接受例外狀況類型之基底參考的處理常式攔截例外狀況。 請注意，如果是以參考攔截例外狀況，它會繫結程序至實際擲回的例外狀況物件，否則它會是複本 (就如同函式的引數)。  
  
 擲回例外狀況時，它一定會攔截由下列類型的**攔截**處理常式：  
  
-   可以接受任何類型的處理常式 (使用省略語法)。  
  
-   接受與例外狀況物件相同類型的處理常式因為它是複本， **const**和`volatile`修飾詞會被忽略。  
  
-   可以接受與例外狀況物件相同類型之參考的處理常式。  
  
-   接受的參考的處理常式**const**或`volatile`例外狀況物件相同類型的表單。  
  
-   接受與例外狀況物件相同類型的基底類別的處理常式因為它是複本， **const**和`volatile`修飾詞會被忽略。 **攔截**基底類別處理常式必須前面**攔截**衍生類別處理常式。  
  
-   可以接受與例外狀況物件相同類型的基底類別之參考的處理常式。  
  
-   接受的參考的處理常式**const**或`volatile`表單的基底類別的例外狀況物件相同的型別。  
  
-   可以接受指標的處理常式，擲回的指標物件可以透過標準指標轉換規則轉換成該指標。  
  
 順序**攔截**處理常式會出現相當重要，因為處理常式指定**再試一次**區塊會檢查其出現的順序。 例如，將基底類別的處理常式放在衍生類別的處理常式前面就是錯誤的範例。 比對之後**攔截**找不到處理常式，就不會檢查後續處理常式。 如此一來，省略符號**攔截**處理常式必須是最後一個處理常式，如其**再試一次**區塊。 例如:   
  
```  
// ...  
try  
{  
    // ...  
}  
catch( ... )  
{  
    // Handle exception here.  
}  
// Error: the next two handlers are never examined.  
catch( const char * str )  
{  
    cout << "Caught exception: " << str << endl;  
}  
catch( CExcptClass E )  
{  
    // Handle CExcptClass exception here.  
}  
```  
  
 在此範例中，省略符號**攔截**處理常式是唯一會進行檢查的處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 例外狀況處理](../cpp/cpp-exception-handling.md)
