---
title: "_U_MENUorID 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs:
- C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f7c0a5c34c4e103f830a029f58cdfa00dcb58a32
ms.lasthandoff: 02/24/2017

---
# <a name="umenuorid-class"></a>_U_MENUorID 類別
這個類別會提供包裝函式的**CreateWindow**和**CreateWindowEx**。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class _U_MENUorID
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|建構函式。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|功能表的控點。|  
  
## <a name="remarks"></a>備註  
 這個引數的配接器類別可讓任一 Id ( **UINT**s) 或功能表的控制代碼 ( `HMENU`s) 傳遞至函式，而不需要呼叫端的組件上的明確轉型。  
  
 這個類別主要用來實作包裝函式以 Windows API，尤其是[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)和[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)函式，這兩種接受`HMENU`可能是子視窗識別項的引數 ( **UINT**) 而不是功能表控制代碼。 例如，您所見中使用這個類別做為參數[CWindowImpl::Create](cwindowimpl-class.md#create)。  

  
 類別會定義兩個建構函式多載︰ 其中一個接受**UINT**引數，而另一個接受`HMENU`引數。 **UINT**引數只會轉換成`HMENU`建構函式和結果儲存在該類別的單一資料成員， [m_hMenu](#_u_menuorid__m_hmenu)。 引數`HMENU`建構函式會儲存直接而無需轉換。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="a-nameumenuoridmhmenua--umenuoridmhmenu"></a><a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu  
 類別會保存的值傳遞至其中一個建構函式為公用`HMENU`資料成員。  
  
```
HMENU m_hMenu;
```  
  
##  <a name="a-nameumenuoridumenuorida--umenuoridumenuorid"></a><a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID  
 **UINT**引數只會轉換成`HMENU`建構函式和結果儲存在該類別的單一資料成員， [m_hMenu](#_u_menuorid__m_hmenu)。  
  
```
_U_MENUorID(UINT nID);  
_U_MENUorID(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 子視窗的識別項。  
  
 `hMenu`  
 功能表控制代碼。  
  
### <a name="remarks"></a>備註  
 引數`HMENU`建構函式會儲存直接而無需轉換。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

