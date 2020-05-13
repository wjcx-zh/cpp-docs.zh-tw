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
ms.openlocfilehash: c0a2c96a37f58c956976980beafd5ecbed4d1318
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365110"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>在 C++ 類別中使用 dllimport 和 dllexport

**Microsoft 特定的**

可以使用**dllimport**或**dllexport**屬性聲明C++類。 這些形式表示會將整個類別匯入或匯出。 以這種方式匯出的類別稱為可匯出類別。

下列範例將定義可匯出類別。 它的所有成員函式和靜態資料都會匯出：

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

請注意,禁止在可匯出類的成員上顯式使用**dllimport**和**dllexport**屬性。

## <a name="dllexport-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>dllexport 類別

當您聲明類**dllexport**時,將匯出其所有成員函數和靜態數據成員。 您必須提供相同程式中所有這類成員的定義。 否則會產生連結器錯誤。 這項規則的例外狀況適用於純虛擬函式，您不需要為其提供明確定義。 不過，由於抽象類別的解構函式一定是由基底類別的解構函式所呼叫，因此純虛擬解構函式一定要提供定義。 請注意，這些規則同樣適用於不可匯出的類別。

如果您匯出類別類型的資料或傳回類別的函式，則務必匯出類別。

## <a name="dllimport-classes"></a><a name="_pluslang_dllexport_classesdllexportclasses"></a>dllimport 類別

當您聲明類**dllimport**時,將導入其所有成員函數和靜態數據成員。 與非類類型上的**dllimport**和**dllexport**行為不同,靜態數據成員無法在同一程式中指定定義**dllimport**類的定義。

## <a name="inheritance-and-exportable-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>繼承和可匯出類別

可匯出類別的所有基底類別都必須為可匯出。 否則會產生編譯器警告。 此外，同樣為類別的所有可存取成員也都必須為可匯出。 此規則允許**dllexport**類從**dllimport**類繼承 **,dllimport**類從**dllexport**類繼承(儘管不建議繼承後者)。 通常，DLL 用戶端可以存取的所有項目 (根據 C++ 存取規則)，都必須是可匯出介面的一部分。 這包括內嵌函式中參考的 private 資料成員。

## <a name="selective-member-importexport"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>選擇性成員匯入/匯出

由於類中的成員函數和靜態數據具有外部連結,因此可以使用**dllimport**或**dllexport**屬性聲明它們,除非匯出整個類。 如果導入或匯出整個類,則禁止成員函數和數據明確聲明為**dllimport**或**dllexport。** 如果將類定義中的靜態資料成員聲明為**dllexport,** 則定義必須發生在同一程式中的某處(與非類外部連結一樣)。

同樣,您可以使用**dllimport**或**dllexport**屬性聲明成員函數。 在這種情況下,您必須在同一程式中的某個位置提供**dllexport**定義。

關於選擇性成員匯入和匯出，有幾項重點值得注意：

- 選擇性成員匯入/匯出最適合用於提供較嚴格的匯出類別介面版本，也就是您可以為這個介面設計 DLL，公開比語言所允許更少的公用或私用功能。 另外也很適合用於微調可匯出介面：當您根據定義得知用戶端無法存取某些私用資料時，您不需要匯出整個類別。

- 如果您匯出類別中的某一個虛擬函式，就必須匯出所有虛擬函式，或是至少要提供用戶端可以直接使用的版本。

- 如果您在所擁有的類別中使用具有虛擬函式的選擇性成員匯入/匯出，這些函式必須位於可匯出介面中，或是定義為內嵌 (用戶端能夠看見)。

- 如果將成員定義為**dllexport,** 但不包括在類定義中,則產生編譯器錯誤。 您必須在類別標頭中定義成員。

- 儘管允許將類成員定義為**dllimport**或**dllexport,** 但不能覆蓋類定義中指定的介面。

- 如果在聲明該函數的類定義正文之外的其他位置定義成員函數,則如果該函數定義為**dllexport**或**dllimport(** 如果此定義與類聲明中指定的定義不同),則將發出警告。

**結束微軟的**

## <a name="see-also"></a>另請參閱

[dllexport、dllimport](../cpp/dllexport-dllimport.md)
