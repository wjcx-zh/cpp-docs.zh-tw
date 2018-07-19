---
title: _com_error::_com_error |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::_com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec16faa9881fc1c69dca5f8f39b8797cf0fcff0d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942852"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Microsoft 專屬**  
  
 建構 `_com_error` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
_com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false) throw( );  

_com_error( const _com_error& that ) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *hr*  
 HRESULT 資訊。  
  
 *perrinfo*  
 `IErrorInfo` 物件  
  
 `bool fAddRef=false`  
 會導致非 null 值上呼叫 AddRef 的建構函式`IErrorInfo`介面。 如此可在將介面的擁有權傳入 `_com_error` 物件的一般情況下，提供正確的參考計數，例如：  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 如果您不想要傳送擁有權轉移給您的程式碼`_com_error`物件，而`AddRef`才能位移`Release`在`_com_error`解構函式，建構物件，如下所示：  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *,*  
 現有的 `_com_error` 物件。  
  
## <a name="remarks"></a>備註  
 第一個建構函式會建立新的物件，指定的 HRESULT 和選擇性`IErrorInfo`物件。 第二個方法會建立現有 `_com_error` 物件的複本。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)