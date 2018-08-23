---
title: 'Ftmbase:: Disconnectobject 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
dev_langs:
- C++
helpviewer_keywords:
- DisconnectObject method
ms.assetid: 33253eec-3a65-4e72-8525-0249245a4790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b467162d2f5cc5b04bc43a6d31019eb08e17e750
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595402"
---
# <a name="ftmbasedisconnectobject-method"></a>FtmBase::DisconnectObject 方法

強制釋放物件的所有外部連線。 物件的伺服器會呼叫這個方法之前關閉物件的實作。

## <a name="syntax"></a>語法

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>參數

*dwReserved*  
保留以備將來之用；必須為零。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="requirements"></a>需求

**標頭：** ftm.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[FtmBase 類別](../windows/ftmbase-class.md)