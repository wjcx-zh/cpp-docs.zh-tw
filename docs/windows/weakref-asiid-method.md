---
title: 'Weakref:: Asiid 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e5ff6510463a6fed06534236612feb460919e37
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643481"
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID 方法
設定指定`ComPtr`指標參數代表指定的介面識別碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
### <a name="parameters"></a>參數  
 *riid*  
 介面識別碼。  
  
 *ptr*  
 這項作業完成時，表示參數的物件*riid*。  
  
## <a name="return-value"></a>傳回值  
  
-   如果這項作業成功，則為 S_OK否則，指出原因的 HRESULT 作業失敗，並*ptr*設為**nullptr**。  
  
-   如果這項作業成功，但目前為 S_OK **WeakRef**物件已被釋放。 參數*ptr*設為**nullptr**。  
  
-   如果這項作業成功，但目前為 S_OK **WeakRef**物件不衍生自參數*riid*。 參數*ptr*設為**nullptr**。 (如需詳細資訊，請參閱＜備註＞)。  
  
## <a name="remarks"></a>備註  
 如果，就會發出錯誤參數*riid*不衍生自`IInspectable`。 這個錯誤會取代傳回值。  
  
 第一個範本是程式碼中應該使用的表單。 第二個範本 (此處未顯示但會在標頭檔中宣告) 是支援 C++ 語言功能的內部協助程式特製化，例如 [auto](../cpp/auto-cpp.md) 類型推斷關鍵字。  
  
 從 Windows 10 SDK 開始，這個方法不會設定**WeakRef**執行個體**nullptr**如果無法取得弱式參考，因此您應該避免檢查錯誤的程式碼，檢查**WeakRef** for **nullptr**。 相反地，檢查*ptr* for **nullptr**。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [WeakRef 類別](../windows/weakref-class.md)