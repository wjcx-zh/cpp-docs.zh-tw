---
title: 'Handlet:: Close 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab919b3aeba45462a15900429493225f00909d5a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602450"
---
# <a name="handletclose-method"></a>HandleT::Close 方法

關閉目前**HandleT**物件。

## <a name="syntax"></a>語法

```cpp
void Close();
```

## <a name="remarks"></a>備註

控制代碼就是目前的基礎**HandleT**已關閉，而**HandleT**設為無效的狀態。

如果控制代碼不正確關閉，就會呼叫的執行緒中引發例外狀況。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HandleT 類別](../windows/handlet-class.md)