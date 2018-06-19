---
title: 雙重介面和事件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99dc173f3dde8ea81f6dc11d02298cd94673f999
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354063"
---
# <a name="dual-interfaces-and-events"></a>雙重介面和事件
雖然也可以設計成雙重事件介面，但是有許多良好的設計的理由不這樣做。 基本的原因是事件來源只會引發事件，透過 vtable 或透過`Invoke`，不能同時。 如果事件來源就會引發為直接 vtable 方法呼叫，事件`IDispatch`絕不會使用方法，並明確的介面應該已經純 vtable 介面。 如果事件來源就會引發事件與呼叫`Invoke`、 絕不會使用 vtable 方法，而且很清楚介面已被分配介面。 如果您定義事件介面為雙重介面時，您將會要求用戶端實作絕不會使用介面的一部分。  
  
> [!NOTE]
>  這個引數不適用於雙重介面，在一般情況下。 從實作觀點來看，雙重介面是快速、 方便的且格式支援的方式實作都可以存取各種不同的用戶端的介面。  
  
 還有其他原因，若要避免雙重的事件介面。Visual Basic 和 Internet Explorer 都不支援這些選項。  
  
## <a name="see-also"></a>另請參閱  
 [雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)

