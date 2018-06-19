---
title: 彙總 |Microsoft 文件
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
ms.openlocfilehash: 760a595274ba7a1901138cc0cceceddf97122725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32353959"
---
# <a name="aggregation"></a>彙總
但有些的時候，當物件的實作項想要利用預先建置的另一個物件所提供的服務。 此外，還可能想要顯示的第一個自然一部分此第二個物件。 COM 完成這兩個目標透過內含項目和彙總。  
  
 彙總表示包含 （外部） 物件會建立包含 （內部） 的物件做為其建立程序的一部分，而且內部物件的介面會公開外部。 物件可讓本身或不是可彙總。 如果是，它必須遵循特定規則才能正常運作的彙總。  
  
 所有主要**IUnknown**所包含的物件呼叫方法必須委派給與包含物件。  
  
## <a name="see-also"></a>另請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [重複使用的物件](http://msdn.microsoft.com/library/windows/desktop/ms678443)

