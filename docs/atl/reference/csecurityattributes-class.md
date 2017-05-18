---
title: "CSecurityAttributes 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
dev_langs:
- C++
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
caps.latest.revision: 24
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 24dfba8b6125172cc2d4ff7a32b61da412bfe2be
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="csecurityattributes-class"></a>CSecurityAttributes 類別
這個類別是安全性屬性結構的精簡型包裝函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSecurityAttributes::Set](#set)|呼叫這個方法來設定的屬性`CSecurityAttributes`物件。|  
  
## <a name="remarks"></a>備註  
 **ATTRIBUTES**結構包含[安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa379561)用於建立物件，並指定是否可繼承擷取藉由指定此結構的控制代碼。  
  
 在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsecurity.h  
  
##  <a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes  
 建構函式。  
  
```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rSecurityDescriptor`  
 安全性描述元的參考。  
  
 `bInheritsHandle`  
 指定是否在建立新處理序時繼承傳回的控制代碼。 如果此成員為 true，新處理序會繼承控制代碼。  
  
##  <a name="set"></a>CSecurityAttributes::Set  
 呼叫這個方法來設定的屬性`CSecurityAttributes`物件。  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rSecurityDescriptor`  
 安全性描述元的參考。  
  
 `bInheritHandle`  
 指定是否在建立新處理序時繼承傳回的控制代碼。 如果此成員為 true，新處理序會繼承控制代碼。  
  
### <a name="remarks"></a>備註  
 這個方法由建構函式來初始化`CSecurityAttributes`物件。  
  
## <a name="see-also"></a>另請參閱  
 [安全性範例](../../visual-cpp-samples.md)   
 [ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性的全域函式](../../atl/reference/security-global-functions.md)

