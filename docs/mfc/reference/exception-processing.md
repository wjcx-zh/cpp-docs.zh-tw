---
title: 例外狀況處理
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: 337fe03ab09a6ed3da283f45dd4eb58aaaad5bc5
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957493"
---
# <a name="exception-processing"></a>例外狀況處理

當程式執行時, 可能會發生一些異常情況和稱為「例外狀況」的錯誤。 這些可能包括記憶體不足、資源配置錯誤, 以及找不到檔案的問題。

MFC 程式庫使用的例外狀況處理配置, 會在 ANSI 標準委員會所提議的之後, 仔細模型化C++。 必須先設定例外狀況處理常式, 才能呼叫可能會遇到異常情況的函式。 如果函式遇到異常情況, 則會擲回例外狀況, 並將控制權傳遞給例外狀況處理常式。

MFC 程式庫所包含的數個宏將會設定例外狀況處理常式。 如有必要, 還有一些其他全域函式有助於擲回特定的例外狀況並終止程式。 這些宏和全域函式分成下列類別:

- 例外狀況宏, 這會為您的例外狀況處理常式進行結構。

- 例外狀況擲回的函式), 會產生特定類型的例外狀況。

- 終止函式, 這會造成程式終止。

如需範例和詳細資訊, 請參閱[例外](../../mfc/exception-handling-in-mfc.md)狀況一文。

### <a name="exception-macros"></a>例外狀況宏

