---
title: CString 格式和訊息方塊顯示
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: ad880c5302fd2274c5d46719e912461fd7497f10
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421125"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString 格式和訊息方塊顯示

提供一些函數來格式化和剖析 `CString` 物件。 只要您必須操控 `CString` 物件，就可以使用這些函式，但它們特別適用于格式化將顯示在訊息方塊文字中的字串。

這組函式也包含用於顯示訊息方塊的全域常式。

### <a name="cstring-functions"></a>CString 函式

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|以指定來源字串中的單一字元來解壓縮子字串。|
|[AfxFormatString1](#afxformatstring1)|在字串資料表所包含的字串中，以指定的字串取代格式字元 "%1"。|
|[AfxFormatString2](#afxformatstring2)|在字串資料表所包含的字串中，以兩個格式字元 "%1" 和 "%2" 取代字串。|
|[AfxMessageBox](#afxmessagebox)|顯示訊息方塊。|

### <a name="requirements"></a>需求

  **標頭**afxwin.h。h

##  <a name="afxextractsubstring"></a>AfxExtractSubString

這個全域函式可以用來從指定的來源字串解壓縮子字串。

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>參數

*rString*<br/>
會接收個別子字串之[CString](../../atl-mfc-shared/using-cstring.md)物件的參考。

*lpszFullString*<br/>
字串，包含要從中解壓縮之字串的全文文字。

*iSubString*<br/>
要從*lpszFullString*中解壓縮的子字串之以零為起始的索引。

*chSep*<br/>
用來分隔子字串的分隔符號。

### <a name="return-value"></a>傳回值

如果函式成功解壓縮所提供索引處的子字串，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當已知的單一字元分隔每個子字串時，此函式適用于從來源字串解壓縮多個子字串。 此函式會在每次呼叫*lpszFullString*參數的開頭進行搜尋。

如果其中一個*lpszFullString*設定為 Null，或函式到達*lpszFullString*的結尾，而未尋找指定分隔符號的*iSubString*+ 1，則此函式會傳回 FALSE。 如果*lpszFullString*設定為 Null， *rString*參數將不會從其原始值中修改。否則，如果無法針對指定的索引解壓縮子字串， *rString*參數會設定為空字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h。h

##  <a name="afxformatstring1"></a>AfxFormatString1

將*lpsz1*所指向的字串取代為*nIDS*所識別之範本字串資源中任何字元 "%1" 的實例。

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>參數

*rString*<br/>
`CString` 物件的參考，在執行替代之後將會包含結果字串。

*nIDS*<br/>
要執行替代作業之範本字串的資源 ID。

*lpsz1*<br/>
將取代範本字串中格式字元「%1」的字串。

### <a name="remarks"></a>備註

新形成的字串會儲存在*rString*中。 例如，如果字串資料表中的字串是「找不到檔案 %1」，而且*lpsz1*等於「C:\MYFILE。TXT "，則*rString*會包含字串" File C:\MYFILE。找不到 TXT」。 此函式在為傳送到訊息方塊和其他視窗的字串進行格式化時，便可派上用場。

如果格式字元「%1」多次出現在字串中，將會進行多個替代作業。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h。h

##  <a name="afxformatstring2"></a>AfxFormatString2

將*lpsz1*所指向的字串取代為任何字元 "%1" 的實例，並將*lpsz2*所指向的字串用於*nIDS*所識別的範本字串資源中任何字元 "%2" 的實例。

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>參數

*rString*<br/>
在執行替代之後，將包含結果字串之 `CString` 的參考。

*nIDS*<br/>
將在其上執行替代之範本字串的字串資料表識別碼。

*lpsz1*<br/>
將取代範本字串中格式字元「%1」的字串。

*lpsz2*<br/>
字串，將會取代範本字串中的格式字元 "%2"。

### <a name="remarks"></a>備註

新形成的字串會儲存在*rString*中。 例如，如果字串資料表中的字串是「在目錄 %2 中找不到檔案 %1」， *lpsz1*會指向「myfile.txt。TXT "，而*lpsz2*指向" C:\MYDIR "， *rString*會包含字串" File myfile.txt "。在目錄 C:\MYDIR 中找不到 TXT」

如果格式字元 "%1" 或 "%2" 出現在字串中超過一次，則會進行多個替代。 它們不一定要以數位順序排序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h。h

##  <a name="afxmessagebox"></a>AfxMessageBox

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

*lpszText*<br/>
指向 `CString` 物件或以 null 終止的字串，其中包含要顯示在訊息方塊中的訊息。

*nType*<br/>
訊息方塊的樣式。 將任何[訊息方塊樣式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)套用至方塊。

*nIDHelp*<br/>
訊息的說明內容識別碼;0表示將使用應用程式的預設說明內容。

*nIDPrompt*<br/>
唯一識別碼，用來參考字串資料表中的字串。

### <a name="return-value"></a>傳回值

如果沒有足夠的記憶體可顯示訊息方塊，則為零;否則，會傳回下列其中一個值：

- IDABORT 已選取 [中止] 按鈕。

- IDCANCEL 已選取 [取消] 按鈕。

- IDIGNORE 已選取 [略過] 按鈕。

- IDNO 已選取 [否] 按鈕。

- IDOK 已選取 [確定] 按鈕。

- IDRETRY 已選取 [重試] 按鈕。

- IDYES 已選取 [是] 按鈕。

如果訊息方塊具有 [取消] 按鈕，則在按下 ESC 鍵或選取 [取消] 按鈕時，就會傳回 IDCANCEL 值。 如果訊息方塊沒有 [取消] 按鈕，按下 ESC 鍵不會有任何作用。

函式[AfxFormatString1](#afxformatstring1)和[AfxFormatString2](#afxformatstring2)可用於格式化訊息方塊中顯示的文字。

### <a name="remarks"></a>備註

這個多載函式的第一個形式會顯示訊息方塊中*lpszText*所指向的文字字串，並使用*nIDHelp*來描述說明內容。 當使用者按下 [說明] 鍵（通常是 F1）時，會使用 [說明] 內容來跳到相關聯的說明主題。

函式的第二種形式會使用識別碼為*nIDPrompt*的字串資源，在訊息方塊中顯示訊息。 您可以透過*nIDHelp*的值找到相關聯的說明頁面。 如果使用*nIDHelp*的預設值（-1），則會使用字串資源識別碼*nIDPrompt*，做為說明內容。 如需定義說明內容的詳細資訊，請參閱[技術附注 28](../../mfc/tn028-context-sensitive-help-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>另請參閱

[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)
