---
title: "CHtmlEditDoc 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditDoc class
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
caps.latest.revision: 24
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
ms.openlocfilehash: 1d9651c5009fd8f4c742c6b9bf08e32bd67c7d30
ms.lasthandoff: 02/24/2017

---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc 類別
使用[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)，提供 WebBrowser 編輯平台的 MFC 文件檢視架構內容中的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE CHtmlEditDoc : public CDocument  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|建構 `CHtmlEditDoc` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHtmlEditDoc::GetView](#getview)|擷取`CHtmlEditView`物件附加至這份文件。|  
|[CHtmlEditDoc::IsModified](#ismodified)|傳回相關聯的檢視 WebBrowser 控制項是否包含使用者已修改的文件。|  
|[CHtmlEditDoc::OpenURL](#openurl)|開啟的 URL。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `CHtmlEditDoc`  
  
## <a name="requirements"></a>需求  
 **Header:** afxhtml.h  
  
##  <a name="chtmleditdoc"></a>CHtmlEditDoc::CHtmlEditDoc  
 建構**CHtmlEditDoc**物件。  
  
```  
CHtmlEditDoc();
```  
  
##  <a name="getview"></a>CHtmlEditDoc::GetView  
 擷取[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)物件附加至這份文件。  
  
```  
virtual CHtmlEditView* GetView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 將指標傳回至文件的**CHtmlEditView**物件。  
  
##  <a name="ismodified"></a>CHtmlEditDoc::IsModified  
 傳回相關聯的檢視 WebBrowser 控制項是否包含使用者已修改的文件。  
  
```  
virtual BOOL IsModified();
```  
  
##  <a name="openurl"></a>CHtmlEditDoc::OpenURL  
 開啟的 URL。  
  
```  
virtual BOOL OpenURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>參數  
 `lpszURL`  
 若要開啟 URL。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
## <a name="see-also"></a>另請參閱  
 [HTMLEdit 範例](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


