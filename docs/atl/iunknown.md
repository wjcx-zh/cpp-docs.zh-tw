---
title: IUnknown |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5903cebe5de87ab528dbcfe1769047b7b7ace3ef
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761910"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)是所有其他 COM 介面的基底介面。  這個介面會定義三種方法： [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))， [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)，並[版本](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)。 [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))可讓介面使用者向物件的另一個介面的指標。 [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)並[發行](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)實作參考計數介面。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)   
[IUnknown 和介面繼承](/windows/desktop/com/iunknown-and-interface-inheritance)

