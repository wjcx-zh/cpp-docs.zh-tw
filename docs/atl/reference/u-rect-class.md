---
title: _U_RECT 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
dev_langs:
- C++
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ebb76d2f373862b39f2a3742481e14523a7a94b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882217"
---
# <a name="urect-class"></a>_U_RECT 類別
這個引數的配接器類別可讓`RECT`指標或參考傳遞至函式實作方面的指標。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class _U_RECT
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|建構函式。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|指標`RECT`。|  
  
## <a name="remarks"></a>備註  
 此類別會定義兩個建構函式多載： 其中一個接受**RECT &** 引數，而另一個接受`LPRECT`引數。 第一個建構函式會參考引數的位址儲存在該類別的單一資料成員中， [m_lpRect](#_u_rect__m_lprect)。 轉換不直接儲存的指標建構函式的引數。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect  
 類別會保存的值傳遞至其建構函式為公用`LPRECT`資料成員。  
  
```
LPRECT m_lpRect;
```  
  
##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT  
 參考引數的位址儲存在該類別的單一資料成員中， [m_lpRect](#_u_rect__m_lprect)。  
  
```
_U_RECT(RECT& rc);  
_U_RECT(LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 *rc*  
 A`RECT`參考。  
  
 *lpRect*  
 A`RECT`指標。  
  
### <a name="remarks"></a>備註  
 轉換不直接儲存的指標建構函式的引數。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
