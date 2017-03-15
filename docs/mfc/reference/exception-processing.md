---
title: "例外狀況的處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.exceptions
dev_langs:
- C++
helpviewer_keywords:
- macros, exception handling
- DAO (Data Access Objects), exceptions
- OLE exceptions, MFC functions
- exceptions, processing
- exception macros
- termination functions, MFC
- MFC, exceptions
- exceptions, MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
caps.latest.revision: 16
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a2ded9c49a9f6935a5b268ccbefc4678af184029
ms.lasthandoff: 02/24/2017

---
# <a name="exception-processing"></a>例外狀況處理
當程式執行時，可能會發生異常狀況時，稱為 「 例外狀況 」 的錯誤數目。 這些可能包括用完記憶體、 資源配置錯誤，以及找不到檔案。  
  
 Mfc 程式庫會使用藍本之後 ANSI 標準委員會所提議的 c + + 例外狀況處理配置。 例外狀況處理常式必須設定之前呼叫函式可能會發生異常狀況。 如果函式發生異常狀況，則會擲回例外狀況，控制權會傳遞至例外狀況處理常式。  
  
 Mfc 程式庫所包含的數個巨集將例外狀況處理常式設定。 必要時擲回特定例外狀況並結束程式，幫助其他全域函式的數目。 這些巨集和全域函式可分成下列類別︰  
  
- 例外狀況巨集︰ 結構化例外處理常式。  
  
- Exception-throwing 函式)，這會產生的特定類型的例外狀況。  
  
- 終止函式，會導致程式終止。  
  
 如需範例和詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="exception-macros"></a>例外狀況巨集  
  
