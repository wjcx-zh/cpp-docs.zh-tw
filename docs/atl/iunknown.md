---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 17561092c6cccbad264bb82d68dbef9c0e078f76
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809830"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)是所有其他 COM 介面的基底介面。  這個介面會定義三種方法：[QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))， [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)，以及[發行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)。 [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))可讓介面使用者向物件的另一個介面的指標。 [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)並[發行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)實作參考計數介面。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[IUnknown 和介面繼承](/windows/desktop/com/iunknown-and-interface-inheritance)
