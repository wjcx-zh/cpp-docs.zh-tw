---
title: AFX_EXTENSION_MODULE 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6560bf337f6e146bba19e41d56727945df771dd2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE 結構
`AFX_EXTENSION_MODULE` MFC 擴充 Dll 的初始化期間用來容納 MFC 擴充 DLL 模組的狀態。  
  
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
 指定 DLL 模組控制的代碼。  
  
 *hResource*  
 指定 DLL 自訂資源模組的控制代碼。  
  
 *pFirstSharedClass*  
 資訊的指標 (`CRuntimeClass`結構) 的相關 DLL 模組的第一個執行階段類別。 用來提供執行階段類別清單的開頭。  
  
 *pFirstSharedFactory*  
 DLL 模組的第一個物件 factory 的指標 (`COleObjectFactory`物件)。 用來提供類別 factory 清單的開頭。  
  
## <a name="remarks"></a>備註  
 MFC 擴充 Dll 需要做兩件事中, 其`DllMain`函式：  
  
-   呼叫[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)並檢查傳回的值。  
  
-   建立**CDynLinkLibrary**物件如果將匯出的 DLL [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件，或有它自己的自訂資源。  
  
 `AFX_EXTENSION_MODULE`結構用來保存一份 MFC 擴充 DLL 的模組狀態，包括 MFC 擴充 DLL 初始化之前執行的一般靜態物件建構的一部分的執行階段類別物件的副本`DllMain`是輸入。 例如:   
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 模組資訊儲存在`AFX_EXTENSION_MODULE`結構複製到**CDynLinkLibrary**物件。 例如:   
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)   
 [AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)

