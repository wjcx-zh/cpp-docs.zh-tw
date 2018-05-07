---
title: CHtmlEditDoc 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de452365a02b69798c62e2eecfd8051afcf08bb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc 類別
與[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)，提供 WebBrowser 編輯平台的 MFC 文件檢視架構內容中的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE CHtmlEditDoc : public CDocument  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
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
  
##  <a name="chtmleditdoc"></a>  CHtmlEditDoc::CHtmlEditDoc  
 建構**CHtmlEditDoc**物件。  
  
```  
CHtmlEditDoc();
```  
  
##  <a name="getview"></a>  CHtmlEditDoc::GetView  
 擷取[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)物件附加至這份文件。  
  
```  
virtual CHtmlEditView* GetView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 讓指標回到文件的**CHtmlEditView**物件。  
  
##  <a name="ismodified"></a>  CHtmlEditDoc::IsModified  
 傳回相關聯的檢視 WebBrowser 控制項是否包含使用者已修改的文件。  
  
```  
virtual BOOL IsModified();
```  
  
##  <a name="openurl"></a>  CHtmlEditDoc::OpenURL  
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

