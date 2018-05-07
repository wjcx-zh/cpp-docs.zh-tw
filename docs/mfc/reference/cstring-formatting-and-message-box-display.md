---
title: CString 格式和訊息方塊顯示 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.strings
dev_langs:
- C++
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8074d84d739b59acfa0c6040bedf76f46b6ea9c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cstring-formatting-and-message-box-display"></a>CString 格式和訊息方塊顯示
提供數個函數來格式化和剖析`CString`物件。 您可以使用這些函式，只要有操作`CString`物件，但它們會特別有用，會出現在訊息方塊文字的字串進行格式化。  
  
 此群組的函式也包含全域的常式，以顯示訊息方塊。  
  
### <a name="cstring-functions"></a>CString 函式  
  
|||  
|-|-|  
|[AfxExtractSubString](#afxextractsubstring)|擷取指定的來源字串中分隔單一字元的子字串。|  
|[AfxFormatString1](#afxformatstring1)|取代字串中格式字元 「 %1"的指定的字串包含在字串資料表。|  
|[AfxFormatString2](#afxformatstring2)|以兩個字串的格式字元 「 %1"和"%2"在字串中包含在字串資料表中。|  
|[AfxMessageBox](#afxmessagebox)|顯示訊息方塊。|  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxextractsubstring"></a>  AfxExtractSubString  
 此全域函式可以用來從指定的來源字串擷取子字串。  
  
```   
BOOL AFXAPI AfxExtractSubString (
    CString& rString,  
    LPCTSTR lpszFullString,  
    int iSubString,  
    TCHAR chSep  = '\n'); 
```  
  
### <a name="parameters"></a>參數  
 *rString*  
 -   若要參考[CString](../../atl-mfc-shared/using-cstring.md)將收到個別的子字串的物件。  
  
 *lpszFullString*  
 -   字串，包含要擷取之字串的全文檢索。  
  
 *iSubString*  
 -   以零為起始的索引，要擷取之子字串*lpszFullString*。  
  
 *chSep*  
 -   用來分隔的子字串的分隔符號字元。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果函式成功擷取的子字串在提供的索引; 否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 此函式可用於擷取來源字串中的多個子字串時已知的單一字元會分隔每一個子字串。 此函式會搜尋的起點的`lpszFullString`參數每次呼叫時。  
  
 此函式會傳回 FALSE，如果`lpszFullString`設為**NULL**或函式達到結尾`lpszFullString`尋找沒有`iSubString`+ 1 出現指定的分隔符號字元。 `rString`參數將不會修改從其原始值如果`lpszFullString`設**NULL**，否則`rString`如果無法擷取子字串參數設為空字串指定索引。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxformatstring1"></a>  AfxFormatString1  
 用 `lpsz1` 指向的字串，替代由 `nIDS`所識別之範本字串資源中字元「%1」的任何執行個體。  
  
```  
void  AfxFormatString1(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1); 
```  
  
### <a name="parameters"></a>參數  
 `rString`  
 `CString` 物件的參考，在執行替代之後將會包含結果字串。  
  
 `nIDS`  
 要執行替代作業之範本字串的資源 ID。  
  
 `lpsz1`  
 將取代範本字串中格式字元「%1」的字串。  
  
### <a name="remarks"></a>備註  
 新建構的字串儲存於 `rString`中。 例如，假設字串資料表中的字串是「找不到檔案 %1」，而 `lpsz1` 等於「C:\MYFILE.TXT」，則 `rString` 將會包含字串「找不到檔案 C:\MYFILE.TXT」。 此函式在為傳送到訊息方塊和其他視窗的字串進行格式化時，便可派上用場。  
  
 如果格式字元「%1」多次出現在字串中，將會進行多個替代作業。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxformatstring2"></a>  AfxFormatString2  
 替代字串所指向`lpsz1`字元"%1"和字串所指向的任何執行個體`lpsz2`所識別的範本字串資源中的字元"%2"的任何執行個體`nIDS`。  
  
```   
void AfxFormatString2(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1,  
    LPCTSTR lpsz2); 
```  
  
### <a name="parameters"></a>參數  
 `rString`  
 若要參考`CString`執行替代之後將包含結果的字串。  
  
 `nIDS`  
 可執行替代的範本字串的字串資料表識別碼。  
  
 `lpsz1`  
 將取代範本字串中格式字元「%1」的字串。  
  
 `lpsz2`  
 將會取代格式字串的範本字串中字元"%2"。  
  
### <a name="remarks"></a>備註  
 新建構的字串儲存於 `rString`中。 例如，如果字串資料表中的字串是 「 檔案 %1 目錄 %2 中找不到 」`lpsz1`指向 「 MYFILE。TXT"和`lpsz2`指向 「 C:\MYDIR"，然後`rString`將包含字串"File MYFILE。TXT C:\MYDIR 目錄中找不到"  
  
 如果格式字元 「 %1"或"%2"出現在字串中一次以上，將會進行多個替代項目。 它們不必是數字的順序。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxmessagebox"></a>  AfxMessageBox  
 在畫面上顯示訊息方塊。  
  
```  
int AfxMessageBox(
    LPCTSTR lpszText,  
    UINT nType = MB_OK,  
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,  
    UINT nType = MB_OK,  
    UINT nIDHelp = (UINT) -1); 
```  
  
### <a name="parameters"></a>參數  
 `lpszText`  
 指向`CString`物件或 null 結束的字串，包含要顯示在訊息方塊中的訊息。  
  
 `nType`  
 訊息方塊樣式。 套用這其中任何[訊息方塊樣式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)到方塊。  
  
 `nIDHelp`  
 說明內容識別碼的訊息。0 表示會使用應用程式的預設說明內容。  
  
 `nIDPrompt`  
 唯一識別碼，用來參考字串資料表中的字串。  
  
### <a name="return-value"></a>傳回值  
 如果不是記憶體不足，無法顯示訊息方塊，則為零否則，會傳回下列值之一：  
  
- **IDABORT**中止按鈕已選取。  
  
- **IDCANCEL**已選取 [取消] 按鈕。  
  
- **IDIGNORE**已選取 [忽略] 按鈕。  
  
- **IDNO**已選取 [否] 按鈕。  
  
- **IDOK**已選取 [確定] 按鈕。  
  
- **IDRETRY**重試 按鈕已選取。  
  
- **IDYES**已選取 [是] 按鈕。  
  
 如果訊息方塊具有 取消 按鈕， **IDCANCEL**如果按下 ESC 鍵，或選取取消 5d; 按鈕，將會傳回值。 如果訊息方塊具有不到 [取消] 按鈕，按 ESC 鍵任何作用。  
  
 函式[AfxFormatString1](#afxformatstring1)和[AfxFormatString2](#afxformatstring2)可以用來設定出現在訊息方塊的文字格式。  
  
### <a name="remarks"></a>備註  
 第一種形式的多載函式顯示的文字字串所指向`lpszText`在訊息方塊，並使用`nIDHelp`來描述說明內容。 說明內容用來跳到相關的說明主題，當使用者按下的說明鍵 (通常 F1)。  
  
 函式的第二個表單使用字串資源識別碼`nIDPrompt`顯示訊息方塊中的訊息。 相關聯的說明頁面透過值找到`nIDHelp`。 如果預設值的`nIDHelp`為使用 (-1)，字串資源識別碼`nIDPrompt`，用於說明內容。 如需定義說明內容的詳細資訊，請參閱[技術附註 28](../../mfc/tn028-context-sensitive-help-support.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)   
 [CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)
