---
title: 介面 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 5416fb8a99420f0f6c84318753ee3399ccf5db2a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287371"
---
# <a name="interfaces-atl"></a>介面 (ATL)

介面是物件會公開其功能與外界聯繫的方式。 在 COM 中，介面是由物件所實作的函式的指標 （例如 c + + vtable) 的資料表。 資料表代表介面，以及它所指向的函式是該介面的方法。 物件可以公開它所選擇的介面。

每個介面為基礎的基本的 COM 介面， [IUnknown](../atl/iunknown.md)。 方法的`IUnknown`允許巡覽至其他物件所公開的介面。

此外，每個介面都有唯一的介面識別碼 (IID)。 這個唯一性容易介面版本控制支援。 介面的新版本是只是新介面，使用新的 IID。

> [!NOTE]
>  預先定義的標準的 COM 和 OLE 介面的 Iid。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[COM 物件與介面](/windows/desktop/com/com-objects-and-interfaces)