|||  
|-|-|  
|[請嘗試](#try)|將指定的例外狀況處理程式碼區塊。|  
|[CATCH](#catch)|指定一段程式碼來攔截例外狀況在上述案例中的**嘗試**區塊。|  
|[CATCH_ALL](#catch_all)|指定一段程式碼來攔截所有例外狀況，在上述案例中的**嘗試**區塊。|  
|[AND_CATCH](#and_catch)|指定一段程式碼來攔截在上述案例中的其他例外狀況型別**嘗試**區塊。|  
|[AND_CATCH_ALL](#and_catch_all)|指定一段程式碼來攔截所有其他先前擲回的其他例外狀況類型**嘗試**區塊。|  
|[END_CATCH](#end_catch)|結束上次**攔截**或`AND_CATCH`程式碼區塊。|  
|[END_CATCH_ALL](#end_catch_all)|結束上次`CATCH_ALL`程式碼區塊。|  
|[擲回](#throw)|指定的例外狀況會擲回。|  
|[THROW_LAST](#throw_last)|目前處理的例外狀況至下一個外部的處理常式就會擲回。|  
  
### <a name="exception-throwing-functions"></a>擲回例外狀況的函式  
  
|||  
|-|-|  
|[AfxThrowArchiveException](#afxthrowarchiveexception)|封存例外狀況會擲回。|  
|[AfxThrowFileException](#afxthrowfileexception)|檔案例外狀況會擲回。|  
|[AfxThrowMemoryException](#afxthrowmemoryexception)|會擲回記憶體例外狀況。|  
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|不支援例外狀況會擲回。|  
|[AfxThrowResourceException](#afxthrowresourceexception)|Windows 找不到資源例外狀況會擲回。|  
|[AfxThrowUserException](#afxthrowuserexception)|使用者啟動程式動作會擲回例外狀況。|  
  
 MFC 提供兩個擲回例外狀況的函式專為 OLE 例外狀況︰  
  
### <a name="ole-exception-functions"></a>OLE 例外狀況的函式  
  
|||  
|-|-|  
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|擲回例外狀況的 OLE automation 函式內。|  
|[AfxThrowOleException](#afxthrowoleexception)|OLE 例外狀況會擲回。|  
  
 若要支援資料庫例外狀況，資料庫類別提供兩個例外狀況類別，`CDBException`和`CDaoException`，和全域函式，以支援例外狀況類型︰  
  
### <a name="dao-exception-functions"></a>DAO 例外狀況的函式  
  
|||  
|-|-|  
|[AfxThrowDAOException](#afxthrowdaoexception)|擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)從自己的程式碼。|  
|[AfxThrowDBException](#afxthrowdbexception)|擲回[CDBException](../../mfc/reference/cdbexception-class.md)從自己的程式碼。|  
  
 MFC 提供下列的中止函式︰  
  
### <a name="termination-functions"></a>終止函式  
  
|||  
|-|-|  
|[AfxAbort](#afxabort)|呼叫終止應用程式嚴重錯誤時就會發生。|  
  
##  <a name="a-nametrya--try"></a><a name="try"></a>請嘗試  
 設定**嘗試**區塊。  
  
```   
TRY   
```  
  
### <a name="remarks"></a>備註  
 A**嘗試**區塊識別可能會擲回例外狀況的程式碼區塊。 在下列處理這些例外狀況**攔截**和`AND_CATCH`區塊。 允許遞迴︰ 例外狀況可能會傳遞至外部**嘗試**區塊時，略過它們，或使用`THROW_LAST`巨集。 結束**嘗試**區塊`END_CATCH`或`END_CATCH_ALL`巨集。  
  
 如需詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>範例  
 請參閱範例[攔截](#catch)。  

### <a name="requirements"></a>需求
標頭：afx.h

##  <a name="a-namecatcha--catch"></a><a name="catch"></a>CATCH  
 定義會攔截擲回在上述的第一個例外狀況類型的程式碼區塊**嘗試**區塊。  
  
```   
CATCH(exception_class, exception_object_pointer_name)  
 
```  
  
### <a name="parameters"></a>參數  
 *exception_class*  
 指定要測試的例外狀況類型。 如需標準例外狀況類別的清單，請參閱類別[CException](../../mfc/reference/cexception-class.md)。  
  
 *exception_object_pointer_name*  
 指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取的例外狀況物件**攔截**區塊。 會為您宣告這個變數。  
  
### <a name="remarks"></a>備註  
 處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 `THROW_LAST` 巨集將處理移位到下個外部例外狀況框架。 結束**嘗試**區塊`END_CATCH`巨集。  
  
 如果*exception_class*類別`CException`，則會攔截所有例外狀況類型。 您可以使用[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)成員函式來判斷哪一個特定的例外狀況。 攔截例外狀況的幾種更好的辦法是使用循序`AND_CATCH`陳述式各有不同的例外狀況類型。  
  
 巨集來建立例外狀況物件指標。 您不需要宣告它。  
  
> [!NOTE]
>  **攔截**區塊會定義為以大括號分隔的 c + + 範圍。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。 這也適用於*exception_object_pointer_name*。  
  
 如需有關例外狀況和**攔截**巨集，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCExceptions #&26;](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]  
  
##  <a name="a-namecatchalla--catchall"></a><a name="catch_all"></a>CATCH_ALL  
 定義會攔截所有前述擲回的例外狀況類型的程式碼區塊**嘗試**區塊。  
  
```   
CATCH_ALL(exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>參數  
 *exception_object_pointer_name*  
 指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `CATCH_ALL` 區塊中的例外狀況物件。 會為您宣告這個變數。  
  
### <a name="remarks"></a>備註  
 處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 `THROW_LAST` 巨集將處理移位到下個外部例外狀況框架。 如果您使用`CATCH_ALL`，結束**嘗試**區塊`END_CATCH_ALL`巨集。  
  
> [!NOTE]
>  `CATCH_ALL` 區塊會定義為以大括號分隔的 C ++ 範圍。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。  
  
 如需有關例外狀況的詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>範例  
 請參閱範例[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  

##  <a name="a-nameandcatcha--andcatch"></a><a name="and_catch"></a>AND_CATCH  
 定義一段程式碼來攔截中前面擲回其他例外狀況類型**嘗試**區塊。  
  
```   
AND_CATCH(exception_class, exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>參數  
 *exception_class*  
 指定要測試的例外狀況類型。 如需標準例外狀況類別的清單，請參閱類別[CException](../../mfc/reference/cexception-class.md)。  
  
 *exception_object_pointer_name*  
 將巨集所建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `AND_CATCH` 區塊中的例外狀況物件。 會為您宣告這個變數。  
  
### <a name="remarks"></a>備註  
 使用**攔截**巨集，以找出一個例外狀況類型，然後在`AND_CATCH`巨集，以攔截每個後續的型別。 結束**嘗試**區塊`END_CATCH`巨集。  
  
 處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫`THROW_LAST`巨集內`AND_CATCH`封鎖移位到下個外部例外狀況框架處理。 `AND_CATCH`先前的結束標記**攔截**或`AND_CATCH`區塊。  
  
> [!NOTE]
>  `AND_CATCH`區塊會定義為 c + + 範圍 （以大括號分隔）。 如果您宣告變數，在此範圍內，請記得它們是只能在該範圍內存取。 這也適用於*exception_object_pointer_name*變數。  
  
### <a name="example"></a>範例  
 請參閱範例[攔截](#catch)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
##  <a name="a-nameandcatchalla--andcatchall"></a><a name="and_catch_all"></a>AND_CATCH_ALL  
 定義一段程式碼來攔截中前面擲回其他例外狀況類型**嘗試**區塊。  
  
```   
AND_CATCH_ALL(exception_object_pointer_name)  
```  
  
### <a name="parameters"></a>參數  
 *exception_object_pointer_name*  
 將巨集所建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `AND_CATCH_ALL` 區塊中的例外狀況物件。 會為您宣告這個變數。  
  
### <a name="remarks"></a>備註  
 使用**攔截**巨集，以找出一個例外狀況類型，然後在`AND_CATCH_ALL`巨集，以找出其他所有後續的類型。 如果您使用`AND_CATCH_ALL`，結束**嘗試**區塊`END_CATCH_ALL`巨集。  
  
 處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫`THROW_LAST`巨集內`AND_CATCH_ALL`封鎖移位到下個外部例外狀況框架處理。 `AND_CATCH_ALL`先前的結束標記**攔截**或`AND_CATCH_ALL`區塊。  
  
> [!NOTE]
>  `AND_CATCH_ALL`區塊會定義為 c + + 範圍 （以大括號分隔）。 如果您宣告變數，在此範圍內，請記得它們是只能在該範圍內存取。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameendcatcha--endcatch"></a><a name="end_catch"></a>END_CATCH  
 最後一個結束標記**攔截**或`AND_CATCH`區塊。  
  
```   
END_CATCH  
```  
  
### <a name="remarks"></a>備註  
 如需有關`END_CATCH`巨集，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameendcatchalla--endcatchall"></a><a name="end_catch_all"></a>END_CATCH_ALL  
 最後一個結束標記`CATCH_ALL`或`AND_CATCH_ALL`區塊。  
  
```   
END_CATCH_ALL  
```  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-namethrowa--throw-mfc"></a><a name="throw"></a>擲回 (MFC)  
 指定的例外狀況會擲回。  
  
```   
THROW(exception_object_pointer) 
```  
  
### <a name="parameters"></a>參數  
 *exception_object_pointer*  
 例外狀況物件指向衍生自`CException`。  
  
### <a name="remarks"></a>備註  
 **擲回**中斷程式執行，將控制項傳遞至相關聯**攔截**區塊放在您的程式。 如果您沒有提供**攔截**區塊，然後將控制項傳遞至 Mfc 程式庫模組會列印錯誤訊息並結束。  
  
 如需詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-namethrowlasta--throwlast"></a><a name="throw_last"></a>THROW_LAST  
 重新擲回例外狀況，到下一個外部**攔截**區塊。  
  
```   
THROW_LAST()   
```  
  
### <a name="remarks"></a>備註  
 這個巨集可讓您將在本機建立的例外狀況。 如果您嘗試將擲回例外狀況只攔截到的它通常會超出範圍，並刪除。 使用`THROW_LAST`，例外狀況會正確地傳遞至下一個**攔截**處理常式。  
  
 如需詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>範例  
 請參閱範例[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameafxthrowarchiveexceptiona--afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a>AfxThrowArchiveException  
 封存例外狀況會擲回。  
  
```   
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName); 
```  
  
### <a name="parameters"></a>參數  
 `cause`  
 指定一個整數，表示例外狀況的原因。 如需可能的值，請參閱[CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。  
  
 `lpszArchiveName`  
 包含名稱的字串會指向`CArchive`造成例外狀況 （如果有的話） 的物件。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameafxthrowfileexceptiona--afxthrowfileexception"></a><a name="afxthrowfileexception"></a>AfxThrowFileException  
 檔案例外狀況會擲回。  
  
```   
void AfxThrowFileException(
    int cause,  
    LONG lOsError = -1,  
    LPCTSTR lpszFileName = NULL); 
```  
  
### <a name="parameters"></a>參數  
 `cause`  
 指定一個整數，表示例外狀況的原因。 如需可能的值，請參閱[CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。  
  
 `lOsError`  
 包含作業系統的錯誤號碼 （如果有的話），說明例外狀況的原因。 請參閱您作業系統的手冊錯誤碼的清單。  
  
 `lpszFileName`  
 指向包含造成此例外狀況 （如果有的話） 的檔案名稱的字串。  
  
### <a name="remarks"></a>備註  
 您必須負責決定根據作業系統錯誤碼的原因。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameafxthrowmemoryexceptiona--afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a>AfxThrowMemoryException  
 會擲回記憶體例外狀況。  
  
```   
void AfxThrowMemoryException(); 
```  
  
### <a name="remarks"></a>備註  
 如果呼叫此函式呼叫基礎的系統記憶體配置器 (例如`malloc`和[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) Windows 函式) 失敗。 您不需要呼叫它的**新**因為**新**時擲回記憶體例外狀況會自動在記憶體配置失敗。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameafxthrownotsupportedexceptiona--afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException  
 會擲回的例外狀況，因為不支援的功能要求。  
  
```  
void AfxThrowNotSupportedException(); 
```  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameafxthrowresourceexceptiona--afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a>AfxThrowResourceException  
 資源例外狀況會擲回。  
  
```   
void  AfxThrowResourceException(); 
```  
  
### <a name="remarks"></a>備註  
 無法載入 Windows 資源時，通常會呼叫此函式。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameafxthrowuserexceptiona--afxthrowuserexception"></a><a name="afxthrowuserexception"></a>AfxThrowUserException  
 會擲回的例外狀況，以停止使用者作業。  
  
```   
void AfxThrowUserException(); 
```  
  
### <a name="remarks"></a>備註  
 此函式通常會呼叫之後立即`AfxMessageBox`向使用者回報了錯誤。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameafxthrowoledispatchexceptiona--afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException  
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
 [!code-cpp[NVC_MFCExceptions #&25;](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameafxthrowoleexceptiona--afxthrowoleexception"></a><a name="afxthrowoleexception"></a>AfxThrowOleException  
 建立型別的物件`COleException`並擲回例外狀況。  
  
``` 
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr); 
```  
  
### <a name="parameters"></a>參數  
 `sc`  
 OLE 狀態碼表示例外狀況的原因。  
  
 `hr`  
 表示例外狀況原因的結果碼的控制代碼。  
  
### <a name="remarks"></a>備註  
 接受的版本`HRESULT`為引數會將該結果程式碼轉換成對應`SCODE`。 如需有關`HRESULT`和`SCODE`，請參閱[COM 錯誤代碼結構](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdao.h  
  
##  <a name="a-nameafxthrowdaoexceptiona--afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a>AfxThrowDaoException  
 呼叫此函式擲回例外狀況型別[CDaoException](../../mfc/reference/cdaoexception-class.md)從自己的程式碼。  
  
```   
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,  
    SCODE scode = S_OK); 
```  
  
### <a name="parameters"></a>參數  
 `nAfxDaoError`  
 整數值，表示擴充錯誤碼 DAO，可以其中一個值列出這些下[CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)。  
  
 *scode*  
 從 DAO，類型的 OLE 錯誤碼`SCODE`。 如需資訊，請參閱[CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。  
  
### <a name="remarks"></a>備註  
 架構也會呼叫`AfxThrowDaoException`。 在呼叫中，您可以傳遞的參數之一或兩者。 例如，如果您想要引發的其中一個錯誤中定義**CDaoException::nAfxDaoError** ，但您不在意*scode*參數，傳遞有效的程式碼中`nAfxDaoError`參數並接受預設值為*scode*。  
  
 如需 MFC DAO 類別相關的例外狀況資訊，請參閱類別`CDaoException`這本書和發行項中[例外狀況︰ 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdb.h  
  
##  <a name="a-nameafxthrowdbexceptiona--afxthrowdbexception"></a><a name="afxthrowdbexception"></a>AfxThrowDBException  
 呼叫此函式擲回例外狀況型別`CDBException`從自己的程式碼。  
  
```  
void AfxThrowDBException(
    RETCODE nRetCode,  
    CDatabase* pdb,  
    HSTMT hstmt);  
```  
  
### <a name="parameters"></a>參數  
 `nRetCode`  
 型別的值**RETCODE**，造成擲回例外狀況之錯誤的型別定義。  
  
 `pdb`  
 指標`CDatabase`物件，代表與例外狀況是相關聯的資料來源連接。  
  
 `hstmt`  
 ODBC **HSTMT**指定陳述式控制代碼與例外狀況是相關聯的控制代碼。  
  
### <a name="remarks"></a>備註  
 這個架構會呼叫`AfxThrowDBException`當它收到 ODBC **RETCODE**呼叫 ODBC API 函式，並會解譯**RETCODE**為例外狀況，而不是 expectable 的錯誤。 比方說，資料存取作業可能會失敗，因為磁碟的讀取錯誤。  
  
 如需有關資訊**RETCODE** ODBC 所定義的值請參閱第 8 章 「 擷取狀態和錯誤資訊 」 中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需 MFC 擴充功能，這些代碼，請參閱類別[CDBException](../../mfc/reference/cdbexception-class.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afx.h  
  
##  <a name="a-nameafxaborta--afxabort"></a><a name="afxabort"></a>AfxAbort  
 由 MFC 提供預設的中止函式。  
  
```   
void  AfxAbort(); 
```  
  
### <a name="remarks"></a>備註  
 `AfxAbort`會在內部呼叫 MFC 成員函式有嚴重的錯誤，例如無法處理無法攔截例外狀況時。 您可以呼叫`AfxAbort`在少數情況下，當您遇到無法復原的嚴重錯誤。  
  
### <a name="example"></a>範例  
 請參閱範例[攔截](#catch)。  

### <a name="requirements"></a>需求  
  **標頭**afx.h   
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)   
 [CException 類別](../../mfc/reference/cexception-class.md)

