---
title: CArchiveException 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac864831e9d3a0cf0cd5e67501f1ac8396f99473
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="carchiveexception-class"></a>CArchiveException 類別
表示序列化例外狀況  
  
## <a name="syntax"></a>語法  
  
```  
class CArchiveException : public CException  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchiveException::CArchiveException](#carchiveexception)|建構 `CArchiveException` 物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CArchiveException::m_cause](#m_cause)|表示例外狀況的原因。|  
|[CArchiveException::m_strFileName](#m_strfilename)|指定此例外狀況的檔案名稱。|  
  
## <a name="remarks"></a>備註  
 `CArchiveException`類別包含公用資料成員，表示例外狀況的原因。  
  
 `CArchiveException` 物件的建構及內擲回[CArchive](../../mfc/reference/carchive-class.md)成員函式。 您可以存取這些物件的範圍內**攔截**運算式。 原因碼與作業系統無關。 如需例外狀況處理的詳細資訊，請參閱[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException  
 建構`CArchiveException`儲存的值物件`cause`物件中。  
  
```  
CArchiveException(
    int cause = CArchiveException::none,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cause`  
 列舉型別變數，指出例外狀況的原因。 如需列舉值的清單，請參閱[m_cause](#m_cause)資料成員。  
  
 `lpszArchiveName`  
 包含名稱的字串會指向`CArchive`造成例外狀況的物件。  
  
### <a name="remarks"></a>備註  
 您可以建立`CArchiveException`物件在堆積上，並擲回它自己或全域函式可讓[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)為您處理它。  
  
 請勿直接; 使用這個建構函式請改為呼叫全域函式`AfxThrowArchiveException`。  
  
##  <a name="m_cause"></a>  CArchiveException::m_cause  
 指定例外狀況的原因。  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>備註  
 此資料成員是 `int` 類型的公用變數。 其值會由`CArchiveException`列舉型別。 列舉程式及其意義如下：  
  
- **CArchiveException::none**未發生任何錯誤。  
  
- **CArchiveException::genericException**未指定的錯誤。  
  
- **CArchiveException::readOnly**嘗試要寫入至載入的開啟的封存。  
  
- **CArchiveException::endOfFile**讀取物件時發生已達結束的檔案。  
  
- **CArchiveException::writeOnly**嘗試讀取儲存開啟的封存。  
  
- **CArchiveException::badIndex**檔案格式無效。  
  
- **CArchiveException::badClass**嘗試讀取物件為錯誤類型的物件。  
  
- **CArchiveException::badSchema**嘗試讀取具有不同版本的類別的物件。  
  
    > [!NOTE]
    >  這些 `CArchiveException` 原因列舉程式不同於 `CFileException` 原因列舉程式。  
  
    > [!NOTE]
    > **CArchiveException::generic**已被取代。 使用**genericException**改為。 如果**泛型**應用程式中使用，並建立以 /clr，將會不容易解密的語法錯誤。  
  
##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName  
 指定此例外狀況的檔案名稱。  
  
```  
CString m_strFileName;  
```  
  
## <a name="see-also"></a>另請參閱  
 [CException 類別](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CArchive 類別](../../mfc/reference/carchive-class.md)   
 [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)   
 [例外狀況處理](../../mfc/reference/exception-processing.md)

