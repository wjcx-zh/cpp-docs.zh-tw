---
title: Platform::IDisposable 介面
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: 0024edbad0bb3311a0497be67fc8bcfc954602e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214236"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable 介面

用來釋放 Unmanaged 資源。

## <a name="syntax"></a>語法

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>屬性

**GuidAttribute**（"de0cbaea-8065-4a45-b196-c9d443f9bab3"）

**VersionAttribute**（NTDDI_WIN8）

### <a name="members"></a>成員

IDisposable 介面繼承自 IUnknown 介面。 IDisposable 也有下列類型的成員：

**方法**

IDisposable 介面具有下列方法。

|方法|描述|
|------------|-----------------|
|處置|用來釋放 Unmanaged 資源。|

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform
