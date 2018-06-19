---
title: IID_PPV_ARGS_Helper 函式 |Microsoft 文件
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
ms.openlocfilehash: 0cef979ae284a303b120df7d14ae71f311498423
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882338"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 函式
確認指定的引數的型別衍生自`IUnknown`介面。  
  
> [!IMPORTANT]
>  這個樣板特製化支援 WRL 基礎結構，並不是直接從您的程式碼使用。 使用[IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx)改為。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 引數的型別`pp`。  
  
 `pp`  
 雙向間接指標。  
  
## <a name="return-value"></a>傳回值  
 引數`pp`轉換成指標-到-a-指標`void`。  
  
## <a name="remarks"></a>備註  
 會產生編譯時間錯誤的範本參數`T`不是衍生自`IUnknown`。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
## <a name="see-also"></a>另請參閱  
 [參考 （Windows 執行階段程式庫）](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)