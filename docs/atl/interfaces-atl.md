---
title: 介面 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 2373351330982623ffa602fd81bec61d0bc257b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492130"
---
# <a name="interfaces-atl"></a>介面 (ATL)

介面是物件將其功能公開給外部世界的方式。 在 COM 中, 「介面」 (interface) 是指物件C++所實函式的指標 (例如 vtable) 資料表。 資料表代表介面, 而它指向的函式是該介面的方法。 物件可以公開所選擇的介面數目。

每個介面都是以基本 COM 介面[IUnknown](../atl/iunknown.md)為基礎。 的方法`IUnknown`允許導覽至物件所公開的其他介面。

此外, 每個介面都具有唯一的介面識別碼 (IID)。 這種唯一性可讓您輕鬆地支援介面版本設定。 介面的新版本只是新的介面, 具有新的 IID。

> [!NOTE]
>  標準 COM 和 OLE 介面的 Iid 是預先定義的。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[COM 物件和介面](/windows/win32/com/com-objects-and-interfaces)
