---
title: "COleException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
dev_langs:
- C++
helpviewer_keywords:
- COleException class
- exceptions, OLE
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 059c92c8dc8796cf103cc02533ba5f3526720249
ms.lasthandoff: 02/24/2017

---
# <a name="coleexception-class"></a>COleException 類別
表示與 OLE 作業相關的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class COleException : public CException  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleException::Process](#process)|將轉譯成 OLE 傳回碼攔截的例外狀況。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleException::m_sc](#m_sc)|包含表示例外狀況原因的狀態碼。|  
  
## <a name="remarks"></a>備註  
 `COleException`類別包含保存之原因的例外狀況的狀態程式碼的公用資料成員。  
  
 一般情況下，您不應該建立`COleException`物件直接; 相反地，您應該呼叫[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。  
  
 如需有關例外狀況的詳細資訊，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[例外狀況︰ OLE 例外狀況](../../mfc/exceptions-ole-exceptions.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="m_sc"></a>COleException::m_sc  
 此資料成員會保留之 OLE 狀態碼，指出例外狀況的原因。  
  
```  
SCODE m_sc;  
```  
  
### <a name="remarks"></a>備註  
 這個變數的值由設定[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。  
  
 如需有關`SCODE`，請參閱[結構的 COM 錯誤碼](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&22;](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]  
  
##  <a name="process"></a>COleException::Process  
 呼叫**程序**成員函式以轉譯成 OLE 狀態碼攔截的例外狀況。  
  
```  
static SCODE PASCAL Process(const CException* pAnyException);
```  
  
### <a name="parameters"></a>參數  
 *pAnyException*  
 攔截的例外狀況的指標。  
  
### <a name="return-value"></a>傳回值  
 OLE 狀態碼。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  此函式是**靜態**。  
  
 如需有關`SCODE`，請參閱[結構的 COM 錯誤碼](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CALCDRIV](../../visual-cpp-samples.md)   
 [CException 類別](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




