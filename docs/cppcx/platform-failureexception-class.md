---
title: Platform::FailureException 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::FailureException::FailureException
- VCCORLIB/Platform::FailureException
helpviewer_keywords:
- Platform::FailureException
ms.assetid: 1729cd07-bfc2-448e-9db5-185d5cbf5b81
ms.openlocfilehash: f527271b50382a9aec1585e139a0083135315473
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383330"
---
# <a name="platformfailureexception-class"></a>Platform::FailureException 類別

作業失敗時擲回。 這是 E_FAIL HRESULT 的對等用法。

## <a name="syntax"></a>語法

```cpp
public ref class FailureException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md) 類別。

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="see-also"></a>另請參閱

[Platform::COMException 類別](../cppcx/platform-comexception-class.md)
