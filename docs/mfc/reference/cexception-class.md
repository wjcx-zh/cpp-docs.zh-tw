---
title: "CException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CException
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchException class, base class
- CException class
- exceptions, classes for
- CInternetException class, base class
- macros, exception handling
- CNotSupportedException class, base class
- CFileException class, base class
- CDBException class, base class
- CArchiveException class, base class
- CUserException class
- CDaoException class, base class
- CMemoryException class, base class
- COleException class, base class
- CResourceException class, base class
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
caps.latest.revision: 22
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 4cbb69ff79a1b201260d83b1bd568b63519a33b5
ms.lasthandoff: 02/24/2017

---
# <a name="cexception-class"></a>CException 類別
MFC 程式庫中所有例外狀況的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE CException : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CException::CException](#cexception)|建構 `CException` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CException::Delete](#delete)|刪除`CException`物件。|  
|[CException::ReportError](#reporterror)|向使用者回報在訊息方塊中的錯誤訊息。|  
  
## <a name="remarks"></a>備註  
 因為`CException`是抽象的基底類別，您無法建立`CException`物件直接; 您必須建立衍生類別的物件。 如果您要建立您自己`CException`-樣式類別，使用衍生的類別做為模型上面所列的其中一個。 請確定您的衍生的類別，也會使用`IMPLEMENT_DYNAMIC`。  
  
 衍生的類別和其描述如下︰  
  
|||  
|-|-|  
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|資源關鍵 MFC 例外狀況的基底類別|  
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|無效的引數例外狀況|  
|[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)|記憶體不足例外狀況|  
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|不支援的作業要求|  
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|封存特有的例外狀況|  
|[CFileException](../../mfc/reference/cfileexception-class.md)|檔案特定例外狀況|  
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|找不到或無法建立 Windows 資源|  
|[COleException](../../mfc/reference/coleexception-class.md)|OLE 例外狀況|  
|[CDBException](../../mfc/reference/cdbexception-class.md)|資料庫例外狀況 （也就是例外狀況所引發的開放式資料庫連接為基礎之 MFC 資料庫類別）|  
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|OLE 分派 （自動） 例外狀況|  
|[CUserException](../../mfc/reference/cuserexception-class.md)|例外狀況，表示找不到資源|  
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|資料存取物件的例外狀況 （也就是例外狀況所引發的 DAO 類別）|  
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|網際網路例外狀況 （也就是例外狀況所引發的網際網路類別）。|  
  
 這些例外狀況用來搭配[擲回](exception-processing.md#throw)， [THROW_LAST](exception-processing.md#throw_last)，[嘗試](exception-processing.md#try)，[攔截](exception-processing.md#catch)， [and_catch](exception-processing.md#and_catch)，和[end_catch](exception-processing.md#end_catch)巨集。 如需有關例外狀況的詳細資訊，請參閱[例外狀況處理](exception-processing.md)，或請參閱文章[例外狀況處理 (MFC)](../exception-handling-in-mfc.md)。  
  
 若要攔截特定例外狀況，使用適當的衍生的類別。 若要攔截所有例外狀況類型，使用`CException`，然後使用[cobject:: Iskindof](cobject-class.md#iskindof)區別`CException`-衍生的類別。 請注意，`CObject::IsKindOf`只適用於類別宣告為具有[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)巨集，以利用動態型別檢查。 任何`CException`-您建立的衍生的類別應該使用`IMPLEMENT_DYNAMIC`巨集，太。  
  
 您可以對使用者的例外狀況的相關報告詳細資料，藉由呼叫[GetErrorMessage](cfileexception-class.md#geterrormessage)或[ReportError](#reporterror)、 兩個成員函式，可使用任何`CException`的衍生類別。  
  
 如果其中一個巨集，會攔截例外狀況`CException`物件會自動刪除，請勿刪除它自己。 如果使用攔截到例外狀況**攔截**關鍵字，不會自動刪除。 請參閱文章[例外狀況處理 (MFC)](../exception-handling-in-mfc.md)如需有關何時要刪除的例外狀況物件。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](cobject-class.md)  
  
 `CException`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="a-namecexceptiona--cexceptioncexception"></a><a name="cexception"></a>CException::CException  
 此成員函式建構`CException`物件。  
  
```  
explicit CException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>參數  
 *b_AutoDelete*  
 指定**TRUE**如果的記憶體`CException`已在堆積上配置物件。 這將導致`CException`時刪除物件**刪除**呼叫成員函式會刪除例外狀況。 指定**FALSE**如果`CException`物件在堆疊上，或全域物件。 在此情況下，`CException`物件不會刪除**刪除**成員函式呼叫。  
  
### <a name="remarks"></a>備註  
 您通常不需要直接呼叫這個建構函式。 擲回例外狀況的函式應該建立的執行個體`CException`-衍生類別，並呼叫其建構函式，或它應該 MFC 使用其中一個擲回函式，例如[AfxThrowFileException](exception-processing.md#afxthrowfileexception)、 預先定義的型別會擲回。 本文件僅供完整性。  
  
##  <a name="a-namedeletea--cexceptiondelete"></a><a name="delete"></a>CException::Delete  
 此函式會檢查是否要**CException**堆積上建立物件，如果是的話，它會呼叫**刪除**物件上的運算子。  
  
```  
void Delete();
```  
  
### <a name="remarks"></a>備註  
 刪除時**CException**物件，請使用**刪除**成員函式來刪除例外狀況。 請勿使用**刪除**運算子直接，因為`CException`物件可能全域物件，或已建立在堆疊上。  
  
 您可以指定要建構的物件時，是否應刪除物件。 如需詳細資訊，請參閱[CException::CException](#cexception)。  
  
 您只需要呼叫**刪除**如果您使用 c + +**嘗試**- **攔截**機制。 如果您使用 MFC 巨集**嘗試**和**攔截**，則這些巨集將會自動呼叫此函式。  
  
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
  
##  <a name="a-namereporterrora--cexceptionreporterror"></a><a name="reporterror"></a>CException::ReportError  
 在訊息方塊中，使用者呼叫此成員函式，來報告錯誤文字。  
  
```  
virtual int ReportError(
    UINT nType = MB_OK,  
    UINT nMessageID = 0);
```  
  
### <a name="parameters"></a>參數  
 `nType`  
 指定訊息方塊樣式。 套用的任何結合[訊息方塊樣式](message-box-styles.md)至方塊。 如果您未指定此參數，預設值是**MB_OK**。  
  
 *nMessageID*  
 指定的資源識別碼 （字串資料表項目） 的例外狀況物件不具有錯誤訊息時所顯示的訊息。 如果為 0，訊息 「 沒有錯誤訊息已使用 「 隨即出現。  
  
### <a name="return-value"></a>傳回值  
 `AfxMessageBox`值; 否則為 0，表示記憶體不足，無法顯示訊息方塊。 請參閱[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)提供可能的傳回值。  
  
### <a name="example"></a>範例  
 以下是使用的範例`CException::ReportError`。 如需其他範例，請參閱範例[攔截](exception-processing.md#catch)。  
  
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
 [CObject 類別](cobject-class.md)   
 [階層架構圖表](../hierarchy-chart.md)   
 [例外狀況處理](exception-processing.md)   
 [如何︰ 建立我自己的自訂例外狀況類別](http://go.microsoft.com/fwlink/linkid=128045)



