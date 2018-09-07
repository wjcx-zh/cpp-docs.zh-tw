---
title: 'Platform:: recreateexception 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
dev_langs:
- C++
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28434f6c8c35f2cd4cfc15953f761d28037626e6
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109715"
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException 方法

這個方法僅供內部使用，使用者程式碼並不需要。 請改用 exception:: createexception 方法。

## <a name="syntax"></a>語法

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>參數

*hr*

### <a name="property-valuereturn-value"></a>屬性值/傳回值

根據指定的 HRESULT 傳回新的 Platform::Exception^。
