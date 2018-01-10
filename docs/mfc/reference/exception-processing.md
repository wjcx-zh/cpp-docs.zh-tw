---
title: "例外狀況處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.exceptions
dev_langs: C++
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
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: adad6183d15b378feb7ec96aedff6a0013a2dd24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exception-processing"></a>例外狀況處理
當程式執行時，可能會發生的異常狀況時，稱為 「 例外狀況 」 的錯誤數目。 這些可能包括用完記憶體、 資源配置錯誤，以及找不到檔案。  
  
 Microsoft Foundation 類別庫會使用模組化緊密之後 ANSI 標準委員會所提議的 c + + 例外狀況處理配置。 呼叫函式可能會遭遇異常性情況之前，必須是設定例外狀況處理常式。 如果函式發生異常狀況，就會擲回例外狀況，控制權會傳遞給例外狀況處理常式。  
  
 Microsoft Foundation 類別庫所包含的數個巨集將設定例外狀況處理常式。 必要時擲回特定例外狀況，並結束程式，幫助的其他全域函式的數字。 這些巨集和全域函式可分成下列類別：  
  
- 例外狀況巨集，組織您的例外狀況處理常式。  
  
- Exception-throwing 函式)，這會產生特定類型的例外狀況。  
  
- 終止函式，會導致程式終止。  
  
 如範例和詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="exception-macros"></a>例外狀況巨集  
  
