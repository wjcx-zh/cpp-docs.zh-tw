---
title: "CFileException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CFile class, exceptions of
- exceptions, file type
- CFileException class
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
caps.latest.revision: 20
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
ms.openlocfilehash: d9064ae66f0dcd0e9f0dce0eedd8e38353f9da06
ms.lasthandoff: 02/24/2017

---
# <a name="cfileexception-class"></a>CFileException 類別
表示檔案相關的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class CFileException : public CException  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFileException::CFileException](#cfileexception)|建構 `CFileException` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFileException::ErrnoToException](#errnotoexception)|傳回造成執行階段錯誤數的程式碼。|  
|[CFileException::GetErrorMessage](#geterrormessage)|取得描述例外狀況訊息。|  
|[CFileException::OsErrorToException](#oserrortoexception)|傳回對應至作業系統錯誤碼的原因碼。|  
|[CFileException::ThrowErrno](#throwerrno)|會根據執行階段錯誤號碼的檔案例外狀況。|  
|[CFileException::ThrowOsError](#throwoserror)|會根據作業系統錯誤數值檔案例外狀況。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CFileException::m_cause](#m_cause)|包含對應的例外狀況原因的可攜式程式碼。|  
|[CFileException::m_lOsError](#m_loserror)|包含相關的作業系統錯誤號碼。|  
|[CFileException::m_strFileName](#m_strfilename)|包含這個例外狀況的檔案名稱。|  
  
## <a name="remarks"></a>備註  
 `CFileException`類別包含保存原因可攜式程式碼和操作系統特定錯誤號碼的公用資料成員。 此類別也會提供靜態成員函式擲回的例外狀況的檔案，並傳回作業系統錯誤和 C 執行階段錯誤的原因代碼。  
  
 `CFileException`物件的建構與中擲回`CFile`成員函式在衍生類別的成員函式。 您可以存取這些物件的範圍內**攔截**運算式。 可攜性，請使用造成程式碼，取得例外狀況的原因。 如需例外狀況的詳細資訊，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CFileException`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="cfileexception"></a>CFileException::CFileException  
 建構`CFileException`將原因代碼和作業系統程式碼儲存在物件的物件。  
  
```  
CFileException(
    int cause = CFileException::none,  
    LONG lOsError = -1,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cause`  
 列舉型別變數，指出例外狀況的原因。 請參閱[CFileException::m_cause](#m_cause)的可能值清單。  
  
 `lOsError`  
 例外狀況，如果有的話，操作系統特定原因。 `lOsError`參數提供詳細的資訊比`cause`沒有。  
  
 `lpszArchiveName`  
 包含名稱的字串會指向`CFile`造成例外狀況物件。  
  
### <a name="remarks"></a>備註  
 請勿直接使用這個建構函式，但呼叫全域函式，而是[AfxThrowFileException](exception-processing.md#afxthrowfileexception)。  
  
> [!NOTE]
>  變數`lOsError`僅適用於`CFile`和`CStdioFile`物件。 `CMemFile`類別不會處理此錯誤的程式碼。  
  
##  <a name="errnotoexception"></a>CFileException::ErrnoToException  
 指定的執行階段程式庫錯誤將值轉換成`CFileException`列舉值時發生錯誤。  
  
```  
static int PASCAL ErrnoToException(int nErrno);
```  
  
### <a name="parameters"></a>參數  
 `nErrno`  
 整數錯誤碼 ERRNO 執行時期 include 檔中所定義。H.  
  
### <a name="return-value"></a>傳回值  
 對應至指定的執行階段程式庫錯誤值的列舉的值。  
  
### <a name="remarks"></a>備註  
 請參閱[CFileException::m_cause](#m_cause)可能的清單的列舉值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&26;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]  
  
##  <a name="geterrormessage"></a>CFileException::GetErrorMessage  
 擷取描述例外狀況的文字。  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,  
    UINT nMaxError,  
    PUINT pnHelpContext = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 [in、out] `lpszError`  
 收到的錯誤訊息的緩衝區指標。  
  
 [in] `nMaxError`  
 指定的緩衝區可以保留的字元數目上限。 這包括結束的 null 字元。  
  
 [in、out] `pnHelpContext`  
 指標不帶正負號整數，會收到說明內容識別碼。 如果`NULL`，會傳回任何識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果指定的緩衝區太小，則會截斷錯誤訊息。  
  
### <a name="example"></a>範例  
 下列範例會使用`CFileException::GetErrorMessage`。  
  
 [!code-cpp[NVC_MFCExceptions #&22;](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]  
  
##  <a name="m_cause"></a>CFileException::m_cause  
 包含 `CFileException` 列舉類型所定義的值。  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>備註  
 此資料成員是 `int` 類型的公用變數。 列舉程式及其意義如下：  
  
- `CFileException::none`0︰ 沒有發生錯誤。  
  
- `CFileException::genericException`1︰ 發生意外的錯誤。  
  
- `CFileException::fileNotFound`2︰ 找不到檔案。  
  
- `CFileException::badPath`3︰ 整個或部分路徑無效。  
  
- `CFileException::tooManyOpenFiles`4︰ 超出允許的開啟檔案數目。  
  
- `CFileException::accessDenied`5︰ 無法存取檔案。  
  
- `CFileException::invalidFile`6︰ 嘗試使用無效的檔案控制代碼。  
  
- `CFileException::removeCurrentDir`7︰ 無法移除目前工作目錄。  
  
- `CFileException::directoryFull`8︰ 有沒有更多的目錄項目。  
  
- `CFileException::badSeek`9︰ 嘗試設定檔案指標時發生錯誤。  
  
- `CFileException::hardIO`10︰ 硬體錯誤。  
  
- `CFileException::sharingViolation`11︰ 共用。EXE 未載入，或共用的區域被鎖定。  
  
- `CFileException::lockViolation`12︰ 嘗試鎖定已被鎖定的區域。  
  
- `CFileException::diskFull`14︰ 磁碟已滿。  
  
- `CFileException::endOfFile`15︰ 已到達檔案結尾。  
  
    > [!NOTE]
    >  這些 `CFileException` 原因列舉程式不同於 `CArchiveException` 原因列舉程式。  
  
    > [!NOTE]
    > `CArchiveException::generic` 已被取代。 請改用 `genericException`。 如果 `generic` 用在應用程式中，並且是以 /clr 建立，所產生的語法錯誤將不易破解。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&30;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]  
  
##  <a name="m_loserror"></a>CFileException::m_lOsError  
 包含這個例外狀況的作業系統錯誤碼。  
  
```  
LONG m_lOsError;  
```  
  
### <a name="remarks"></a>備註  
 請參閱您作業系統的技術手冊錯誤碼的清單。 此資料成員是類型的公用變數**長**。  
  
##  <a name="m_strfilename"></a>CFileException::m_strFileName  
 包含這個例外狀況的檔案名稱。  
  
```  
CString m_strFileName;  
```  
  
##  <a name="oserrortoexception"></a>CFileException::OsErrorToException  
 傳回列舉值，對應到給定`lOsError`值。 如果錯誤碼是未知，則此函數會傳回**CFileException::generic**。  
  
```  
static int PASCAL OsErrorToException(LONG lOsError);
```  
  
### <a name="parameters"></a>參數  
 `lOsError`  
 操作系統特定的錯誤碼。  
  
### <a name="return-value"></a>傳回值  
 對應至指定的作業系統錯誤值的列舉的值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&27;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]  
  
##  <a name="throwerrno"></a>CFileException::ThrowErrno  
 建構`CFileException`物件對應到給定`nErrno`值，則會擲回例外狀況。  
  
```  
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nErrno`  
 整數錯誤碼 ERRNO 執行時期 include 檔中所定義。H.  
  
 `lpszFileName`  
 造成例外狀況，如果使用字串，包含檔案名稱的指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&28;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]  
  
##  <a name="throwoserror"></a>CFileException::ThrowOsError  
 擲回`CFileException`對應於指定`lOsError`值。 如果錯誤碼是未知，則函式會擲回例外狀況編碼成**CFileException::generic**。  
  
```  
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lOsError`  
 操作系統特定的錯誤碼。  
  
 `lpszFileName`  
 造成例外狀況，如果使用字串，包含檔案名稱的指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&29;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CException 類別](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [例外狀況處理](../../mfc/reference/exception-processing.md)




