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
ms.openlocfilehash: c3742db7475e626b18e9c073a0b7417a8034863f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373944"
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
|[例外::例外](#cexception)|建構 `CException` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[例::Delete](#delete)|刪除`CException`物件。|
|[例外:報告錯誤](#reporterror)|向使用者報告訊息框中的錯誤消息。|

## <a name="remarks"></a>備註

因為`CException`是一個抽象的基類`CException`, 你不能直接創建物件;必須創建派生類的物件。 如果需要創建自己的`CException`樣式類,請使用上面列出的派生類之一作為模型。 確保衍生類別使用`IMPLEMENT_DYNAMIC`。

派生類及其描述如下:

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|資源關鍵型 MFC 異常的基類|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|不合法參數例外條件|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|記憶體不足異常|
|[不支援例外](../../mfc/reference/cnotsupportedexception-class.md)|要求不支援的作業|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|特定於存檔的例外|
|[CFileException](../../mfc/reference/cfileexception-class.md)|檔案的例外|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|找不到或無法建立的視窗資源|
|[COleException](../../mfc/reference/coleexception-class.md)|OLE 例外|
|[CDBException](../../mfc/reference/cdbexception-class.md)|資料庫異常(即基於開放資料庫連線的 MFC 資料庫類別產生的異常條件)|
|[COle排程](../../mfc/reference/coledispatchexception-class.md)|OLE 調度 (自動化)異常|
|[CUserException](../../mfc/reference/cuserexception-class.md)|指示找不到資源的例外|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|資料存取物件異常(即 DAO 類別產生的例外條件)|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|互聯網例外(即,互聯網類產生的異常條件)。|

這些異常旨在與[try](exception-processing.md#try)[THROW](exception-processing.md#throw)[THROW、THROW_LAST、](exception-processing.md#throw_last)嘗試、[捕獲](exception-processing.md#catch)[、and_catch](exception-processing.md#and_catch)和[end_catch](exception-processing.md#end_catch)宏一起使用。 有關異常的詳細資訊,請參閱[異常處理](exception-processing.md),或請參閱文章[異常處理 (MFC)。](../exception-handling-in-mfc.md)

要捕獲特定異常,請使用相應的派生類。 要捕捉所有類型的異常,請使用,`CException`然後使用[CObject::isKindOf](cobject-class.md#iskindof)來`CException`區分 派生類。 請注意,`CObject::IsKindOf`僅適用於使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)宏聲明的類,以便利用動態類型檢查。 您`CException`創建的任何派生類也應使用`IMPLEMENT_DYNAMIC`宏。

您可以通過調用[GetErrorMessage](cfileexception-class.md#geterrormessage)或[ReportError](#reporterror)向使用者報告有關異常的詳細資訊,這兩個`CException`成員函數適用於任何 派生類。

如果某個宏捕獲了異常,則會自動刪除該物件;`CException`如果某個宏捕獲異常,則會自動刪除該物件。不要自己刪除它。 如果使用**catch**關鍵字捕獲異常,則不會自動刪除該異常。 有關何時刪除解斥物件的詳細資訊,請參閱文章[異常處理 (MFC)。](../exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cexceptioncexception"></a><a name="cexception"></a>例外::例外

此成員函式建構物件`CException`。

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*b_AutoDelete*<br/>
如果`CException`物件的記憶體已在堆上分配,請指定 TRUE。 這將導致在`CException`調用`Delete`成員函數刪除異常時刪除物件。 如果物件位於堆`CException`棧上或是全域物件,請指定 FALSE。 在這種情況下,`CException`在呼`Delete`叫成員函數時不會刪除該物件。

### <a name="remarks"></a>備註

您通常不需要直接呼叫此建構函數。 引發異常的函數應創建`CException`派生類的實例並調用其構造函數,或者它應該使用 MFC 引發函數之一(如[AfxThrowFileexception)](exception-processing.md#afxthrowfileexception)來引發預定義類型。 本文檔僅用於完整性。

## <a name="cexceptiondelete"></a><a name="delete"></a>例::Delete

此函數檢查`CException`物件是否在堆上創建,如果是,它將調用物件上的**delete**運算符。

```
void Delete();
```

### <a name="remarks"></a>備註

刪除物件時`CException`,`Delete`請使用成員函數刪除異常。 不要直接使用**刪除**運算符,`CException`因為 物件可能是全域物件或在堆疊上創建的。

您可以指定在建構物件時是否應刪除該物件。 有關詳細資訊,請參閱["例外::例例](#cexception)"。

僅當使用C++`Delete`**嘗試**- **捕獲**機制時,才需要調用。 如果使用 MFC 宏**TRY**和**CATCH,** 則這些宏將自動呼叫此函數。

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

## <a name="cexceptionreporterror"></a><a name="reporterror"></a>例外:報告錯誤

呼叫此成員函數向使用者報告訊息框中的錯誤文本。

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>參數

*nType*<br/>
指定消息框的樣式。 將[消息框樣式](styles-used-by-mfc.md#message-box-styles)的任意組合應用於該框。 如果不指定此參數,則預設值為MB_OK。

*nMessageID*<br/>
指定要顯示的消息的資源 ID(字串表條目),如果異常物件沒有錯誤消息。 如果為 0,則顯示"無錯誤消息可用"

### <a name="return-value"></a>傳回值

值`AfxMessageBox`;否則 0 如果沒有足夠的記憶體來顯示消息框。 有關可能的返回值,請參閱[AfxMessageBox。](cstring-formatting-and-message-box-display.md#afxmessagebox)

### <a name="example"></a>範例

下面是 使用的範`CException::ReportError`例 。 對於另一個示例,請參閱[CATCH](exception-processing.md#catch)的範例。

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
[如何操作:建立自己的自訂異常類](https://go.microsoft.com/fwlink/p/?linkid=128045)
