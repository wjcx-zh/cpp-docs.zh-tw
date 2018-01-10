---
title: "_U_RECT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
dev_langs: C++
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b7efb94f5afdd2f6daa6fa047d36ea51c957d31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="urect-class"></a>_U_RECT 類別
這個引數的配接器類別，可讓 `RECT`指標或參考傳遞至函式指標來實作。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class _U_RECT```  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|The constructor.|  
  
### Public Data Members  
  
|Name|Description|  
|----------|-----------------|  
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Pointer to a `RECT`.|  
  
## Remarks  
 The class defines two constructor overloads: one accepts a **RECT&** argument and the other accepts an `LPRECT` argument. The first constructor stores the address of the reference argument in the class's single data member, [m_lpRect](#_u_rect__m_lprect). The argument to the pointer constructor is stored directly without conversion.  
  
## Requirements  
 **Header:** atlwin.h  
  
##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect  
 The class holds the value passed to either of its constructors as a public `LPRECT` data member.  
  
```
LPRECT m_lpRect;
```  
  
##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT  
 The address of the reference argument is stored in the class's single data member, [m_lpRect](#_u_rect__m_lprect).  
  
```
_U_RECT (RECT & rc);  
_U_RECT (LPRECT lpRect);
```  
  
### Parameters  
 `rc`  
 A `RECT` reference.  
  
 `lpRect`  
 A `RECT` pointer.  
  
### Remarks  
 The argument to the pointer constructor is stored directly without conversion.  
  
## See Also  
 [Class Overview](../../atl/atl-class-overview.md)
