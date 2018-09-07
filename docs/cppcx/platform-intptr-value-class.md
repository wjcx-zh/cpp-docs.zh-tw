---
title: 'Platform:: intptr 實值類別 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
dev_langs:
- C++
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0c6f7bc2cdc6b1478aba26c1ce0db48464a9ef2
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104033"
---
# <a name="platformintptr-value-class"></a>Platform::IntPtr 實值類別

表示大小適用於平台、帶正負號的指標或控制代碼 (32 位元或 64 位元)。

## <a name="syntax"></a>語法

```cpp
public value struct IntPtr
```

### <a name="members"></a>成員

IntPtr 具有下列成員：

|成員|描述|
|------------|-----------------|
|[IntPtr::IntPtr](#ctor)|初始化 IntPtr 的新執行個體。|
|[IntPtr::op_explicit 運算子](#op-explicit)|將指定的參數轉換為 IntPtr，或將指標轉換為 IntPtr 值。|
|[IntPtr::ToInt32](#toint32)|將目前 IntPtr 轉換為 32 位元整數。|

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="ctor"> </a> IntPtr::IntPtr 建構函式

使用指定的值初始化 IntPtr 的新執行個體。

### <a name="syntax"></a>語法

```cpp
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );
```

### <a name="parameters"></a>參數

*值*<br/>
64 位元控制代碼或指標、64 位元值的指標、或是可轉換為 64 位元值的 32 位元值。

## <a name="op-explicit"> </a> IntPtr::op_explicit 運算子

將指定的參數轉換為 IntPtr，或將指標轉換為 IntPtr 值。

### <a name="syntax"></a>語法

```cpp
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );
```

### <a name="parameters"></a>參數

*Value1*<br/>
控制代碼的指標或 IntPtr。

*Value2*<br/>
可以轉換為 IntPtr 的 32 位元整數。

*value3*<br/>
IntPtr。

### <a name="return-value"></a>傳回值

第一個和第二個運算子傳回 IntPtr。 第三個運算子傳回目前 IntPtr 所表示的值的指標。

## <a name="toint32"> </a> IntPtr::ToInt32 方法

將目前 IntPtr 值轉換為 32 位元整數。

### <a name="syntax"></a>語法

```cpp
int32 IntPtr::ToInt32();
```

### <a name="return-value"></a>傳回值

32 位元整數。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](../cppcx/platform-namespace-c-cx.md)