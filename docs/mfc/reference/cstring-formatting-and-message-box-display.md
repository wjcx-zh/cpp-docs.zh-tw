---
title: "CString 格式和訊息方塊顯示 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.strings
dev_langs:
- C++
helpviewer_keywords:
- CString objects, formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 48fc79f74bda10e43807d57fbcd7ed85fbb5d78b
ms.lasthandoff: 02/24/2017

---
# <a name="cstring-formatting-and-message-box-display"></a>CString 格式和訊息方塊顯示
函式的數目，可用於格式化和剖析`CString`物件。 您可以使用這些函式，當您需要管理`CString`物件，不過它們特別適用於格式化會出現在訊息方塊文字的字串。  
  
 此函式的群組也包含全域的常式，以顯示訊息方塊。  
  
### <a name="cstring-functions"></a>CString 函式  
  
|||  
|-|-|  
|[AfxExtractSubString](#afxextractsubstring)|擷取指定的來源字串中分隔單一字元的子字串。|  
|[AfxFormatString1](#afxformatstring1)|替代格式字元"%1"在字串中指定的字串包含在字串資料表中。|  
|[AfxFormatString2](#afxformatstring2)|取代兩個字串的格式字元 「 %1"和"%2"在字串中包含在字串資料表中。|  
|[AfxMessageBox](#afxmessagebox)|顯示訊息方塊。|  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="a-nameafxextractsubstringa--afxextractsubstring"></a><a name="afxextractsubstring"></a>AfxExtractSubString  
 此全域函式可用來從指定的來源字串擷取子字串。  
  
```   
BOOL AFXAPI AfxExtractSubString (
    CString& rString,  
    LPCTSTR lpszFullString,  
    int iSubString,  
    TCHAR chSep  = '\n'); 
```  
  
### <a name="parameters"></a>參數  
 *rString*  
 -   若要參考[CString](../../atl-mfc-shared/using-cstring.md)將會收到個別的子字串的物件。  
  
 *lpszFullString*  
 -   字串，包含要擷取之字串的全文檢索。  
  
 *iSubString*  
 -   要擷取之子字串之以零起始索引*lpszFullString*。  
  
 *chSep*  
 -   用來分隔的子字串的分隔符號字元。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果函式成功擷取的子字串，在提供的索引; 否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 此函式可用於擷取來源字串中的多個子字串時已知的單一字元分隔每一個子字串。 此函式會搜尋起點的`lpszFullString`參數每次呼叫時。  
  
 如果此函式會傳回 FALSE`lpszFullString`設為**NULL**或函式的結尾到達`lpszFullString`尋找沒有`iSubString`+&1; 指定的分隔符號字元出現次數。 `rString`參數將不會修改從其原始值如果`lpszFullString`設為**NULL**，否則`rString`參數設為空字串，如果無法擷取子字串，指定索引。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&48;](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="a-nameafxformatstring1a--afxformatstring1"></a><a name="afxformatstring1"></a>AfxFormatString1  
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
 [!code-cpp[NVC_MFC_Utilities #&25;](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="a-nameafxformatstring2a--afxformatstring2"></a><a name="afxformatstring2"></a>AfxFormatString2  
 所指向的字串，替代`lpsz1`字元"%1"，並指向任何的字串執行個體`lpsz2`所識別之範本字串資源中的字元"%2"的任何執行個體`nIDS`。  
  
```   
void AfxFormatString2(
    CString& rString,  
    UINT nIDS,  
    LPCTSTR lpsz1,  
    LPCTSTR lpsz2); 
```  
  
### <a name="parameters"></a>參數  
 `rString`  
 參考`CString`執行替代之後將包含結果字串。  
  
 `nIDS`  
 可執行替代的範本字串的字串資料表 ID。  
  
 `lpsz1`  
 將取代範本字串中格式字元「%1」的字串。  
  
 `lpsz2`  
 字串，將會取代先前的範本字串中字元"%2"。  
  
### <a name="remarks"></a>備註  
 新建構的字串儲存於 `rString`中。 例如，假設字串資料表中的字串是 「 檔案目錄 %2 中找不到 %1"，`lpsz1`指向 「 MYFILE。TXT"和`lpsz2`指向 「 C:\MYDIR 」，然後`rString`將包含字串"File MYFILE。TXT C:\MYDIR 目錄中找不到 」  
  
 如果格式字元 「 %1"或"%2"多次出現在字串中，將會進行多個替代作業。 它們並沒有數字的順序。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&26;](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="a-nameafxmessageboxa--afxmessagebox"></a><a name="afxmessagebox"></a>AfxMessageBox  
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
 指向`CString`物件或 null 結束的字串，包含顯示在訊息方塊中的訊息。  
  
 `nType`  
 訊息方塊樣式。 套用的任何[訊息方塊樣式](../../mfc/reference/message-box-styles.md)至方塊。  
  
 `nIDHelp`  
 說明內容識別碼的訊息;0 表示會使用應用程式的預設說明內容。  
  
 `nIDPrompt`  
 唯一識別碼，用來參考字串資料表中的字串。  
  
### <a name="return-value"></a>傳回值  
 如果記憶體不足，無法顯示訊息方塊中，為零否則，會傳回下列值之一︰  
  
- **IDABORT**已選取 [中止] 按鈕。  
  
- **IDCANCEL**已選取 [取消] 按鈕。  
  
- **IDIGNORE**已選取 [略過] 按鈕。  
  
- **IDNO**已選取 [否] 按鈕。  
  
- **IDOK**已選取 [確定] 按鈕。  
  
- **IDRETRY**重試 按鈕已選取。  
  
- **IDYES**已選取 [是] 按鈕。  
  
 如果訊息方塊已取消 按鈕， **IDCANCEL**會傳回值，如果按下 ESC 鍵或 取消 按鈕。 如果訊息方塊沒有 [取消] 按鈕，按下 ESC 鍵任何作用。  
  
 函式[AfxFormatString1](#afxformatstring1)和[AfxFormatString2](#afxformatstring2)可以用來格式化文字出現在訊息方塊中。  
  
### <a name="remarks"></a>備註  
 第一種形式的多載函式顯示的文字字串所指`lpszText`訊息方塊並使用`nIDHelp`來描述的說明內容。 說明內容用來跳到相關聯的 [說明] 主題，當使用者按下的說明鍵 (通常 F1)。  
  
 函式的第二個表單使用字串資源識別碼`nIDPrompt`顯示訊息方塊中的訊息。 相關聯的說明頁面找到的值透過`nIDHelp`。 如果預設值的`nIDHelp`用 (â €"1)，字串資源識別碼， `nIDPrompt`，用於說明內容。 如需定義說明內容的詳細資訊，請參閱[技術附註 28](../../mfc/tn028-context-sensitive-help-support.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&133;](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)   
 [CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)

