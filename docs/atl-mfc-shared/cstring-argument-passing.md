---
title: CString 引數傳遞 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 642ff20028a0929bb7bc11815e66b9f845ef9bd7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356826"
---
# <a name="cstring-argument-passing"></a>CString 引數傳遞
這篇文章說明如何將傳遞[CString](../atl-mfc-shared/reference/cstringt-class.md)物件為函式，以及如何傳回`CString`從函式的物件。  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a> CString 引數傳遞慣例  
 當您定義的類別介面時，您必須判斷成員函式的引數傳遞慣例。 有一些標準的規則，以便傳遞和傳回`CString`物件。 如果遵循所述的規則[字串做為函式輸入](#_core_strings_as_function_inputs)和[字串做為函式輸出](#_core_strings_as_function_outputs)，您必須有效，正確程式碼。  
  
##  <a name="_core_strings_as_function_inputs"></a> 做為函式的輸入字串  
 最有效率且安全的方式使用`CString`中呼叫的函式物件是傳遞`CString`函式的物件。 雖然名稱`CString`物件不會儲存字串內部為 C 樣式字串具有 null 結束字元。 相反地，`CString`物件會小心追蹤它所具有的字元數。 具有`CString`提供`LPCTSTR`以 null 終止字串的指標是少量就會變大，如果您的程式碼經常執行的工作。 結果是暫時性的因為任何變更，以`CString`內容會導致無效的舊複本`LPCTSTR`指標。  
  
 在某些情況下，以提供的 C 樣式字串，它就很重要。 例如，可以呼叫的函式以 C 撰寫和不支援物件的情況。 在此情況下，強制轉型`CString`參數`LPCTSTR`，函式將取得的 C 樣式 null 結尾字串。 您可以前往其他方向，並建立`CString`物件使用`CString`接受 C 樣式字串參數的建構函式。  
  
 若要變更函式的字串內容，將參數宣告為非常數`CString`參考 (**CString &**)。  
  
##  <a name="_core_strings_as_function_outputs"></a> 為函式輸出的字串  
 通常，您可以傳回`CString`從函式物件，因為`CString`物件遵循如同基本類型的實值語意。 若要傳回唯讀的字串，使用常數`CString`參考 (**const CString &**)。 下列範例說明使用`CString`參數和傳回型別：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

