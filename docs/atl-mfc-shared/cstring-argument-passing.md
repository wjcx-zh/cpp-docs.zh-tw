---
title: CString 引數傳遞
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
ms.openlocfilehash: 1729167786d71c107fe6a4369d5a0c7e7c8594f1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742203"
---
# <a name="cstring-argument-passing"></a>CString 引數傳遞

這篇文章說明如何傳遞[CString](../atl-mfc-shared/reference/cstringt-class.md)物件為函式，以及如何傳回`CString`從函式的物件。

##  <a name="_core_cstring_argument.2d.passing_conventions"></a> CString 引數傳遞慣例

當您定義的類別介面時，您必須決定您的成員函式的引數傳遞慣例。 有一些標準的規則，以便傳遞和傳回`CString`物件。 如果遵循所述的規則[做為函式的輸入字串](#_core_strings_as_function_inputs)並[字串做為函式的輸出](#_core_strings_as_function_outputs)，您會有有效、 正確的程式碼。

##  <a name="_core_strings_as_function_inputs"></a> 做為函式輸入的字串

最有效且安全的方式使用`CString`中呼叫的函式物件是將傳遞`CString`函式的物件。 儘管有此名稱，`CString`物件不會儲存字串，在內部為 C 樣式字串具有 null 結束字元。 相反地，`CString`物件會仔細追蹤它所具有的字元數。 具有`CString`提供 LPCTSTR 指標以 null 終止的字串是少量的工作，可能會比較長，如果您的程式碼必須不斷執行它。 結果是暫時性的因為任何變更，以`CString`內容失效的 LPCTSTR 指標的舊複本。

有意義在某些情況下提供的 C 樣式字串。 例如，可以呼叫的函式以 C 撰寫，而不支援物件的情況。 在此情況下，強制轉型`CString`參數，以 LPCTSTR，且函式會取得與 C 樣式 null 結尾的字串。 您也可以進入另一個方向，並建立`CString`物件使用`CString`接受 C 樣式字串參數的建構函式。

如果字串的內容變更函式，宣告為非常數參數`CString`參考 (`CString&`)。

##  <a name="_core_strings_as_function_outputs"></a> 函式的輸出為字串

通常，您可以返回`CString`物件從函式，因為`CString`物件遵循基本類型類似的實值語意。 若要傳回唯讀的字串，使用常數`CString`參考 (`const CString&`)。 下列範例示範如何將`CString`參數和傳回型別：

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>另請參閱

[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
