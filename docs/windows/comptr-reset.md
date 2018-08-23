---
title: ComPtr::Reset |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 86e7716ff4e9a0b4f5132abfd431a2649f22f80f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593089"
---
# <a name="comptrreset"></a>ComPtr::Reset

釋放與此相關聯的介面指標的所有參考**ComPtr**。

## <a name="syntax"></a>語法

```cpp
unsigned long Reset();
```

## <a name="return-value"></a>傳回值

釋放的參考數目 (若有的話)。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ComPtr 類別](../windows/comptr-class.md)