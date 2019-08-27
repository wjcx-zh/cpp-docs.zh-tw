---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 9c9faa4cffcdc8e6840dfbbe141cb63f51155ded
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492065"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)是每個其他 COM 介面的基底介面。  這個介面會定義三個方法:[QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))、 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)。 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))可讓介面使用者要求物件提供其介面的另一個指標。 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)會在介面上執行參考計數。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[IUnknown 和介面繼承](/windows/win32/com/iunknown-and-interface-inheritance)
