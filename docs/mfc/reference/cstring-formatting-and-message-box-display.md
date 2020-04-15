---
title: CString 格式和訊息方塊顯示
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: d30d26ecf0e72ee33affe3df5b88c438ff83bb6b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365999"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString 格式和訊息方塊顯示

提供了許多函數來格式化和分析`CString`物件。 只要必須操作`CString`物件,都可以使用這些函數,但它們對於設置將顯示在消息框文本中的字串的格式特別有用。

這組函數還包括用於顯示消息框的全域例程。

### <a name="cstring-functions"></a>CString 函數

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|從給定源字串中提取由單個字元分隔的子字串。|
|[AfxFormatString1](#afxformatstring1)|將給定字串替換為字串表中包含的字串中的格式字元"%1"。|
|[AfxFormatString2](#afxformatstring2)|用兩個字串取代字串表中的格式字元「%1」和「%2」。|
|[AfxMessageBox](#afxmessagebox)|顯示訊息方塊。|

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a>Afx提取子字串

此全域函數可用於從給定源字串中提取子字串。

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>參數

*rString*<br/>
對將收到單個子字串的[CString](../../atl-mfc-shared/using-cstring.md)物件的引用。

*lpsz全字串*<br/>
包含要提取的字串的全文。

*iSubString*<br/>
從*lpszFullString*中提取的子字串的零基索引。

*chSep*<br/>
分隔符字元用於分隔子字串。

### <a name="return-value"></a>傳回值

如果函數成功提取了提供的索引上的子字串,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

當已知的單個字元分隔每個子字串時,此功能可用於從原始字串中提取多個子字串。 每次調用*lpszFullString*參數時,此函數都會從開始搜索。

如果*lpszFullString*設定為 NULL,或者該函數到達*lpszFullString*的末尾而不查找指定分隔符字元的*iSubString*+1 匹配項,則此功能將返回 FALSE。 如果將*lpszFullString*設置為 NULL,則*rString*參數將不會從其原始值修改;否則,如果無法為指定的索引提取子字串,則*rString*參數將設置為空字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a>AfxFormatString1

將*lpsz1*指向的字串取代為*nIDS*識別的樣本字串資源中字元"%1'的任何實例。

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>參數

*rString*<br/>
`CString` 物件的參考，在執行替代之後將會包含結果字串。

*Nids*<br/>
要執行替代作業之範本字串的資源 ID。

*lpsz1*<br/>
將取代範本字串中格式字元「%1」的字串。

### <a name="remarks"></a>備註

新形成的字串存儲在*rString*中。 例如,如果字串表中的字串為"找不到檔案 %1",並且*lpsz1*等於"C:\MYFILE"。TXT",然後*rString*將包含字串"檔C:\MYFILE。未找到 TXT"。 此函式在為傳送到訊息方塊和其他視窗的字串進行格式化時，便可派上用場。

如果格式字元「%1」多次出現在字串中，將會進行多個替代作業。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a>AfxFormatString2

將*lpsz1*指向的字串取代為字串'%1' 的任何實體,以及*lpsz2*指向字元'%2'的任何實體的字串,該字串位於*nIDS*識別的樣本字串資源中。

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>參數

*rString*<br/>
執行替換後將`CString`包含結果字串的對的引用。

*Nids*<br/>
將在其上執行替換的範本字串的字串的表 ID。

*lpsz1*<br/>
將取代範本字串中格式字元「%1」的字串。

*lpsz2*<br/>
將取代樣本字串的格式字元'%2'的字串。

### <a name="remarks"></a>備註

新形成的字串存儲在*rString*中。 例如,如果字串表中的字串是「在目錄 %2 中找不到檔案 %1」*,lpsz1*指向「MYFILE」。*TXT",lpsz2*指向"C:_MYDIR",然後*rString*將包含字串"檔MYFILE"。目錄 C 中找不到 TXT:\MYDIR"

如果格式字元'%1' 或 '%2' 在字串中多次顯示,則進行多次取代。 它們不必按數位順序排列。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a>AfxMessageBox

螢幕上顯示一個消息框。

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
指向包含`CString`要在消息框中顯示的消息的物件或空端結束的字串。

*nType*<br/>
消息框的樣式。 將任何[消息框樣式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)應用於該框。

*nIDHelp*<br/>
郵件的説明上下文 ID;0 表示將使用應用程式的預設説明上下文。

*NID提示*<br/>
用於參考字串表中的字串的唯一 ID。

### <a name="return-value"></a>傳回值

如果記憶體不足以顯示消息框,則為零;否則,返回以下值之一:

- 選擇中止按鈕。

- IDCANCEL"取消"按鈕已選定。

- 已選擇「忽略」按鈕。

- IDNO "沒有"按鈕已選中。

- IDOK 已選擇"確定"按鈕。

- 選擇重試按鈕。

- IDYES 選擇"是"按鈕。

如果消息框具有"取消"按鈕,則如果按下 ESC 鍵或選擇"取消"按鈕,則將返回 IDCANCEL 值。 如果消息框沒有"取消"按鈕,則按下 ESC 鍵不起作用。

函數[AfxFormatString1](#afxformatstring1)和[AfxFormatString2](#afxformatstring2)可用於設置消息框中顯示的文本的格式。

### <a name="remarks"></a>備註

此重載函數的第一種形式在消息框中顯示*lpszText*指向的文本字串,並使用*nIDHelp*來描述説明上下文。 當使用者按下幫助鍵(通常是 F1)時,説明上下文用於跳轉到關聯的幫助主題。

函數的第二種形式使用帶有 ID *nIDPrompt 的*字串資源在消息框中顯示一條消息。 關聯的幫助頁面通過*nIDHelp*的值找到。 如果使用*nIDHelp*的預設值 (-1),則字串資源 ID *nIDPrompt*將用於説明上下文。 有關定義説明上下文的詳細資訊,請參閱[技術說明 28](../../mfc/tn028-context-sensitive-help-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)
