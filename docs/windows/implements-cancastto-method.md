---
title: 'Implements:: cancastto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 328691877a3b129c852460f8f68cdd3db4974e6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595295"
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo 方法

取得指定的介面指標。

## <a name="syntax"></a>語法

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>參數

*riid*  
參考介面識別碼。

*ppv*  
如果成功，介面的指標所指定*riid*。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，HRESULT，表示錯誤，例如 E_NOINTERFACE。

## <a name="remarks"></a>備註

這是執行 QueryInterface 作業的內部協助程式函式。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Implements 結構](../windows/implements-structure.md)