|||  
|-|-|  
|[再試一次](#try)|將指定進行例外狀況處理程式碼區塊。|  
|[CATCH](#catch)|將攔截例外狀況，在上述案例中的程式碼區塊指定**再試一次**區塊。|  
|[CATCH_ALL](#catch_all)|指定一段程式碼來攔截所有例外狀況，從前述**再試一次**區塊。|  
|[AND_CATCH](#and_catch)|指定一段程式碼來攔截在上述案例中的其他例外狀況類型**再試一次**區塊。|  
|[AND_CATCH_ALL](#and_catch_all)|指定一段程式碼來攔截所有其他先前擲回的其他例外狀況類型**再試一次**區塊。|  
|[END_CATCH](#end_catch)|結束上次**攔截**或`AND_CATCH`程式碼區塊。|  
|[END_CATCH_ALL](#end_catch_all)|結束上次`CATCH_ALL`程式碼區塊。|  
|[擲回](#throw)|指定的例外狀況會擲回。|  
|[THROW_LAST](#throw_last)|目前處理的例外狀況至下一個外部的處理常式就會擲回。|  
  
### <a name="exception-throwing-functions"></a>擲回例外狀況的函式  
  
|||  
|-|-|  
|[AfxThrowArchiveException](#afxthrowarchiveexception)|封存例外狀況會擲回。|  
|[AfxThrowFileException](#afxthrowfileexception)|檔案例外狀況會擲回。|  
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|無效的引數例外狀況會擲回。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|擲回記憶體例外狀況。|  
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|不支援例外狀況會擲回。|  
|[AfxThrowResourceException](#afxthrowresourceexception)|Windows 找不到資源例外狀況會擲回。|  
|[AfxThrowUserException](#afxthrowuserexception)|擲回例外狀況，在使用者啟動程式動作。|  
  
 MFC 提供兩個擲回例外狀況的函式專為 OLE 例外狀況：  
  
### <a name="ole-exception-functions"></a>OLE 例外狀況的函式  
  
|||  
|-|-|  
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|擲回例外狀況的 OLE automation 函式內。|  
|[AfxThrowOleException](#afxthrowoleexception)|OLE 例外狀況會擲回。|  
  
 若要支援資料庫例外狀況，資料庫類別提供兩個例外狀況類別，`CDBException`和`CDaoException`，和全域函式，以支援例外狀況類型：  
  
### <a name="dao-exception-functions"></a>DAO 例外狀況的函式  
  
|||  
|-|-|  
|[AfxThrowDAOException](#afxthrowdaoexception)|擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)從自己的程式碼。|  
|[AfxThrowDBException](#afxthrowdbexception)|擲回[CDBException](../../mfc/reference/cdbexception-class.md)從自己的程式碼。|  
  
 MFC 提供下列的中止函式：  
  
### <a name="termination-functions"></a>終止函式  
  
|||  
|-|-|  
|[AfxAbort](#afxabort)|呼叫終止應用程式嚴重錯誤時，就會發生。|  
  
##  <a name="try"></a>再試一次  
 設定**再試一次**區塊。  
  
```   
TRY   
```  
  
### <a name="remarks"></a>備註  
 A**再試一次**區塊識別可能會擲回例外狀況的程式碼區塊。 在下列處理這些例外狀況**攔截**和`AND_CATCH`區塊。 允許遞迴： 例外狀況可能會傳遞至外部**再試一次**區塊中的，略過它們，或使用`THROW_LAST`巨集。 結束**再試一次**區塊`END_CATCH`或`END_CATCH_ALL`巨集。  
  
 如需詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>範例  
 請參閱範例的[攔截](#catch)。  

### <a name="requirements"></a>需求
標頭：afx.h

##  <a name="catch"></a>CATCH  
 定義會攔截擲回在上述的第一個例外狀況類型的程式碼區塊**再試一次**區塊。  
  
```   
CATCH(exception_class, exception_object_pointer_name)  
 
```  
  
### <a name="parameters"></a>參數  
 *exception_class*  
 指定要測試的例外狀況類型。 如需標準例外狀況類別的清單，請參閱類別[CException](../../mfc/reference/cexception-class.md)。  
  
 *exception_object_pointer_name*  
 指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取例外狀況物件內**攔截**區塊。 會為您宣告這個變數。  
  
### <a name="remarks"></a>備註  
 處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 `THROW_LAST` 巨集將處理移位到下個外部例外狀況框架。 結束**再試一次**區塊`END_CATCH`巨集。  
  
 如果*exception_class*是類別`CException`，則會攔截所有例外狀況類型。 您可以使用[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)成員函式來判斷哪一個特定的例外狀況。 若要攔截例外狀況的幾種更好的方法是使用循序`AND_CATCH`陳述式各有不同的例外狀況類型。  
  
 例外狀況物件指標的建立方式的巨集。 您不需要自行宣告。  
  
> [!NOTE]
>  **攔截**區塊會定義為 c + + 範圍括號括住分隔。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。 這也適用於*exception_object_pointer_name*。  
  
 如需有關例外狀況和**攔截**巨集，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]  
  
##  <a name="catch_all"></a>CATCH_ALL  
 定義會攔截所有前述擲回的例外狀況類型的程式碼區塊**再試一次**區塊。  
  
```   
CATCH_ALL(exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>參數  
 *exception_object_pointer_name*  
 指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `CATCH_ALL` 區塊中的例外狀況物件。 會為您宣告這個變數。  
  
### <a name="remarks"></a>備註  
 處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 `THROW_LAST` 巨集將處理移位到下個外部例外狀況框架。 如果您使用`CATCH_ALL`，結束**再試一次**區塊`END_CATCH_ALL`巨集。  
  
> [!NOTE]
>  `CATCH_ALL` 區塊會定義為以大括號分隔的 C ++ 範圍。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。  
  
 如需有關例外狀況的詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>範例  
 請參閱範例的[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  

##  <a name="and_catch"></a>AND_CATCH  
 定義一段程式碼來攔截中前面擲回其他例外狀況類型**再試一次**區塊。  
  
```   
AND_CATCH(exception_class, exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>參數  
 *exception_class*  
 指定要測試的例外狀況類型。 如需標準例外狀況類別的清單，請參閱類別[CException](../../mfc/reference/cexception-class.md)。  
  
 *exception_object_pointer_name*  
 將巨集所建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `AND_CATCH` 區塊中的例外狀況物件。 會為您宣告這個變數。  
  
### <a name="remarks"></a>備註  
 使用**攔截**巨集，以攔截一個例外狀況類型，則`AND_CATCH`巨集，以找出每個後續的型別。 結束**再試一次**區塊`END_CATCH`巨集。  
  
 處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫`THROW_LAST`巨集內`AND_CATCH`封鎖移位到下個外部例外狀況框架處理。 `AND_CATCH`先前的結束標記**攔截**或`AND_CATCH`區塊。  
  
> [!NOTE]
>  `AND_CATCH`區塊會定義為 c + + 範圍 （大括號括住分隔）。 如果您宣告這個範圍中的變數，請記得它們是只能在該範圍內存取。 這也適用於*exception_object_pointer_name*變數。  
  
### <a name="example"></a>範例  
 請參閱範例的[攔截](#catch)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
##  <a name="and_catch_all"></a>AND_CATCH_ALL  
 定義一段程式碼來攔截中前面擲回其他例外狀況類型**再試一次**區塊。  
  
```   
AND_CATCH_ALL(exception_object_pointer_name)  
```  
  
### <a name="parameters"></a>參數  
 *exception_object_pointer_name*  
 將巨集所建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `AND_CATCH_ALL` 區塊中的例外狀況物件。 會為您宣告這個變數。  
  
### <a name="remarks"></a>備註  
 使用**攔截**巨集，以攔截一個例外狀況類型，則`AND_CATCH_ALL`巨集，以攔截所有其他後續的類型。 如果您使用`AND_CATCH_ALL`，結束**再試一次**區塊`END_CATCH_ALL`巨集。  
  
 處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫`THROW_LAST`巨集內`AND_CATCH_ALL`封鎖移位到下個外部例外狀況框架處理。 `AND_CATCH_ALL`先前的結束標記**攔截**或`AND_CATCH_ALL`區塊。  
  
> [!NOTE]
>  `AND_CATCH_ALL`區塊會定義為 c + + 範圍 （大括號分隔）。 如果您宣告這個範圍中的變數，請記得它們是只能在該範圍內存取。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="end_catch"></a>END_CATCH  
 上一次結束標記**攔截**或`AND_CATCH`區塊。  
  
```   
END_CATCH  
```  
  
### <a name="remarks"></a>備註  
 如需有關`END_CATCH`巨集，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="end_catch_all"></a>END_CATCH_ALL  
 上一次結束標記`CATCH_ALL`或`AND_CATCH_ALL`區塊。  
  
```   
END_CATCH_ALL  
```  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="throw"></a>擲回 (MFC)  
 指定的例外狀況會擲回。  
  
```   
THROW(exception_object_pointer) 
```  
  
### <a name="parameters"></a>參數  
 *exception_object_pointer*  
 例外狀況物件指向衍生自`CException`。  
  
### <a name="remarks"></a>備註  
 **擲回**程式執行，將控制權傳遞至相關聯的插斷**攔截**封鎖程式中。 如果您未提供**攔截**封鎖，則控制權會傳遞給 Microsoft Foundation 類別庫模組，會列印錯誤訊息並結束。  
  
 如需詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="throw_last"></a>THROW_LAST  
 就會擲回例外狀況傳回至下一個外部**攔截**區塊。  
  
```   
THROW_LAST()   
```  
  
### <a name="remarks"></a>備註  
 這個巨集可讓您將在本機建立的例外狀況。 如果您嘗試將擲回只攔截到例外狀況，它通常會超出範圍，並刪除。 與`THROW_LAST`，例外狀況已正確地傳遞至下一個**攔截**處理常式。  
  
 如需詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>範例  
 請參閱範例的[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="afxthrowarchiveexception"></a>AfxThrowArchiveException  
 封存例外狀況會擲回。  
  
```   
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName); 
```  
  
### <a name="parameters"></a>參數  
 `cause`  
 指定一個整數，表示例外狀況的原因。 如需可能值的清單，請參閱[CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。  
  
 `lpszArchiveName`  
 包含名稱的字串會指向`CArchive`造成例外狀況 （如果有的話） 的物件。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="afxthrowfileexception"></a>AfxThrowFileException  
 檔案例外狀況會擲回。  
  
```   
void AfxThrowFileException(
    int cause,  
    LONG lOsError = -1,  
    LPCTSTR lpszFileName = NULL); 
```  
  
### <a name="parameters"></a>參數  
 `cause`  
 指定一個整數，表示例外狀況的原因。 如需可能值的清單，請參閱[CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。  
  
 `lOsError`  
 包含作業系統錯誤號碼 （如果有的話），說明例外狀況的原因。 請參閱您作業系統的手冊錯誤碼的清單。  
  
 `lpszFileName`  
 指向字串，包含造成此例外狀況 （如果有的話） 的檔案名稱。  
  
### <a name="remarks"></a>備註  
 您有責任判斷基礎的作業系統錯誤碼的原因。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  

## <a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgException
無效的引數例外狀況會擲回。  
   
### <a name="syntax"></a>語法    
```
void AfxThrowInvalidArgException( );  
```  
   
### <a name="remarks"></a>備註  
 無效的引數使用時，會呼叫此函數。  
   
### <a name="requirements"></a>需求  
 **標頭：** afx.h  
   
### <a name="see-also"></a>請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [CInvalidArgException 類別](cinvalidargexception-class.md)   
 [擲回](#throw)
  
  
##  <a name="afxthrowmemoryexception"></a>AfxThrowMemoryException  
 擲回記憶體例外狀況。  
  
```   
void AfxThrowMemoryException(); 
```  
  
### <a name="remarks"></a>備註  
 如果呼叫此函式呼叫基礎的系統記憶體配置器 (例如`malloc`和[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) Windows 函式) 失敗。 您不需要呼叫它的**新**因為**新**將會擲回記憶體例外狀況自動如果記憶體配置失敗。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException  
 擲回的例外狀況，不支援的功能要求的結果。  
  
```  
void AfxThrowNotSupportedException(); 
```  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="afxthrowresourceexception"></a>AfxThrowResourceException  
 擲回資源例外狀況。  
  
```   
void  AfxThrowResourceException(); 
```  
  
### <a name="remarks"></a>備註  
 無法載入 Windows 資源時，通常會呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="afxthrowuserexception"></a>AfxThrowUserException  
 擲回例外狀況以停止使用者作業。  
  
```   
void AfxThrowUserException(); 
```  
  
### <a name="remarks"></a>備註  
 此函式通常會呼叫之後立即`AfxMessageBox`向使用者回報了錯誤。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
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
 `wCode`  
 應用程式特定的錯誤碼。  
  
 `lpszDescription`  
 錯誤的詳細描述。  
  
 `nDescriptionID`  
 詳細錯誤描述的資源 ID。  
  
 `nHelpID`  
 您的應用程式說明 (.HLP) 檔的說明內容。  
  
### <a name="remarks"></a>備註  
 提供給此函式的資訊可以透過驅動應用程式 (Microsoft Visual Basic 或其他 OLE Automation 用戶端應用程式) 來加以顯示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="afxthrowoleexception"></a>AfxThrowOleException  
 建立類型的物件`COleException`並擲回例外狀況。  
  
``` 
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr); 
```  
  
### <a name="parameters"></a>參數  
 `sc`  
 OLE 狀態碼指出例外狀況的原因。  
  
 `hr`  
 控制代碼，以指出例外狀況原因的結果碼。  
  
### <a name="remarks"></a>備註  
 接受的版本`HRESULT`為引數會將該結果程式碼轉換成對應`SCODE`。 如需有關`HRESULT`和`SCODE`，請參閱[結構 COM 錯誤碼的](http://msdn.microsoft.com/library/windows/desktop/ms690088)Windows SDK 中。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="afxthrowdaoexception"></a>AfxThrowDaoException  
 呼叫此函式，可擲回例外狀況型別的[CDaoException](../../mfc/reference/cdaoexception-class.md)從自己的程式碼。  
  
```   
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,  
    SCODE scode = S_OK); 
```  
  
### <a name="parameters"></a>參數  
 `nAfxDaoError`  
 整數值，表示擴充錯誤碼 DAO，這可以其中一個值列在[CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)。  
  
 *scode*  
 DAO，類型的 OLE 錯誤碼`SCODE`。 如需資訊，請參閱[CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。  
  
### <a name="remarks"></a>備註  
 架構也會呼叫`AfxThrowDaoException`。 在呼叫中，您可以傳遞其中一個參數或兩者。 例如，如果您想要引發的其中一個錯誤中定義**CDaoException::nAfxDaoError**但您不在意*scode*參數，傳遞有效的程式碼中`nAfxDaoError`參數並接受預設值*scode*。  
  
 如需 MFC DAO 類別相關的例外狀況資訊，請參閱類別`CDaoException`本書和發行項中[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdb.h  
  
##  <a name="afxthrowdbexception"></a>AfxThrowDBException  
 呼叫此函式，可擲回例外狀況型別的`CDBException`從自己的程式碼。  
  
```  
void AfxThrowDBException(
    RETCODE nRetCode,  
    CDatabase* pdb,  
    HSTMT hstmt);  
```  
  
### <a name="parameters"></a>參數  
 `nRetCode`  
 型別的值**RETCODE**，定義的錯誤，導致系統擲回的例外狀況類型。  
  
 `pdb`  
 指標`CDatabase`物件，表示與例外狀況相關聯的資料來源連接。  
  
 `hstmt`  
 ODBC **HSTMT**指定與例外狀況相關聯的陳述式控制代碼的控制代碼。  
  
### <a name="remarks"></a>備註  
 這個架構會呼叫`AfxThrowDBException`當它收到 ODBC **RETCODE**呼叫 ODBC API 函式，並解譯**RETCODE**為例外狀況，而不是 expectable 錯誤。 例如，資料存取作業可能會失敗，因為磁碟讀取錯誤。  
  
 如需有關資訊**RETCODE** ODBC 所定義的值請參閱 Windows SDK 中的第 8 章 「 擷取狀態和錯誤資訊 」。 這些代碼的 MFC 擴充功能的相關資訊，請參閱類別[CDBException](../../mfc/reference/cdbexception-class.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="afxabort"></a>AfxAbort  
 由 MFC 提供預設的中止函式。  
  
```   
void  AfxAbort(); 
```  
  
### <a name="remarks"></a>備註  
 `AfxAbort`會由內部呼叫 MFC 的成員函式發生嚴重錯誤，例如無法處理的遺漏例外狀況時。 您可以呼叫`AfxAbort`在極少數的情況下，如果遇到重大錯誤，因此您無法復原的。  
  
### <a name="example"></a>範例  
 請參閱範例的[攔截](#catch)。  

### <a name="requirements"></a>需求  
  **標頭**afx.h   
  
## <a name="see-also"></a>請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)   
 [CException 類別](../../mfc/reference/cexception-class.md)
