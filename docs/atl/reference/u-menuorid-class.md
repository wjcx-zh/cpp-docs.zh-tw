---
title: "_U_MENUorID 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs: C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ddde6ff5d45c90e675bd2e44ac421e840d1357b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="umenuorid-class"></a>_U_MENUorID 類別
這個類別會提供包裝函式**CreateWindow**和**CreateWindowEx**。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class _U_MENUorID
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|建構函式。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|功能表的控點。|  
  
## <a name="remarks"></a>備註  
 這個引數的介面卡類別可讓任一識別碼 ( **UINT**s) 或功能表的控制代碼 ( `HMENU`s) 要傳遞給函式，而不需要呼叫端的組件上的明確轉換。  
  
 這個類別主要用來實作包裝函式以 Windows API 中，尤其是[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)和[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)函式，這兩種接受`HMENU`可以是子工作的引數視窗識別項 ( **UINT**) 而不是功能表的控制代碼。 比方說，您可以看到在使用這個類別當做參數[CWindowImpl::Create](cwindowimpl-class.md#create)。  

  
 類別會定義兩個建構函式多載： 其中一個接受**UINT**引數，而另一個接受`HMENU`引數。 **UINT**引數只會轉換成`HMENU`中建構函式和結果儲存在該類別的單一資料成員， [m_hMenu](#_u_menuorid__m_hmenu)。 引數`HMENU`建構函式會以無轉換直接儲存。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu  
 類別會保存的值傳遞給其建構函式之一，作為公用`HMENU`資料成員。  
  
```
HMENU m_hMenu;
```  
  
##  <a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID  
 **UINT**引數只會轉換成`HMENU`中建構函式和結果儲存在該類別的單一資料成員， [m_hMenu](#_u_menuorid__m_hmenu)。  
  
```
_U_MENUorID(UINT nID);  
_U_MENUorID(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 子視窗的識別項。  
  
 `hMenu`  
 功能表的控制代碼。  
  
### <a name="remarks"></a>備註  
 引數`HMENU`建構函式會以無轉換直接儲存。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
