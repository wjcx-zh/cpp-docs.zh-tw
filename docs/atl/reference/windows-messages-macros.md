---
title: "Windows 訊息巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
caps.latest.revision: 16
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: be814c0a2ade7df8f7a4d6863627e79efe0a48bc
ms.lasthandoff: 02/24/2017

---
# <a name="windows-messages-macros"></a>Windows 訊息巨集
這個巨集將轉送的視窗訊息。  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|用來轉送至另一個視窗進行處理的視窗所接收的訊息。|  

## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h 
   
##  <a name="a-namewmforwardmsga--wmforwardmsg"></a><a name="wm_forwardmsg"></a>WM_FORWARDMSG  
 這個巨集會轉送至另一個視窗進行處理的視窗所接收的訊息。  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>傳回值  
 非零值已處理訊息，零如果不是。  
  
### <a name="remarks"></a>備註  
 使用`WM_FORWARDMSG`轉送給處理另一個視窗的視窗所接收的訊息。 LPARAM 和 WPARAM 參數使用，如下所示︰  
  
|參數|使用方式|  
|---------------|-----------|  
|WPARAM|由使用者定義的資料|  
|LPARAM|指標`MSG`結構，其中包含訊息的相關資訊|  
  
### <a name="example"></a>範例  
 在下列範例中，`m_hWndOther`代表接收此訊息的視窗。  
  
 [!code-cpp[NVC_ATL_Windowing #&137;](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)

