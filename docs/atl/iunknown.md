---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 6adfbdc59b2a63aa2f2bb39e27139ca977ba9465
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298749"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)是每個其他 COM 介面的基底介面。  這個介面會定義三種方法： [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))、 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)。 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))可讓介面使用者要求物件提供其介面的另一個指標。 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和[Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)會在介面上執行參考計數。

## <a name="see-also"></a>請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[IUnknown 和介面繼承](/windows/win32/com/iunknown-and-interface-inheritance)
