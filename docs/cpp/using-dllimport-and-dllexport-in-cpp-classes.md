---
title: C + + 類別中使用 dllimport 和 dllexport |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe1454ee615f489190ec455adabcd4bdecb4e0f0
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460816"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>在 C++ 類別中使用 dllimport 和 dllexport
## <a name="microsoft-specific"></a>Microsoft 特定的  
 您可以宣告具有 c + + 類別**dllimport**或是**dllexport**屬性。 這些形式表示會將整個類別匯入或匯出。 以這種方式匯出的類別稱為可匯出類別。  
  
 下列範例將定義可匯出類別。 它的所有成員函式和靜態資料都會匯出：  
  
```cpp 
#define DllExport   __declspec( dllexport )  
  
class DllExport C {  
   int i;  
   virtual int func( void ) { return 1; }  
};  
```  
  
 請注意，明確地使用**dllimport**並**dllexport**禁止使用可匯出類別的成員上的屬性。  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a> dllexport 類別  
 當您宣告類別**dllexport**，所有其成員函式和靜態資料成員都會匯出。 您必須提供相同程式中所有這類成員的定義。 否則會產生連結器錯誤。 這項規則的例外狀況適用於純虛擬函式，您不需要為其提供明確定義。 不過，由於抽象類別的解構函式一定是由基底類別的解構函式所呼叫，因此純虛擬解構函式一定要提供定義。 請注意，這些規則同樣適用於不可匯出的類別。  
  
 如果您匯出類別類型的資料或傳回類別的函式，則務必匯出類別。  
  
##  <a name="_pluslang_dllexport_classesdllexportclasses"></a> dllimport 類別  
 當您宣告類別**dllimport**，所有其成員函式和靜態資料成員都會匯入。 與行為的不同**dllimport**並**dllexport**非類別類型上的靜態資料成員無法所在的相同程式中指定的定義**dllimport**類別定義。  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a> 繼承和可匯出類別  
 可匯出類別的所有基底類別都必須為可匯出。 否則會產生編譯器警告。 此外，同樣為類別的所有可存取成員也都必須為可匯出。 此規則允許**dllexport**類別繼承自**dllimport**類別，以及**dllimport**類別繼承自**dllexport**類別 （雖然後者不建議）。 通常，DLL 用戶端可以存取的所有項目 (根據 C++ 存取規則)，都必須是可匯出介面的一部分。 這包括內嵌函式中參考的 private 資料成員。  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a> 選擇性成員匯入/匯出  
 成員函式和靜態類別內的資料以隱含方式具有外部連結，因為您可以將它們與宣告**dllimport**或是**dllexport**屬性，除非已匯出整個類別。 如果整個類別匯入或匯出，成員函式和資料明確宣告**dllimport**或是**dllexport**禁止使用。 如果您宣告為類別定義中的靜態資料成員**dllexport**，定義必須發生在某個位置相同的程式 （如同非類別外部連結）。  
  
 同樣地，您可以宣告成員函式與**dllimport**或是**dllexport**屬性。 在此情況下，您必須提供**dllexport**定義相同的程式中的某個位置。  
  
 關於選擇性成員匯入和匯出，有幾項重點值得注意：  
  
-   選擇性成員匯入/匯出最適合用於提供較嚴格的匯出類別介面版本，也就是您可以為這個介面設計 DLL，公開比語言所允許更少的公用或私用功能。 另外也很適合用於微調可匯出介面：當您根據定義得知用戶端無法存取某些私用資料時，您不需要匯出整個類別。  
  
-   如果您匯出類別中的某一個虛擬函式，就必須匯出所有虛擬函式，或是至少要提供用戶端可以直接使用的版本。  
  
-   如果您在所擁有的類別中使用具有虛擬函式的選擇性成員匯入/匯出，這些函式必須位於可匯出介面中，或是定義為內嵌 (用戶端能夠看見)。  
  
-   如果您定義做為成員**dllexport**但不是包含此類別定義中，則編譯器會產生錯誤。 您必須在類別標頭中定義成員。  
  
-   雖然為類別成員的定義**dllimport**或是**dllexport**是允許，您無法覆寫在類別定義中指定的介面。  
  
-   如果函式定義為，如果您在其宣告的類別定義主體之外定義成員函式，會產生警告**dllexport**或是**dllimport** （如果有這個定義不同於類別宣告中指定)。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)