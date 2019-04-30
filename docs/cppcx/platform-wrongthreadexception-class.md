---
title: Platform::WrongThreadException 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WrongThreadException
- VCCORLIB/Platform::WrongThreadException::WrongThreadException
helpviewer_keywords:
- Platform::WrongThreadException
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
ms.openlocfilehash: dde8c9afff6be083580042a958f59e057bc44350
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396076"
---
# <a name="platformwrongthreadexception-class"></a>Platform::WrongThreadException 類別

當執行緒透過不屬於執行緒 Apartment 的 Proxy 物件的介面指標來呼叫時擲回。

## <a name="syntax"></a>語法

```cpp
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md)。

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="see-also"></a>另請參閱

[Platform::COMException 類別](../cppcx/platform-comexception-class.md)
