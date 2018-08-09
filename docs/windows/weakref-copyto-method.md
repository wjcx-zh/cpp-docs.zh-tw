---
title: 'Weakref:: Copyto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88a092255655aaea0e06e8f69b520789f441d379
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016284"
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo 方法
指派介面指標 (如有提供) 給指定的指標變數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
### <a name="parameters"></a>參數  
 *U*  
 指標`IInspectable`介面。 如果，就會發出錯誤*U*不衍生自`IInspectable`。  
  
 *riid*  
 介面識別碼。 如果，就會發出錯誤*riid*不衍生自`IWeakReference`。  
  
 *ptr*  
 雙向間接指標`IInspectable`或`IWeakReference`。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK，否則會是 HRESULT 指出失敗。 如需詳細資訊，請參閱**備註**。  
  
## <a name="remarks"></a>備註  
 傳回值 S_OK 只表示此作業已成功，而不會指出是否已將弱式參考解析為強式參考。 如果傳回 S_OK，測試參數*p*為強式參考，也就是參數*p*不等於**nullptr**。  
  
 從 Windows 10 SDK 開始，這個方法不會設定**WeakRef**執行個體**nullptr**如果無法取得弱式參考，因此您應該避免檢查程式碼，檢查 weakref 有無錯誤**nullptr**。 相反地，檢查*ptr* for **nullptr**。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [WeakRef 類別](../windows/weakref-class.md)