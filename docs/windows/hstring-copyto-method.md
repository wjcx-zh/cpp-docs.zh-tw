---
title: 'Hstring:: Copyto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65d8e259b74bcdffbf11c6c96172d918f9db1b50
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570869"
---
# <a name="hstringcopyto-method"></a>HString::CopyTo 方法
複製目前**HString**到 HSTRING 物件的物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *str*  
 接收複本的 HSTRING。  
  
## <a name="remarks"></a>備註  
 這個方法會呼叫[WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx)函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)