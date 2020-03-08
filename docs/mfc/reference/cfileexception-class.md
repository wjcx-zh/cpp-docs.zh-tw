---
title: CFileException 類別
ms.date: 11/04/2016
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
ms.openlocfilehash: a3514c76d4136fe2bc0b096cc382e6f7f4dd3392
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855268"
---
# <a name="cfileexception-class"></a>CFileException 類別

表示檔案相關的例外狀況。

## <a name="syntax"></a>語法

```
class CFileException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|建構 `CFileException` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|傳回對應于執行時間錯誤號碼的原因程式碼。|
|[CFileException::GetErrorMessage](#geterrormessage)|抓取描述例外狀況的訊息。|
|[CFileException::OsErrorToException](#oserrortoexception)|傳回對應至作業系統錯誤碼的原因代碼。|
|[CFileException::ThrowErrno](#throwerrno)|根據執行階段錯誤號碼擲回檔案例外狀況。|
|[CFileException::ThrowOsError](#throwoserror)|根據作業系統錯誤號碼擲回檔案例外狀況。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CFileException：： m_cause](#m_cause)|包含對應至例外狀況原因的可移植程式碼。|
|[CFileException：： m_lOsError](#m_loserror)|包含相關的作業系統錯誤號碼。|
|[CFileException：： m_strFileName](#m_strfilename)|包含這個例外狀況的檔案名。|

## <a name="remarks"></a>備註

`CFileException` 類別包含的公用資料成員會保存可攜的原因程式碼和作業系統特定的錯誤號碼。 類別也提供靜態成員函式，用來擲回檔案例外狀況，以及傳回作業系統錯誤和 C 執行階段錯誤的原因代碼。

`CFileException` 物件會在 `CFile` 成員函式和衍生類別的成員函式中進行結構化和擲回。 您可以在**CATCH**運算式的範圍記憶體取這些物件。 針對可攜性，請只使用原因代碼來取得例外狀況的原因。 如需例外狀況的詳細資訊，請參閱[例外狀況處理（MFC）](../../mfc/exception-handling-in-mfc.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="cfileexception"></a>CFileException::CFileException

建立一個 `CFileException` 物件，將原因代碼和作業系統程式碼儲存在物件中。

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>參數

*cause*<br/>
列舉類型變數，指出例外狀況的原因。 如需可能值的清單，請參閱[CFileException：： m_cause](#m_cause) 。

*lOsError*<br/>
例外狀況的作業系統特定原因（如果有的話）。 *LOsError*參數提供的資訊會比*造成*的更多。

*lpszArchiveName*<br/>
指向字串，其中包含造成例外狀況之 `CFile` 物件的名稱。

### <a name="remarks"></a>備註

請勿直接使用此函式，而是呼叫全域函式[AfxThrowFileException](exception-processing.md#afxthrowfileexception)。

> [!NOTE]
>  變數*lOsError*只適用于 `CFile` 和 `CStdioFile` 物件。 `CMemFile` 類別不會處理此錯誤碼。

##  <a name="errnotoexception"></a>CFileException::ErrnoToException

將指定的執行時間程式庫錯誤值轉換為 `CFileException` 列舉的錯誤值。

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>參數

*nErrno*<br/>
執行時間 include 檔 ERRNO 中定義的整數錯誤碼。H.

### <a name="return-value"></a>傳回值

對應至指定執行時間程式庫錯誤值的列舉值。

### <a name="remarks"></a>備註

如需可能列舉值的清單，請參閱[CFileException：： m_cause](#m_cause) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>CFileException::GetErrorMessage

抓取描述例外狀況的文字。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>參數

*lpszError*<br/>
[in、out]接收錯誤訊息之緩衝區的指標。

*nMaxError*<br/>
在指定緩衝區可以保存的最大字元數。 這包括終止的 null 字元。

*pnHelpCoNtext*<br/>
[in、out]接收說明內容識別碼之不帶正負號整數的指標。 如果 `NULL`，則不會傳回任何識別碼。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果指定的緩衝區太小，則會截斷錯誤訊息。

### <a name="example"></a>範例

下列範例會使用 `CFileException::GetErrorMessage`。

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>CFileException：： m_cause

包含 `CFileException` 列舉類型所定義的值。

```
int m_cause;
```

### <a name="remarks"></a>備註

此資料成員是**int**類型的公用變數。列舉值和其意義如下：

- `CFileException::none` 0：未發生任何錯誤。

- `CFileException::genericException` 1：發生未指定的錯誤。

- `CFileException::fileNotFound` 2：找不到檔案。

- `CFileException::badPath` 3：路徑的全部或部分無效。

- `CFileException::tooManyOpenFiles` 4：已超過允許的開啟檔案數目。

- `CFileException::accessDenied` 5：無法存取檔案。

- `CFileException::invalidFile` 6：嘗試使用不正確檔案控制代碼。

- `CFileException::removeCurrentDir` 7：無法移除目前的工作目錄。

- `CFileException::directoryFull` 8：沒有其他目錄專案。

- `CFileException::badSeek` 9：嘗試設定檔案指標時發生錯誤。

- `CFileException::hardIO` 10：發生硬體錯誤。

- `CFileException::sharingViolation` 11：共用。未載入 EXE，或共用區域已鎖定。

- `CFileException::lockViolation` 12：嘗試鎖定已鎖定的區域。

- `CFileException::diskFull` 14：磁片已滿。

- `CFileException::endOfFile` 15：已到達檔案結尾。

    > [!NOTE]
    >  這些 `CFileException` 原因列舉程式不同於 `CArchiveException` 原因列舉程式。

    > [!NOTE]
    > `CArchiveException::generic` 已被取代。 請改用 `genericException`。 如果在應用程式中使用**泛型**，並以/clr 建立，則產生的語法錯誤不容易解密。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>CFileException：： m_lOsError

包含這個例外狀況的作業系統錯誤碼。

```
LONG m_lOsError;
```

### <a name="remarks"></a>備註

如需錯誤碼的清單，請參閱您的作業系統技術手冊。 此資料成員是 LONG 類型的公用變數。

##  <a name="m_strfilename"></a>CFileException：： m_strFileName

包含此例外狀況條件的檔案名。

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>CFileException::OsErrorToException

傳回對應至指定之*lOsError*值的枚舉器。 如果錯誤碼不明，則函數會傳回 `CFileException::generic`。

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>參數

*lOsError*<br/>
作業系統特定的錯誤碼。

### <a name="return-value"></a>傳回值

對應至指定作業系統錯誤值的列舉值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>CFileException::ThrowErrno

建立對應至給定*nErrno*值的 `CFileException` 物件，然後擲回例外狀況。

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>參數

*nErrno*<br/>
執行時間 include 檔 ERRNO 中定義的整數錯誤碼。H.

*lpszFileName*<br/>
字串的指標，其中包含造成例外狀況之檔案的名稱（如果有的話）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>CFileException::ThrowOsError

擲回對應至指定*lOsError*值的 `CFileException`。 如果錯誤碼不明，則函式會擲回編碼為 `CFileException::generic`的例外狀況。

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>參數

*lOsError*<br/>
作業系統特定的錯誤碼。

*lpszFileName*<br/>
字串的指標，其中包含造成例外狀況之檔案的名稱（如果有的話）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[例外狀況處理](../../mfc/reference/exception-processing.md)
