---
title: IID_PPV_ARGS_Helper 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 351e0755f786e69da1dea6a925b7afc7cb6d6bf1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011636"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 函式
確認指定的引數的型別衍生自`IUnknown`介面。  
  
> [!IMPORTANT]
>  此樣板特製化支援 WRL 結構，而且不是直接從您的程式碼使用。 使用[IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx)改。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename T>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 引數的型別*pp*。  
  
 *前置處理*  
 雙向間接指標。  
  
## <a name="return-value"></a>傳回值  
 引數*pp*轉換成指標-至-a-指標**void**。  
  
## <a name="remarks"></a>備註  
 如果，就會產生編譯時期錯誤的範本參數*T*不是衍生自`IUnknown`。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
## <a name="see-also"></a>另請參閱  
 [參考 （Windows 執行階段程式庫）](http://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)