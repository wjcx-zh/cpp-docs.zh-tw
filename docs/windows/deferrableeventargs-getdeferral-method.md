---
title: 'Deferrableeventargs:: Getdeferral 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 47376a055da1625f718b7b2a8b6dbf4fe703e533
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601801"
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral 方法

取得參考[延遲](http://go.microsoft.com/fwlink/p/?linkid=526520)代表延期的事件的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```

### <a name="parameters"></a>參數

*結果*  
將參考的指標[延遲](http://go.microsoft.com/fwlink/p/?linkid=526520)物件呼叫完成時。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="remarks"></a>備註

如需程式碼範例，請參閱 < [DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)。

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)