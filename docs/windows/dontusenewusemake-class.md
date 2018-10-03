---
title: DontUseNewUseMake 類別 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c1f3a57401a3ab2efd45cab2dace127010c24e6
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235278"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>備註

防止使用運算子`new`在`RuntimeClass`。 因此，您必須使用[讓函式](../windows/make-function.md)改。

## <a name="members"></a>成員

### <a name="public-operators"></a>公用運算子

名稱                                             | 描述
------------------------------------------------ | ---------------------------------------------------------------------------
[Dontusenewusemake:: Operator 新](#operator-new) | 多載運算子`new`並且讓它無法使用於`RuntimeClass`。

## <a name="inheritance-hierarchy"></a>繼承階層

`DontUseNewUseMake`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="operator-new"></a>Dontusenewusemake:: Operator 新

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>參數

*__unnamed0*<br/>
未命名的參數，指定要配置的記憶體位元組數目。

*放置*<br/>
要配置的類型。

### <a name="return-value"></a>傳回值

可用來傳遞其他引數，如果您多載運算子`new`。

### <a name="remarks"></a>備註

多載運算子`new`並且讓它無法使用於`RuntimeClass`。
