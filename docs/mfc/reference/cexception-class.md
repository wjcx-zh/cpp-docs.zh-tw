---
title: CException 類別
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: e27802e05c832d28d848d9eb1235d6ef5980b306
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841554"
---
# <a name="cexception-class"></a>CException 類別

MFC 程式庫中所有例外狀況的基底類別。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CException：： CException](#cexception)|建構 `CException` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CException：:D elete](#delete)|刪除 `CException` 物件。|
|[CException：： ReportError](#reporterror)|將訊息方塊中的錯誤訊息報告給使用者。|

## <a name="remarks"></a>備註

因為 `CException` 是抽象基類，所以您無法 `CException` 直接建立物件; 您必須建立衍生類別的物件。 如果您需要建立自己的 `CException` 樣式類別，請使用上面所列的其中一個衍生類別做為模型。 請確定您的衍生類別也使用 `IMPLEMENT_DYNAMIC` 。

衍生的類別和其描述如下所示：

|名稱|描述|
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|資源關鍵 MFC 例外狀況的基類|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|不正確引數例外狀況條件|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|記憶體不足例外狀況|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|要求不支援的作業|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|封存特定例外狀況|
|[CFileException](../../mfc/reference/cfileexception-class.md)|檔案特定的例外狀況|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|找不到或無法為 Windows 資源|
|[COleException](../../mfc/reference/coleexception-class.md)|OLE 例外狀況|
|[CDBException](../../mfc/reference/cdbexception-class.md)|資料庫例外狀況 (也就是根據開放式資料庫連接而產生的 MFC 資料庫類別例外狀況) |
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|OLE 分派 (automation) 例外狀況|
|[CUserException](../../mfc/reference/cuserexception-class.md)|指出找不到資源的例外狀況|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|資料存取物件例外狀況 (也就是 DAO 類別所產生的例外狀況) |
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|網際網路例外狀況 (也就是) 的網際網路類別所產生的例外狀況。|

這些例外狀況適用于 [THROW](exception-processing.md#throw)、 [THROW_LAST](exception-processing.md#throw_last)、 [try](exception-processing.md#try)、 [catch](exception-processing.md#catch)、 [and_catch](exception-processing.md#and_catch)和 [end_catch](exception-processing.md#end_catch) 宏。 如需例外狀況的詳細資訊，請參閱 [例外狀況處理](exception-processing.md)，或參閱 [ (MFC) ](../exception-handling-in-mfc.md)的發行項例外狀況處理。

若要攔截特定的例外狀況，請使用適當的衍生類別。 若要攔截所有類型的例外狀況，請使用 `CException` ，然後使用 [CObject：： IsKindOf](cobject-class.md#iskindof) 來區分不同 `CException` 的衍生類別。 請注意， `CObject::IsKindOf` 僅適用于使用 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) 宏所宣告的類別，以便利用動態類型檢查。 `CException`您所建立的任何衍生類別也都應該使用 `IMPLEMENT_DYNAMIC` 宏。

您可以藉由呼叫 [GetErrorMessage](cfileexception-class.md#geterrormessage) 或 [ReportError](#reporterror)（可使用任何衍生類別的兩個成員函式），來向使用者報告例外狀況的詳細資料 `CException` 。

如果其中一個宏攔截到例外狀況，則 `CException` 會自動刪除物件; 請勿自行將其刪除。 如果使用關鍵字攔截到例外狀況 **`catch`** ，則不會自動刪除。 如需有關何時刪除 exeption 物件的詳細資訊，請參閱 [ (MFC) ](../exception-handling-in-mfc.md) 的文章例外狀況處理。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="cexceptioncexception"></a><a name="cexception"></a> CException：： CException

此成員函式會建立 `CException` 物件。

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*b_AutoDelete*<br/>
如果已在堆積上設定物件的記憶體，請指定 TRUE `CException` 。 這會導致在 `CException` `Delete` 呼叫成員函式來刪除例外狀況時，刪除物件。 如果 `CException` 物件在堆疊上或為全域物件，請指定 FALSE。 在此情況下， `CException` 當呼叫成員函式時，不會刪除物件 `Delete` 。

### <a name="remarks"></a>備註

您通常不需要直接呼叫此函式。 擲回例外狀況的函式應該建立衍生類別的實例， `CException` 並呼叫其函式，或是使用其中一個 MFC throw 函數（例如 [AfxThrowFileException](exception-processing.md#afxthrowfileexception)）來擲回預先定義的類型。 本檔僅提供完整性。

## <a name="cexceptiondelete"></a><a name="delete"></a> CException：:D elete

此函式會檢查是否 `CException` 已在堆積上建立物件，如果是，則會在 **`delete`** 物件上呼叫運算子。

```cpp
void Delete();
```

### <a name="remarks"></a>備註

刪除物件時 `CException` ，請使用成員函式 `Delete` 來刪除例外狀況。 請勿 **`delete`** 直接使用運算子，因為 `CException` 物件可能是全域物件，或已建立在堆疊上。

您可以指定是否要在建立物件時刪除物件。 如需詳細資訊，請參閱 [CException：： CException](#cexception)。

`Delete`如果您使用的是 c + + 機制，則只需要呼叫 **`try`** -  **`catch`** 。 如果您使用 MFC 宏 **TRY** 和 **CATCH**，則這些宏會自動呼叫此函式。

### <a name="example"></a>範例

```cpp
CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}
```

## <a name="cexceptionreporterror"></a><a name="reporterror"></a> CException：： ReportError

呼叫這個成員函式，將訊息方塊中的錯誤文字報告給使用者。

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>參數

*nType*<br/>
指定訊息方塊的樣式。 將 [訊息方塊樣式](styles-used-by-mfc.md#message-box-styles) 的任何組合套用至方塊。 如果您未指定此參數，則預設值為 MB_OK。

*nMessageID*<br/>
指定當例外狀況物件沒有錯誤訊息時，要顯示之訊息的資源識別碼 (字串資料表專案) 。 如果是0，則會顯示訊息「沒有可用的錯誤訊息」。

### <a name="return-value"></a>傳回值

`AfxMessageBox`值; 如果沒有足夠的記憶體可顯示訊息方塊，則為0。 如需可能的傳回值，請參閱 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) 。

### <a name="example"></a>範例

以下是使用的範例 `CException::ReportError` 。 如需其他範例，請參閱 [CATCH](exception-processing.md#catch)的範例。

```cpp
CFile fileInput;
CFileException ex;

// try to open a file for reading.
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>另請參閱

[CObject 類別](cobject-class.md)<br/>
[階層架構圖表](../hierarchy-chart.md)<br/>
[例外狀況處理](exception-processing.md)<br/>
[如何：建立我自己的自訂例外狀況類別](https://go.microsoft.com/fwlink/p/?linkid=128045)
