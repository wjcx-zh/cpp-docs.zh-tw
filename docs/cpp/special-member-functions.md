---
title: "特殊成員函式 |Microsoft 文件"
ms.custom: 
ms.date: 12/06/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
caps.latest.revision: 17
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
ms.openlocfilehash: 460e6e2ba25566cb4a2295ca4b35590405b51eb3
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="special-member-functions"></a>特殊成員函式  
  
*特殊成員函式*是類別 （或結構），在某些情況下，編譯器會自動為您產生的成員函式。 這些函式是[預設建構函式](constructors-cpp.md#default_constructors)、[解構函式](destructors-cpp.md)、[複製建構函式和複製指派運算子](copy-constructors-and-copy-assignment-operators-cpp.md)，而[移動建構函式和移動指派運算子](move-constructors-and-move-assignment-operators-cpp.md)。 如果您的類別未定義一或多個特殊成員函式，編譯器可能會以隱含方式宣告，然後定義所使用的函式。 編譯器產生的實作會呼叫*預設*特殊成員函式。 如果不需要它們，編譯器不會產生函式。  
  
您可以使用，以明確宣告的預設特殊成員函式`= default`關鍵字。 這會導致編譯器在函式才需要以相同方式如同不完全宣告的函式定義。 

在某些情況下，編譯器可能會產生*刪除*特殊成員函式，都不是已定義且因此無法呼叫。 這可能會發生在其中的類別上的特定的特殊成員函式的呼叫沒有意義，指定類別的其他內容的情況下。 若要明確地防止自動產生特殊成員函式，您可以將它宣告為已刪除使用`= delete`關鍵字。  
  
編譯器會產生*預設建構函式*，您未宣告任何其他建構函式時，才會採用任何引數的建構函式。 如果您宣告僅使用建構函式參數，嘗試呼叫預設建構函式的程式碼會導致編譯器產生的錯誤訊息。 編譯器產生的預設建構函式會執行簡單 member-wise[預設會初始化](initializers.md#default_initialization)的物件。 預設值初始化離開處於不定狀態的所有成員變數。  
  
預設解構函式會執行物件的成員解構。 只有當基底類別解構函式是虛擬的它是虛擬的。  
  
預設複製和移動建構和指派作業執行成員的位元模式複製或移動的非靜態資料成員。 移動作業只會產生當宣告時沒有解構函式或移動或複製作業。 宣告複製建構函式時，才會產生預設複製建構函式。 它是隱含地刪除宣告移動作業。 只有在沒有複製指派運算子已明確宣告時，會產生預設複製指派運算子。 它是隱含地刪除宣告移動作業。  
  
## <a name="see-also"></a>另請參閱  
[C++ 語言參考](cpp-language-reference.md)  



 

