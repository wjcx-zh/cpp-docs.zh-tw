---
title: 介面 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 56d5a010bc28257dce181ee33e0ddf74655ccd3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319392"
---
# <a name="interfaces-atl"></a>介面 (ATL)

介面是物件向外部世界公開其功能的方式。 在 COM 中,介面是指向物件實現的函數的指標表(如 C++可 vtable)。 表表示介面,它指向的函數是該介面的方法。 物件可以公開任意選擇的介面數。

每個介面都基於基本的COM介面[,I未知。](../atl/iunknown.md) `IUnknown`允許導航到物件公開的其他介面的方法。

此外,每個介面都被授予一個唯一的介面 ID (IID)。 這種唯一性使得支援介面版本控制變得容易。 介面的新版本只是一個新的介面,帶有新的 IID。

> [!NOTE]
> 預先定義標準 COM 和 OLE 介面的 IID。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[COM 物件與介面](/windows/win32/com/com-objects-and-interfaces)
