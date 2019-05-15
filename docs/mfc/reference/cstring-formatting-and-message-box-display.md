---
title: CString 格式和訊息方塊顯示
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: ad880c5302fd2274c5d46719e912461fd7497f10
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611008"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString 格式和訊息方塊顯示

提供數個函數來格式化和剖析`CString`物件。 您可以使用這些函式，每當您必須操作`CString`物件，但它們會特別有用，會出現在訊息方塊文字的字串進行格式化。

此函式群組也包含通用的常式，以顯示訊息方塊。

### <a name="cstring-functions"></a>CString 函式

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|擷取子字串從指定的來源字串分隔為單一字元。|
|[AfxFormatString1](#afxformatstring1)|替代格式字元"%1"在字串中指定的字串包含在字串資料表中。|
|[AfxFormatString2](#afxformatstring2)|取代兩個字串格式字元"%1"和"%2"的字串中包含在字串資料表中。|
|[AfxMessageBox](#afxmessagebox)|顯示訊息方塊。|

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxextractsubstring"></a>  AfxExtractSubString

此全域函式可用來從指定的來源字串擷取子字串。

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>參數

*rString*<br/>
若要參考[CString](../../atl-mfc-shared/using-cstring.md)會收到個別的子字串的物件。

*lpszFullString*<br/>
字串，包含要擷取之字串的完整文字。

*iSubString*<br/>
要擷取的子字串以零起始的索引*lpszFullString*。

*chSep*<br/>
用來分隔的子字串的分隔符號字元。

### <a name="return-value"></a>傳回值

如果函式成功擷取上提供的索引; 的子字串，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

此函式可用於從來源字串擷取多個子字串，當已知的單一字元來分隔每一個子字串。 此函式會搜尋從開頭*lpszFullString*參數每次呼叫時。

此函式會傳回 FALSE，如果有任一*lpszFullString*設為 NULL 或到達的結尾，函式*lpszFullString*而不需要尋找*iSubString*+ 1指定的分隔符號字元的項目。 *RString*參數將不會修改從其原始值如果*lpszFullString*已設為 NULL，否則*rString*參數設為空字串，如果無法擷取指定之索引子字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxformatstring1"></a>  AfxFormatString1

替代字串所指向*lpsz1*所識別的範本字串資源中的字元"%1"的任何執行個體*nIDS*。

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

新建構的字串會儲存在*rString*。 例如，如果字串資料表中的字串是 「 檔案 %1 找不到 」，並*lpsz1*等於"C:\MYFILE。TXT"，然後*rString*會包含字串"File C:\MYFILE。TXT 找不到 」。 此函式在為傳送到訊息方塊和其他視窗的字串進行格式化時，便可派上用場。

如果格式字元「%1」多次出現在字串中，將會進行多個替代作業。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxformatstring2"></a>  AfxFormatString2

替代字串所指向*lpsz1*所指向的字串的任何字元"%1"的執行個體*lpsz2*範本字串資源中的字元"%2"的任何執行個體由識別*nIDS*。

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>參數

*rString*<br/>
參考`CString`執行替代之後將包含結果的字串。

*nIDS*<br/>
會對其執行替代的範本字串的字串資料表 ID。

*lpsz1*<br/>
將取代範本字串中格式字元「%1」的字串。

*lpsz2*<br/>
範本字串中，將會取代格式的字串字元"%2"。

### <a name="remarks"></a>備註

新建構的字串會儲存在*rString*。 例如，如果字串資料表中的字串是 「 檔案 %1 目錄 %2 中找不到 」 *lpsz1*指向 「 MYFILE。TXT"，並*lpsz2*指向 「 C:\MYDIR\"，然後*rString*會包含字串"File MYFILE。TXT C:\MYDIR\ 目錄中找不到 」

如果格式字元 「 %1"或"%2"出現在字串中一次以上，將會進行多個替代項目。 它們沒有數字的順序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxmessagebox"></a>  AfxMessageBox

在螢幕上顯示的訊息方塊。

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
指向`CString`物件或 null 結束的字串，包含要在訊息方塊中顯示的訊息。

*nType*<br/>
訊息方塊的樣式。 套用的任何[訊息方塊樣式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)至方塊。

*nIDHelp*<br/>
訊息，說明內容識別碼0 表示將會使用應用程式的預設說明內容。

*nIDPrompt*<br/>
唯一的識別碼，用來參考字串資料表中的字串。

### <a name="return-value"></a>傳回值

如果不是記憶體不足，無法顯示訊息方塊中，則為零否則，會傳回下列值之一：

- 已選取 IDABORT [中止] 按鈕。

- 已選取 IDCANCEL [取消] 按鈕。

- 已選取 IDIGNORE [忽略] 按鈕。

- IDNO [否] 按鈕已選取。

- 已選取 IDOK [確定] 按鈕。

- 已選取 IDRETRY 重試 按鈕。

- 已選取 是 IDYES 按鈕。

如果訊息方塊有 [取消] 按鈕，將會傳回 IDCANCEL 值，如果按下 ESC 鍵，或選取 [取消] 按鈕。 如果訊息方塊沒有 [取消] 按鈕，按下 ESC 鍵任何作用。

函式[AfxFormatString1](#afxformatstring1)並[AfxFormatString2](#afxformatstring2)可用於格式化顯示在訊息方塊的文字。

### <a name="remarks"></a>備註

第一種形式的多載函式顯示的文字字串所指向*lpszText*在訊息方塊，並使用*nIDHelp*來描述說明內容。 說明內容用來跳到相關聯的 [說明] 主題，當使用者按下說明鍵 (通常是 F1)。

函式的第二個表單使用字串資源識別碼*nIDPrompt*顯示訊息方塊中的訊息。 相關聯的 說明 頁面找到的值透過*nIDHelp*。 如果預設值*nIDHelp*會使用 (-1)，字串資源 ID *nIDPrompt*，用於 「 說明 」 內容。 如需有關如何定義說明主題的詳細資訊，請參閱 <<c0> [ 技術提示 28](../../mfc/tn028-context-sensitive-help-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)
