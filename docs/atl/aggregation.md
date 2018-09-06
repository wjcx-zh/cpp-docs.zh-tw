---
title: 彙總 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e29fd2c7af893fe6bb548db0a3ec3f956576a37
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767307"
---
# <a name="aggregation"></a>彙總

有些的時候，當物件的實作項想要充分利用預先建置的另一個物件所提供的服務。 此外，它想要這個第二個物件顯示的第一個自然的一部分。 COM 可完成這兩個透過內含項目和彙總目標。

彙總表示包含 （外部） 的物件會包含 （內部） 的物件建立做為其建立程序的一部分，而且由外部公開內部物件的介面。 物件可讓本身可以彙總。 如果是，它必須遵循特定規則才能正常運作的彙總。

所有主要`IUnknown`所包含的物件上的方法呼叫必須委派給包含的物件。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)   
[重複使用的物件](/windows/desktop/com/reusing-objects)

