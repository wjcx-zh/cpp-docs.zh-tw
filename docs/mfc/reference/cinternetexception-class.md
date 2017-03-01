---
title: "CInternetException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetException
dev_langs:
- C++
helpviewer_keywords:
- exception handling, Internet operations
- exceptions, Internet
- CInternetException class
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: a128095cfc443f0ea8de4cb4028b903929a83f47
ms.lasthandoff: 02/24/2017

---
# <a name="cinternetexception-class"></a>CInternetException 類別
表示與網際網路作業相關的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class CInternetException : public CException  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CInternetException::CInternetException](#cinternetexception)|建構 `CInternetException` 物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CInternetException::m_dwContext](#m_dwcontext)|造成例外狀況的作業相關聯的內容值。|  
|[CInternetException::m_dwError](#m_dwerror)|造成例外狀況的錯誤。|  
  
## <a name="remarks"></a>備註  
 `CInternetException`類別包含兩個公用資料成員︰ 一個保存的例外狀況相關聯的錯誤程式碼，並另包含與錯誤相關聯的網際網路應用程式的內容識別碼。  
  
 如需網際網路應用程式的內容識別項的詳細資訊，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxinet.h  
  
##  <a name="a-namecinternetexceptiona--cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>CInternetException::CInternetException  
 此成員函式時，會呼叫`CInternetException`建立物件。  
  
```  
CInternetException(DWORD dwError);
```  
  
### <a name="parameters"></a>參數  
 `dwError`  
 造成例外狀況的錯誤。  
  
### <a name="remarks"></a>備註  
 擲回 CInternetException，呼叫 MFC 的全域函式[AfxThrowInternetException](http://msdn.microsoft.com/library/c9645b10-9541-48b2-8b0c-94ca33fed3cb)。  
  
##  <a name="a-namemdwcontexta--cinternetexceptionmdwcontext"></a><a name="m_dwcontext"></a>CInternetException::m_dwContext  
 相關的網際網路作業相關聯的內容值。  
  
```  
DWORD_PTR m_dwContext;  
```  
  
### <a name="remarks"></a>備註  
 中原本指定的內容識別碼[CInternetSession](../../mfc/reference/cinternetsession-class.md)傳遞 MFC [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)-和[CInternetFile](../../mfc/reference/cinternetfile-class.md)-衍生的類別。 您可以覆寫這個預設值，並將任何指派`dwContext`參數您選擇的值。 `dwContext`與指定之任何的物件作業有關聯。 `dwContext`識別所傳回的作業的狀態資訊[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。  
  
##  <a name="a-namemdwerrora--cinternetexceptionmdwerror"></a><a name="m_dwerror"></a>CInternetException::m_dwError  
 造成例外狀況的錯誤。  
  
```  
DWORD m_dwError;  
```  
  
### <a name="remarks"></a>備註  
 此錯誤的值可能是系統 WINERROR 中找到的錯誤碼。H 或從 WININET 錯誤值。H.  
  
 如需 Win32 錯誤碼的清單，請參閱[錯誤碼](http://msdn.microsoft.com/library/windows/desktop/ms681381)。 如需網際網路特定錯誤訊息，請參閱。 這兩個主題[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [CException 類別](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CException 類別](../../mfc/reference/cexception-class.md)

