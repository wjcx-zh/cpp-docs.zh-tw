---
title: 'Eventtargetarray:: End 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::End
dev_langs:
- C++
helpviewer_keywords:
- End method
ms.assetid: 20c491b8-f355-4d8f-ad14-8f46121d9af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17f79830cf50d83058ee2f2665b94f86a53acd78
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428976"
---
# <a name="eventtargetarrayend-method"></a>EventTargetArray::End 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
ComPtr<IUnknown>* End();
```

## <a name="return-value"></a>傳回值

內部陣列中的事件處理常式的最後一個項目位址。

## <a name="remarks"></a>備註

取得內部陣列中的事件處理常式的最後一個元素的位址。

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[EventTargetArray 類別](../windows/eventtargetarray-class.md)<br/>
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)