---
title: Platform::ChangedStateException 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
ms.openlocfilehash: 79181702c95f8c666b06bdb26319ccb06e55db0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161708"
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException 類別

當物件的內部狀態已經變更時擲回，藉以讓方法的結果失效。

## <a name="syntax"></a>語法

```cpp
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>備註

擲回這個例外狀況的一個例子是，在父集合變更後呼叫集合迭代器或集合檢視的方法時，藉以讓方法的結果失效。

如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md) 類別。

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="see-also"></a>另請參閱

[Platform::COMException 類別](../cppcx/platform-comexception-class.md)
