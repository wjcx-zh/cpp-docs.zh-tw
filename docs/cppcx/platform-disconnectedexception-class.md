---
title: Platform::DisconnectedException 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
ms.openlocfilehash: 2d4f8f4cb52fdb7e50c36eb3f0255bd85c15dbb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477138"
---
# <a name="platformdisconnectedexception-class"></a>Platform::DisconnectedException 類別

當 COM Proxy 物件嘗試參考已不存在的 COM 伺服器時會擲回

## <a name="syntax"></a>語法

```
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>備註

當類別 A 參考另一個處理序中的其他類別 (類別 B) 時，類別 A 需要 Proxy 物件，才能與保留類別 B 之跨處理序的 COM 伺服器通訊。有時候伺服器記憶體用盡，但類別 A 卻不知道。 在這種情況下，會擲回 RPC_E_DISCONNECTED 例外狀況，並轉譯成 Platform::DisconnectedException。 發生這種情形的情境之一，就是事件來源叫用的委派已傳遞給它，但在它訂閱事件之後的某個時間點，該委派卻終結。 發生此情況時，事件來源會將委派從其引動過程清單中移除。

如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md) 類別。

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="see-also"></a>另請參閱

[Platform::COMException 類別](../cppcx/platform-comexception-class.md)