---
title: "COleDispatchException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchException class
- Automation, exceptions
- exceptions, OLE
- OLE exceptions, to IDispatch interface
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0071e57b6c8f6bec73712186e8ff8baa9bfcc165
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="coledispatchexception-class"></a>COleDispatchException 類別
處理 OLE `IDispatch` 介面 (OLE Automation 的主要部分) 特定的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDispatchException : public CException  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|錯誤的說明內容。|  
|[COleDispatchException::m_strDescription](#m_strdescription)|口頭錯誤描述。|  
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|說明檔，以搭配`m_dwHelpContext`。|  
|[COleDispatchException::m_strSource](#m_strsource)|產生例外狀況的應用程式。|  
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`為特定的錯誤碼。|  
  
## <a name="remarks"></a>備註  
 如同其他的例外狀況類別衍生自`CException`基底類別，`COleDispatchException`可以搭配**擲回**， `THROW_LAST`，**嘗試**，**攔截**， `AND_CATCH`，和`END_CATCH`巨集。  
  
 一般情況下，您應該呼叫[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)建立並擲回`COleDispatchException`物件。  
  
 如需有關例外狀況的詳細資訊，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[例外狀況︰ OLE 例外狀況](../../mfc/exceptions-ole-exceptions.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleDispatchException`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="m_dwhelpcontext"></a>COleDispatchException::m_dwHelpContext  
 識別您的應用程式說明中的說明內容 (。HLP) 檔案。  
  
```  
DWORD m_dwHelpContext;  
```  
  
### <a name="remarks"></a>備註  
 這個成員由函式設定[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)擲回例外狀況時。  
  
### <a name="example"></a>範例  
  請參閱範例[COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)。  
  
##  <a name="m_strdescription"></a>COleDispatchException::m_strDescription  
 包含詳細錯誤描述，例如 「 磁碟已滿。 」  
  
```  
CString m_strDescription;  
```  
  
### <a name="remarks"></a>備註  
 這個成員由函式設定[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)擲回例外狀況時。  
  
### <a name="example"></a>範例  
  請參閱範例[COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)。  
  
##  <a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile  
 架構會填入這個應用程式的說明檔的名稱的字串。  
  
```  
CString m_strHelpFile;  
```  
  
##  <a name="m_strsource"></a>COleDispatchException::m_strSource  
 架構會填入此字串，以產生例外狀況的應用程式的名稱。  
  
```  
CString m_strSource;  
```  
  
### <a name="example"></a>範例  
  請參閱範例[COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)。  
  
##  <a name="m_wcode"></a>COleDispatchException::m_wCode  
 包含您的應用程式特定的錯誤碼。  
  
```  
WORD m_wCode;  
```  
  
### <a name="remarks"></a>備註  
 這個成員由函式設定[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)擲回例外狀況時。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CALCDRIV](../../visual-cpp-samples.md)   
 [CException 類別](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDispatchDriver 類別](../../mfc/reference/coledispatchdriver-class.md)   
 [COleException 類別](../../mfc/reference/coleexception-class.md)

