---
title: "AFX_EXTENSION_MODULE 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
caps.latest.revision: 11
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: f2699316266e9cc061fa898c4176e36ae8323b33
ms.lasthandoff: 02/24/2017

---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE 結構
`AFX_EXTENSION_MODULE` MFC 擴充 Dll 的初始化期間用來保存延伸 DLL 模組的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
struct AFX_EXTENSION_MODULE  
{  
    BOOL bInitialized;  
    HMODULE hModule;  
    HMODULE hResource;  
    CRuntimeClass* pFirstSharedClass;  
    COleObjectFactory* pFirstSharedFactory;  
};  
```  
  
#### <a name="parameters"></a>參數  
 *bInitialized*  
 **TRUE**如果 DLL 模組初始化具有`AfxInitExtensionModule`。  
  
 `hModule`  
 指定 DLL 模組的控制代碼。  
  
 *hResource*  
 指定自訂資源 DLL 模組的控制代碼。  
  
 *pFirstSharedClass*  
 資訊的指標 (`CRuntimeClass`結構) 的相關 DLL 模組的第一個執行階段類別。 用來提供執行階段類別清單的開頭。  
  
 *pFirstSharedFactory*  
 DLL 模組的第一個物件 factory 的指標 (`COleObjectFactory`物件)。 用來提供類別 factory 清單的開頭。  
  
## <a name="remarks"></a>備註  
 MFC 擴充 Dll 需要做兩件事，在其`DllMain`函式︰  
  
-   呼叫[AfxInitExtensionModule](http://msdn.microsoft.com/library/15f0c820-ff34-4da6-8077-79afbbb8dac1)並檢查傳回的值。  
  
-   建立**CDynLinkLibrary**物件如果將匯出的 DLL [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件或它自己的自訂資源。  
  
 `AFX_EXTENSION_MODULE`結構用來保存一份延伸 DLL 的模組狀態，包括已初始化擴充 DLL 的一部分之前執行的一般靜態物件建構的執行階段類別物件的副本`DllMain`輸入。 例如:   
  
 [!code-cpp[NVC_MFC_DLL&#2;](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 模組資訊儲存在`AFX_EXTENSION_MODULE`結構可以複製到**CDynLinkLibrary**物件。 例如:   
  
 [!code-cpp[NVC_MFC_DLL&#5;](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](http://msdn.microsoft.com/library/15f0c820-ff34-4da6-8077-79afbbb8dac1)   
 [AfxTermExtensionModule](http://msdn.microsoft.com/library/b64de402-f1e3-4c26-9823-08c07876aaaa)