|||
|-|-|
|[次](#try)|指定例外狀況處理的程式碼區塊。|
|[CATCH](#catch)|指定程式碼區塊, 以攔截上述**TRY**區塊中的例外狀況。|
|[CATCH_ALL](#catch_all)|指定程式碼區塊, 以攔截上述**TRY**區塊中的所有例外狀況。|
|[AND_CATCH](#and_catch)|指定程式碼區塊, 以攔截上述**TRY**區塊中的其他例外狀況類型。|
|[AND_CATCH_ALL](#and_catch_all)|指定程式碼區塊, 以攔截先前的**TRY**區塊中擲回的所有其他例外狀況類型。|
|[END_CATCH](#end_catch)|結束最後一個**CATCH**或**AND_CATCH**程式碼區塊。|
|[END_CATCH_ALL](#end_catch_all)|結束最後一個**CATCH_ALL**程式碼區塊。|
|[放棄](#throw)|擲回指定的例外狀況。|
|[THROW_LAST](#throw_last)|將目前處理的例外狀況擲回至下一個外部處理常式。|

### <a name="exception-throwing-functions"></a>例外狀況擲回函式

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|擲回封存例外狀況。|
|[AfxThrowFileException](#afxthrowfileexception)|擲回檔案例外狀況。|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|擲回不正確引數例外狀況。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|擲回記憶體例外狀況。|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|擲回不支援的例外狀況。|
|[AfxThrowResourceException](#afxthrowresourceexception)|擲回 Windows 資源-找不到的例外狀況。|
|[AfxThrowUserException](#afxthrowuserexception)|在使用者起始的程式動作中擲回例外狀況。|

MFC 提供兩個專門用於 OLE 例外狀況的例外狀況擲回函式:

### <a name="ole-exception-functions"></a>OLE 例外狀況函式

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|在 OLE automation 函數中擲回例外狀況。|
|[AfxThrowOleException](#afxthrowoleexception)|擲回 OLE 例外狀況。|

為了支援資料庫例外狀況, 資料庫類別提供了兩個例外`CDBException`狀況`CDaoException`類別, 以及和全域函式, 以支援例外狀況類型:

### <a name="dao-exception-functions"></a>DAO 例外狀況函式

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|從您自己的程式碼擲回[CDaoException](../../mfc/reference/cdaoexception-class.md) 。|
|[AfxThrowDBException](#afxthrowdbexception)|從您自己的程式碼擲回[CDBException](../../mfc/reference/cdbexception-class.md) 。|

MFC 提供下列終止函式:

### <a name="termination-functions"></a>終止函式

|||
|-|-|
|[AfxAbort](#afxabort)|呼叫以在發生嚴重錯誤時終止應用程式。|

##  <a name="try"></a>次

設定**TRY**區塊。

```
TRY
```

### <a name="remarks"></a>備註

**TRY**區塊會識別可能會擲回例外狀況的程式碼區塊。 這些例外狀況會在下列**CATCH**和**AND_CATCH**區塊中處理。 允許遞迴: 例外狀況可能會透過忽略它們或使用 THROW_LAST 宏, 傳遞至外部**TRY**區塊。 使用 END_CATCH 或 END_CATCH_ALL 宏來結束**TRY**區塊。

如需詳細資訊, 請參閱[例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="example"></a>範例

請參閱[CATCH](#catch)的範例。

### <a name="requirements"></a>需求

標頭：afx.h

##  <a name="catch"></a>  CATCH

定義程式碼區塊, 以攔截上述**TRY**區塊中擲回的第一個例外狀況類型。

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_class*<br/>
指定要測試的例外狀況類型。 如需標準例外狀況類別的清單, 請參閱類別[CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱來存取**CATCH**區塊內的 exception 物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 THROW_LAST 宏, 將處理轉移至下一個外部例外狀況框架。 以 END_CATCH 宏結束**TRY**區塊。

如果*exception_class*是類別`CException`, 則會攔截到所有例外狀況類型。 您可以使用[CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)成員函式來判斷所擲回的特定例外狀況。 捕捉幾種例外狀況的更好方法是使用順序**AND_CATCH**語句, 每個語句都有不同的例外狀況類型。

例外狀況物件指標是由宏所建立。 您不需要自行宣告。

> [!NOTE]
>  **CATCH**區塊會定義為以大C++括弧分隔的範圍。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。 這也適用于*exception_object_pointer_name*。

如需例外狀況和 CATCH 宏的詳細資訊, 請參閱[例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>  CATCH_ALL

定義程式碼區塊, 以攔截上述**TRY**區塊中擲回的所有例外狀況類型。

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_object_pointer_name*<br/>
指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `CATCH_ALL` 區塊中的例外狀況物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 `THROW_LAST` 巨集將處理移位到下個外部例外狀況框架。 如果您使用**CATCH_ALL**, 請使用 END_CATCH_ALL 宏結束**TRY**區塊。

> [!NOTE]
>  **CATCH_ALL**區塊會定義為以大C++括弧分隔的範圍。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。

如需例外狀況的詳細資訊, 請參閱[例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="example"></a>範例

請參閱[CFile:: Abort](../../mfc/reference/cfile-class.md#abort)的範例。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="and_catch"></a>AND_CATCH

定義程式碼區塊, 以攔截在先前的**TRY**區塊中擲回的其他例外狀況類型。

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_class*<br/>
指定要測試的例外狀況類型。 如需標準例外狀況類別的清單, 請參閱類別[CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
由宏所建立的例外狀況物件指標名稱。 您可以使用指標名稱來存取**AND_CATCH**區塊內的 exception 物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

使用 CATCH 宏來攔截一個例外狀況類型, 然後使用 AND_CATCH 宏來捕捉每個後續的類型。 以 END_CATCH 宏結束**TRY**區塊。

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫**AND_CATCH**區塊內的 THROW_LAST 宏, 將處理轉移至下一個外部例外狀況框架。 **AND_CATCH**會標示先前**CATCH**或**AND_CATCH**區塊的結尾。

> [!NOTE]
>  **AND_CATCH**區塊會定義為C++範圍 (以大括弧描繪)。 如果您在此範圍中宣告變數, 請記住它們只能在該範圍內進行存取。 這也適用于*exception_object_pointer_name*變數。

### <a name="example"></a>範例

請參閱[CATCH](#catch)的範例。

### <a name="requirements"></a>需求

  **標頭**afx。h
##  <a name="and_catch_all"></a>  AND_CATCH_ALL

定義程式碼區塊, 以攔截在先前的**TRY**區塊中擲回的其他例外狀況類型。

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_object_pointer_name*<br/>
由宏所建立的例外狀況物件指標名稱。 您可以使用指標名稱來存取**AND_CATCH_ALL**區塊內的 exception 物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

使用**catch**宏來攔截一個例外狀況類型, 然後使用 AND_CATCH_ALL 宏來捕捉所有其他後續的類型。 如果您使用 AND_CATCH_ALL, 請使用 END_CATCH_ALL 宏結束**TRY**區塊。

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫**AND_CATCH_ALL**區塊內的 THROW_LAST 宏, 將處理轉移至下一個外部例外狀況框架。 **AND_CATCH_ALL**會標示先前**CATCH**或**AND_CATCH_ALL**區塊的結尾。

> [!NOTE]
>  **AND_CATCH_ALL**區塊會定義為C++範圍 (以大括弧描繪)。 如果您在此範圍中宣告變數, 請記住它們只能在該範圍內進行存取。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="end_catch"></a>END_CATCH

標記最後一個**CATCH**或**AND_CATCH**區塊的結尾。

```
END_CATCH
```

### <a name="remarks"></a>備註

如需 END_CATCH 宏的詳細資訊, 請參閱[例外](../../mfc/exception-handling-in-mfc.md)狀況一文。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="end_catch_all"></a>END_CATCH_ALL

標記最後一個**CATCH_ALL88**或**AND_CATCH_ALL**區塊的結尾。

```
END_CATCH_ALL
```

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="throw"></a>THROW (MFC)

擲回指定的例外狀況。

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>參數

*exception_object_pointer*<br/>
指向衍生自`CException`的例外狀況物件。

### <a name="remarks"></a>備註

**擲**回會中斷程式執行, 並將控制權傳遞至程式中的相關聯**CATCH**區塊。 如果您尚未提供**CATCH**區塊, 則控制權會傳遞至會列印錯誤訊息並結束的 MFC 程式庫模組。

如需詳細資訊, 請參閱[例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="throw_last"></a>  THROW_LAST

將例外狀況擲回至下一個外部**CATCH**區塊。

```
THROW_LAST()
```

### <a name="remarks"></a>備註

此宏可讓您擲回本機建立的例外狀況。 如果您嘗試擲回您剛攔截到的例外狀況, 則通常會超出範圍並予以刪除。 使用**THROW_LAST**時, 會正確地將例外狀況傳遞至下一個**CATCH**處理常式。

如需詳細資訊, 請參閱[例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="example"></a>範例

請參閱[CFile:: Abort](../../mfc/reference/cfile-class.md#abort)的範例。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="afxthrowarchiveexception"></a>  AfxThrowArchiveException

擲回封存例外狀況。

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>參數

*cause*<br/>
指定表示例外狀況原因的整數。 如需可能值的清單, 請參閱[CArchiveException:: m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。

*lpszArchiveName*<br/>
指向字串, 其中包含造成例外狀況之`CArchive`物件的名稱 (如果有的話)。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="afxthrowfileexception"></a>  AfxThrowFileException

擲回檔案例外狀況。

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>參數

*cause*<br/>
指定表示例外狀況原因的整數。 如需可能值的清單, 請參閱[CFileException:: m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。

*lOsError*<br/>
包含指出例外狀況原因的作業系統錯誤號碼 (如果有的話)。 如需錯誤碼的清單, 請參閱您的作業系統手冊。

*lpszFileName*<br/>
指向字串, 其中包含造成例外狀況之檔案的名稱 (如果有的話)。

### <a name="remarks"></a>備註

您必須負責根據作業系統錯誤碼來判斷原因。

### <a name="requirements"></a>需求

  **標頭**afx。h

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException

擲回不正確引數例外狀況。

### <a name="syntax"></a>語法

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>備註

使用不正確引數時, 會呼叫這個函式。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxthrowmemoryexception"></a>  AfxThrowMemoryException

擲回記憶體例外狀況。

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>備註

如果對基礎系統記憶體配置器的呼叫 (例如**malloc**和[GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) Windows 函數) 失敗, 請呼叫此函式。 您不需要為**新**的呼叫它, 因為如果記憶體配置失敗,**新**的會自動擲回記憶體例外狀況。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="afxthrownotsupportedexception"></a>  AfxThrowNotSupportedException

會擲回例外狀況, 這是不支援之功能的要求結果。

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="afxthrowresourceexception"></a>  AfxThrowResourceException

擲回資源例外狀況。

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>備註

當無法載入 Windows 資源時, 通常會呼叫這個函式。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="afxthrowuserexception"></a>  AfxThrowUserException

會擲回例外狀況來停止使用者操作。

```
void AfxThrowUserException();
```

### <a name="remarks"></a>備註

此函式通常會在向`AfxMessageBox`使用者回報錯誤之後立即呼叫。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException

使用此函式在 OLE Automation 函式內擲回例外狀況。

```
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>參數

*wCode*<br/>
應用程式特定的錯誤碼。

*lpszDescription*<br/>
錯誤的詳細描述。

*nDescriptionID*<br/>
詳細錯誤描述的資源 ID。

*nHelpID*<br/>
您的應用程式說明 (.HLP) 檔的說明內容。

### <a name="remarks"></a>備註

提供給此函式的資訊可以透過驅動應用程式 (Microsoft Visual Basic 或其他 OLE Automation 用戶端應用程式) 來加以顯示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="afxthrowoleexception"></a>  AfxThrowOleException

建立類型`COleException`的物件, 並擲回例外狀況。

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>參數

*sc*<br/>
表示例外狀況原因的 OLE 狀態碼。

*hr*<br/>
結果碼的控制碼, 表示例外狀況的原因。

### <a name="remarks"></a>備註

接受 HRESULT 做為引數的版本, 會將該結果程式碼轉換成對應的 SCODE。 如需 HRESULT 和 SCODE 的詳細資訊, 請參閱 Windows SDK 中[COM 錯誤碼的結構](/windows/desktop/com/structure-of-com-error-codes)。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

##  <a name="afxthrowdaoexception"></a>  AfxThrowDaoException

呼叫此函式, 從您自己的程式碼擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的例外狀況。

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>參數

*nAfxDaoError*<br/>
表示 DAO 擴充錯誤碼的整數值, 它可以是[CDaoException:: m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)下所列的其中一個值。

*scode*<br/>
DAO 的 OLE 錯誤碼, 屬於 SCODE 類型。 如需相關資訊, 請參閱[CDaoException:: m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。

### <a name="remarks"></a>備註

架構也會呼叫`AfxThrowDaoException`。 在您的呼叫中, 您可以傳遞其中一個參數或兩者。 例如, 如果您想要引發**CDaoException:: nAfxDaoError**中所定義的其中一個錯誤, 但不在意*scode*參數, 請在*nAfxDaoError*參數中傳遞有效的程式碼, 並接受*scode*的預設值。

如需 MFC DAO 類別相關例外狀況的詳細資訊, 請`CDaoException`參閱本書中的類別和[文章例外狀況:資料庫例外](../../mfc/exceptions-database-exceptions.md)狀況。

### <a name="requirements"></a>需求

  **標頭**afxdb。h

##  <a name="afxthrowdbexception"></a>  AfxThrowDBException

呼叫此函式, 從您自己的`CDBException`程式碼擲回類型的例外狀況。

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
RETCODE 類型的值, 定義導致擲回例外狀況的錯誤類型。

*pdb*<br/>
`CDatabase`物件的指標, 表示與例外狀況相關聯的資料來源連接。

*hstmt*<br/>
ODBC HSTMT 控制碼, 指定與例外狀況相關聯的語句控制碼。

### <a name="remarks"></a>備註

當架構從`AfxThrowDBException`呼叫 odbc API 函式接收 odbc RETCODE, 並將 RETCODE 解讀為例外狀況, 而不是 expectable 錯誤時, 會呼叫。 例如, 資料存取作業可能會因為磁片讀取錯誤而失敗。

如需 ODBC 所定義之 RETCODE 值的相關資訊, 請參閱 Windows SDK 中的「取得狀態和錯誤資訊」第8章。 如需這些程式碼之 MFC 延伸模組的相關資訊, 請參閱類別[CDBException](../../mfc/reference/cdbexception-class.md)。

### <a name="requirements"></a>需求

  **標頭**afx。h

##  <a name="afxabort"></a>AfxAbort

MFC 提供的預設終止函式。

```
void  AfxAbort();
```

### <a name="remarks"></a>備註

`AfxAbort`發生嚴重錯誤 (例如無法處理的無法攔截的例外狀況) 時, MFC 成員函式會在內部呼叫。 當您遇到`AfxAbort`無法復原的嚴重錯誤時, 可以在罕見的情況下呼叫。

### <a name="example"></a>範例

請參閱[CATCH](#catch)的範例。

### <a name="requirements"></a>需求

  **標頭**afx。h

## <a name="see-also"></a>另請參閱

[宏和全域](mfc-macros-and-globals.md)<br/>
[CException 類別](cexception-class.md)<br/>
[CInvalidArgException 類別](cinvalidargexception-class.md)
