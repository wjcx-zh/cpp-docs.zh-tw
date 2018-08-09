---
title: 'Weakref:: As 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7dd0dca806c1568d88c20eec6a7ac63e5fb242fb
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020352"
---
# <a name="weakrefas-method"></a>WeakRef::As 方法
設定指定`ComPtr`指標參數代表指定的介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename U>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<typename U>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
### <a name="parameters"></a>參數  
 *U*  
 介面識別碼。  
  
 *ptr*  
 這項作業完成時，表示參數的物件*U*。  
  
## <a name="return-value"></a>傳回值  
  
-   如果這項作業成功，則為 S_OK否則，指出原因的 HRESULT 作業失敗，並*ptr*設為**nullptr**。  
  
-   如果這項作業成功，但目前為 S_OK **WeakRef**物件已被釋放。 參數*ptr*設為**nullptr**。  
  
-   如果這項作業成功，但目前為 S_OK **WeakRef**物件不衍生自參數*U*。參數*ptr*設為**nullptr**。  
  
## <a name="remarks"></a>備註  
 如果，就會發出錯誤參數*U*是`IWeakReference`，或不衍生自`IInspectable`。  
  
 第一個範本是程式碼中應該使用的表單。 第二個範本是內部的，支援 C++ 語言功能的協助程式特製化，例如 [auto](../cpp/auto-cpp.md) 類型推斷關鍵字。  
  
 從 Windows 10 SDK 開始，這個方法不會設定**WeakRef**執行個體**nullptr**如果無法取得弱式參考，因此您應該避免檢查錯誤的程式碼，檢查 weakref 有無**nullptr**。 相反地，檢查*ptr* for **nullptr**。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [WeakRef 類別](../windows/weakref-class.md)