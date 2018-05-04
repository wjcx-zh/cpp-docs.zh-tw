---
title: Windows 訊息巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21bb273b94f871e253ab927238c96256f46e2b3a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="windows-messages-macros"></a>Windows 訊息巨集
這個巨集將轉送視窗訊息。  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|使用來轉送至另一個視窗，進行處理的視窗所接收的訊息。|  

## <a name="requirements"></a>需求  
 **標頭：** atlbase.h 
   
##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG  
 這個巨集將轉送至另一個視窗，進行處理的視窗所接收的訊息。  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已處理訊息，如果零不。  
  
### <a name="remarks"></a>備註  
 使用`WM_FORWARDMSG`轉送至另一個視窗，進行處理的視窗所接收的訊息。 LPARAM 和 WPARAM 參數可用，如下所示：  
  
|參數|使用量|  
|---------------|-----------|  
|WPARAM|由使用者定義的資料|  
|LPARAM|指標`MSG`結構，其中包含訊息的相關資訊|  
  
### <a name="example"></a>範例  
 在下列範例中，`m_hWndOther`代表收到這個訊息的視窗。  
  
 [!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)
