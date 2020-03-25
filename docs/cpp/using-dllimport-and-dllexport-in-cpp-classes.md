---
title: 在 C++ 類別中使用 dllimport 和 dllexport
ms.date: 11/04/2016
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
ms.openlocfilehash: 7d67660fa3b5d57c56d02d5526f0a9ea294a8eef
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187826"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>在 C++ 類別中使用 dllimport 和 dllexport

**Microsoft 專屬**

您可以使用C++ **dllimport**或**dllexport**屬性來宣告類別。 這些形式表示會將整個類別匯入或匯出。 以這種方式匯出的類別稱為可匯出類別。

下列範例將定義可匯出類別。 它的所有成員函式和靜態資料都會匯出：

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

請注意，禁止在可匯出類別的成員上明確使用**dllimport**和**dllexport**屬性。

##  <a name="dllexport-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>dllexport 類別

當您宣告類別**dllexport**時，它的所有成員函式和靜態資料成員都會匯出。 您必須提供相同程式中所有這類成員的定義。 否則會產生連結器錯誤。 這項規則的例外狀況適用於純虛擬函式，您不需要為其提供明確定義。 不過，由於抽象類別的解構函式一定是由基底類別的解構函式所呼叫，因此純虛擬解構函式一定要提供定義。 請注意，這些規則同樣適用於不可匯出的類別。

如果您匯出類別類型的資料或傳回類別的函式，則務必匯出類別。

##  <a name="dllimport-classes"></a><a name="_pluslang_dllexport_classesdllexportclasses"></a>dllimport 類別

當您宣告類別**dllimport**時，它的所有成員函式和靜態資料成員都會匯入。 不同于非類別類型上的**dllimport**和**dllexport**行為，靜態資料成員無法在定義**dllimport**類別的相同程式中指定定義。

##  <a name="inheritance-and-exportable-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>繼承和可匯出類別

可匯出類別的所有基底類別都必須為可匯出。 否則會產生編譯器警告。 此外，同樣為類別的所有可存取成員也都必須為可匯出。 此規則允許**dllexport**類別繼承自**dllimport**類別，並使用**dllimport**類別繼承自**dllexport**類別（但不建議後者）。 通常，DLL 用戶端可以存取的所有項目 (根據 C++ 存取規則)，都必須是可匯出介面的一部分。 這包括內嵌函式中參考的 private 資料成員。

##  <a name="selective-member-importexport"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>選擇性成員匯入/匯出

因為成員函式和類別內的靜態資料會隱含具有外部連結，所以您可以使用**dllimport**或**dllexport**屬性來宣告它們，除非匯出整個類別。 如果匯入或匯出整個類別，則禁止將成員函式和資料明確宣告為**dllimport**或**dllexport** 。 如果您將類別定義中的靜態資料成員宣告為**dllexport**，則定義必須發生在相同程式中的某處（如同非類別外部連結）。

同樣地，您可以使用**dllimport**或**dllexport**屬性來宣告成員函式。 在此情況下，您必須在同一個程式內的某個位置提供**dllexport**定義。

關於選擇性成員匯入和匯出，有幾項重點值得注意：

- 選擇性成員匯入/匯出最適合用於提供較嚴格的匯出類別介面版本，也就是您可以為這個介面設計 DLL，公開比語言所允許更少的公用或私用功能。 另外也很適合用於微調可匯出介面：當您根據定義得知用戶端無法存取某些私用資料時，您不需要匯出整個類別。

- 如果您匯出類別中的某一個虛擬函式，就必須匯出所有虛擬函式，或是至少要提供用戶端可以直接使用的版本。

- 如果您在所擁有的類別中使用具有虛擬函式的選擇性成員匯入/匯出，這些函式必須位於可匯出介面中，或是定義為內嵌 (用戶端能夠看見)。

- 如果您將成員定義為**dllexport** ，但未將它包含在類別定義中，則會產生編譯器錯誤。 您必須在類別標頭中定義成員。

- 雖然允許將類別成員定義為**dllimport**或**dllexport** ，但是您無法覆寫在類別定義中指定的介面。

- 如果您在宣告它的類別定義主體以外的地方定義成員函式，則如果函式定義為**dllexport**或**dllimport** （如果這個定義不同于類別宣告中所指定的，則會產生警告）。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[dllexport、dllimport](../cpp/dllexport-dllimport.md)
