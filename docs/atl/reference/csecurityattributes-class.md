---
title: CSecurityAttributes 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03bda174fb85fa6857e22b851b93bcf1b3192716
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357502"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes 類別
這個類別是安全性屬性結構的精簡型包裝函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Csecurityattributes:: Set](#set)|呼叫此方法以設定的屬性`CSecurityAttributes`物件。|  
  
## <a name="remarks"></a>備註  
 **ATTRIBUTES**結構包含[安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa379561)用於建立物件，並指定擷取透過指定此結構的控制代碼是否可繼承。  
  
 如需在 Windows 中的存取控制模型的簡介，請參閱[存取控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsecurity.h  
  
##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes  
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
  
##  <a name="set"></a>  Csecurityattributes:: Set  
 呼叫此方法以設定的屬性`CSecurityAttributes`物件。  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>參數  
 `rSecurityDescriptor`  
 安全性描述元的參考。  
  
 `bInheritHandle`  
 指定是否在建立新處理序時繼承傳回的控制代碼。 如果此成員為 true，新處理序會繼承控制代碼。  
  
### <a name="remarks"></a>備註  
 這個方法可由建構函式來初始化`CSecurityAttributes`物件。  
  
## <a name="see-also"></a>另請參閱  
 [安全性範例](../../visual-cpp-samples.md)   
 [SECURITY ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [安全性描述元](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [安全性全域函式](../../atl/reference/security-global-functions.md)
