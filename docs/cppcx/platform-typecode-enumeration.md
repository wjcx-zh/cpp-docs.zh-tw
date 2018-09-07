---
title: 'Platform:: typecode 列舉 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::TypeCode
dev_langs:
- C++
helpviewer_keywords:
- Platform::TypeCode Enumeration
ms.assetid: 93c1305f-eb16-4bec-aead-f88d9518b4cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb19a922655a77a2f7a2b5806c9b721f17e028f8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104169"
---
# <a name="platformtypecode-enumeration"></a>Platform::TypeCode 列舉

指定代表內建類型的數值分類。

## <a name="syntax"></a>語法

```cpp
enum class TypeCode {};
```

### <a name="members"></a>成員

|類型程式碼|描述|
|---------------|-----------------|
|Boolean|Platform::Boolean 類型。|
|Char16|default::char16 類型。|
|DateTime|DateTime 型別。|
|Decimal|數字類型。|
|Double|default::float64 類型。|
|Empty|Void|
|Int16|default::int16 類型。|
|Int32|default::int32 類型。|
|Int64|default::int64 類型。|
|Int8|default::int8 類型。|
|Object|Platform::Object 類型。|
|Single|default::float32 類型。|
|String|Platform::String 類型。|
|UInt16|default::uint16 類型。|
|UInt32|default::uint32 類型。|
|UInt64|default::uint64 類型。|
|UInt8|default::uint8 類型。|

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd