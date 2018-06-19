---
title: _U_STRINGorID 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
dev_langs:
- C++
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a601b1c64b28681c13a0b9e8f42156d8820cb4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359658"
---
# <a name="ustringorid-class"></a>_U_STRINGorID 類別
這個引數的介面卡類別可讓任一資源名稱 ( `LPCTSTR`s) 或資源識別碼 ( **UINT**s) 而不需要將 ID 為字串，使用呼叫端傳遞至函式**MAKEINTRESOURCE**巨集。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class _U_STRINGorID
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|建構函式。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|資源識別項。|  
  
## <a name="remarks"></a>備註  
 這個類別針對這類實作 Windows 資源管理 API 的包裝函式[FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042)， [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072)，和[LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990)接受函式`LPCTSTR`引數，可能是資源的名稱，或是它的 id。  
  
 類別會定義兩個建構函式多載： 其中一個接受`LPCTSTR`引數，而另一個接受**UINT**引數。 **UINT**引數會轉換成相容於 Windows 資源管理函式使用的資源類型**MAKEINTRESOURCE**巨集和結果儲存在該類別的單一資料成員， [m_lpstr](#_u_stringorid__m_lpstr)。 引數`LPCTSTR`建構函式會以無轉換直接儲存。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr  
 類別會保存的值傳遞給其建構函式之一，作為公用`LPCTSTR`資料成員。  
  
```
LPCTSTR m_lpstr;
```  
  
##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID  
 **UINT**建構函式會將其引數轉換成相容於 Windows 資源管理函式使用的資源類型**MAKEINTRESOURCE**巨集和結果儲存在該類別的單一資料成員[m_lpstr](#_u_stringorid__m_lpstr)。  
  
```
_U_STRINGorID(UINT nID);  
_U_STRINGorID(LPCTSTR lpString);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 資源識別碼。  
  
 `lpString`  
 資源名稱。  
  
### <a name="remarks"></a>備註  
 引數`LPCTSTR`建構函式會以無轉換直接儲存。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
