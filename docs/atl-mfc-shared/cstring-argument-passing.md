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
ms.openlocfilehash: 53977eb47520a20571a2d5ba8aa105c567ff40d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317925"
---
# <a name="cstring-argument-passing"></a>CString 引數傳遞

本文介紹如何將[CString](../atl-mfc-shared/reference/cstringt-class.md)物件傳遞到函數以及如何從函`CString`數返回 物件。

## <a name="cstring-argument-passing-conventions"></a><a name="_core_cstring_argument.2d.passing_conventions"></a>CString 參數傳遞約定

定義類介面時,必須確定成員函數的參數傳遞約定。 有一些標準規則用於傳遞和返回`CString`物件。 如果按照字串中描述的規則[為函數輸入](#_core_strings_as_function_inputs),[字串作為函數輸出](#_core_strings_as_function_outputs),您將具有高效、正確的代碼。

## <a name="strings-as-function-inputs"></a><a name="_core_strings_as_function_inputs"></a>字串為函數輸入

在調用的函數中使用`CString`物件的最有效和最安全的方法是`CString`將 物件傳遞給函數。 儘管名稱相同,`CString`但物件不會在內部儲存字串為具有空終止符的 C 樣式字串。 相反,`CString`物件會仔細跟蹤其具有的字元數。 提供`CString`指向 null 終止字串的 LPCTSTR 指標是少量工作,如果代碼必須不斷這樣做,這些工作可能會變得重要。 結果是暫時的,`CString`因為對內容的任何更改會使 LPCTSTR 指標的舊副本無效。

在某些情況下,提供 C 樣式字串確實有意義。 例如,在 C 中寫入被調用函數並且不支援物件的情況。 在這種情況下,強制參數`CString`到LPCTSTR,並且函數將獲得一個 C 樣式的 null 終止字串。 還可以採用另一個方向,並使用接受`CString`C 樣式字串`CString`參數 的構造函數創建物件。

如果要由函數更改字串內容,則將參數聲明為非常量`CString`參考 (`CString&`。

## <a name="strings-as-function-outputs"></a><a name="_core_strings_as_function_outputs"></a>字串為函數輸出

通常,可以從函數`CString`返回物件,因為`CString`物件遵循基元類型等值語義。 要傳回唯讀字串,請使用常數`CString`參考`const CString&`( 。 以下範例說明了`CString`參數和傳回類型的使用:

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>另請參閱

[字串(ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
